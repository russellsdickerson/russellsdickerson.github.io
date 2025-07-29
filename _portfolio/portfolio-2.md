---
title: "Nonlinear Control of an Inverted Pendulum on a Cart"
excerpt: "January 2025 - May 2025<br/><img src='/images/inverted_pendulum_nlonls_oc_0.62.gif' alt='inverted_pendulum' style='max-width:100%; height:auto; width:450px;'>"
collection: portfolio
---

## Overview

This project investigates the stabilization of an inverted pendulum on a cart using both linear and nonlinear control techniques. Specifically, it is comprised of modeling, linearization, full-state feedback design, observer-based compensator implementation, and system simulation.

## System Modeling

The nonlinear dynamics of the inverted pendulum system are governed by:

$$
\frac{d^2\phi}{dt^2} = \frac{-(m+M)mgL\sin(\phi) + (mL\dot{\phi})^2\sin(\phi)\cos(\phi) + (mL\cos(\phi))\mu}{(m+M)(J+mL^2) - (mL)^2\cos^2(\phi)}
$$

$$
\frac{d^2s}{dt^2} = \frac{(J+mL^2)mL\dot{\phi}^2\sin(\phi) - (mL)^2g\sin(\phi)\cos(\phi) + (J+mL^2)\mu}{(m+M)(J+mL^2) - (mL)^2\cos^2(\phi)}
$$

Dimensionless variables are then introduced to improve numerical stability and generality:

$$
\bar{s} = \left( \frac{M}{m+1} \right) \frac{s}{L}, \quad \bar{\mu} = \frac{\mu}{(m+M)g}, \quad \bar{t} = \frac{t}{T}
$$

$$
T^2 = \left( \frac{L}{g} \right)\left( \frac{J}{mL^2} + \frac{M}{m+M} \right)
$$

Thus, rewriting the equations in terms of these variables yields the following model:

$$
\frac{d^2\phi}{d\bar{t}^2} = \frac{-c\dot{\phi}^2 \sin(\phi)\cos(\phi) + \sin(\phi) - \cos(\phi)\bar{\mu}}{1 + c\sin^2(\phi)}
$$

$$
\frac{d^2\bar{s}}{d\bar{t}^2} = \frac{d\dot{\phi}^2 \sin(\phi) - \cos(\phi)\sin(\phi) + b\bar{\mu}}{1 + c\sin^2(\phi)}
$$

## Linearization and State-Space Representation

The system is linearized around the upright equilibrium \\( \phi = 0 \\) using the state vector:

$$
x = \begin{bmatrix} \phi & \dot{\phi} & \bar{s} & \dot{\bar{s}} \end{bmatrix}^T
$$

This yields the linear state-space form:

$$
\dot{x} = A x + B \bar{\mu}
$$

Jacobian matrices \\( A \\) and \\( B \\) are obtained analytically and confirmed via MATLAB symbolic computation.

$$
A = \begin{pmatrix}
0 & 1 & 0 & 0 \\
1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 \\
-1 & 0 & 0 & 0
\end{pmatrix}, \quad
B = \begin{pmatrix}
0 \\
-1 \\
0 \\
3
\end{pmatrix}
$$


## Full-State Feedback Design

Next, controllability is verified via rank analysis of the controllability matrix. The desired poles for the system will be set to \\( [-3, -2, -0.7+0.2i, -0.7-0.2i] \\). Because these poles were placed so that their real components are negative, this implies that the eigenvalues of the matrix \\( A \\) are strictly negative, which further implies that the matrix \\( A \\) is 
Hurwitz. Therefore, it can be concluded by Lyapunov’s Indirect Method, that the origin is ideed an asymptotically stable equilibrium point. Therefore, by using pole placement, a feedback gain \\( K \\) is now computed.

$$
K = \begin{bmatrix} -19.3 & -22.975 & -1.59 & -5.525 \end{bmatrix}
$$

Therefore, the control law now becomes:

$$
\bar{\mu} = -Kx
$$

Simulations demonstrate that by applying the control law for both the linearized and nonlinear models at initial angles of 0.10 rad up to 0.65 rad with the other states at zero. At 0.10 rad, the linear model matches the nonlinear response, validating the local linearization. As the angle approaches 0.65 rad, the nonlinear system begins to experience more oscillation before becoming unstable. However the linear model still predicts bounded motion, exposing the approximation’s failure far from the equilibrium. Thus, as expected, the linear model remains reliable only for small perturbations around the origin.

## Observer Design

Assuming only partial state availability \\( y = [\phi, \bar{s}]^T \\), a Luenberger observer is designed:

First 

$$
\dot{\hat{x}} = A\hat{x} + B\bar{\mu} + L(y - \hat{y}), \quad \hat{y} = C\hat{x}, \quad \bar{\mu} = -K\hat{x}
$$

Observer poles are placed significantly faster than the system poles to ensure rapid convergence. This linear observer performs well for small deviations but deteriorates with increased nonlinearity.

## Nonlinear Observer Compensator

To overcome the limitations of the linear observer, a nonlinear observer is employed:

$$
\dot{\hat{x}} = f(\hat{x}, \bar{\mu}) + L(y - \hat{y}), \quad \hat{y} = C\hat{x}, \quad \bar{\mu} = -K\hat{x}
$$

This structure mirrors the nonlinear plant dynamics with an added correction term. Linearization around the equilibrium confirms that the origin remains asymptotically stable under this observer.

Simulations confirm improved performance and reduced estimation error across the tested initial conditions:

| Initial Condition        | Linear Observer Error | Nonlinear Observer Error |
|--------------------------|-----------------------|---------------------------|
| \\( \phi = 0.1 \\)          | Low                   | Very low                  |
| \\( \phi = 0.5 \\)          | Moderate              | Low                       |
| \\( \phi = 0.62 \\)         | High                  | Moderate                  |

## Conclusion

This project illustrates the efficacy and limitations of linear and nonlinear control strategies for an inherently unstable system. Key takeaways include:

- The linear controller stabilizes the system up to \\( \phi = 0.65 \\) radians.
- The linear observer fails to capture nonlinear dynamics far from the origin.
- The nonlinear observer significantly improves robustness in estimating the system state under larger deviations.

## Tools and References

- **Software:** MATLAB (symbolic analysis, simulation)
- **Textbook:** H. K. Khalil, *Nonlinear Systems*, 3rd ed., Prentice Hall, 2002.
