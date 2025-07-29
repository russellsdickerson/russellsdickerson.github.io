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

Next, controllability is verified via rank analysis of the controllability matrix. The desired poles for the system will be set to \\( \ -3, -2, -0.7+0.2i \\), and \\( \ -0.7-0.2i \\) respectively. Because these poles were placed so that their real components are negative, this implies that the eigenvalues of the matrix \\( A \\) are strictly negative, which further implies that the matrix \\( A \\) is Hurwitz. Therefore, it can be concluded by Lyapunov’s Indirect Method, that the origin is indeed an asymptotically stable equilibrium point. Therefore, by using pole placement, a feedback gain \\( K \\) is now computed.

$$
K = \begin{bmatrix} -19.3 & -22.975 & -1.59 & -5.525 \end{bmatrix}
$$

Therefore, the control law now becomes:

$$
\bar{\mu} = -Kx
$$

Simulations demonstrate that by applying the control law for both the linearized and nonlinear models at initial angles of \\( \phi = 0.1 \\) rad up to \\( \phi = 0.65 \\) rad with the other states at zero. At \\( \phi = 0.1 \\) rad, the linear model matches the nonlinear response, validating the local linearization. As the angle approaches \\( \phi = 0.65 \\) rad, the nonlinear system begins to experience more oscillation before becoming unstable. However the linear model still predicts bounded motion, exposing the approximation’s failure far from the equilibrium. Thus, as expected, the linear model remains reliable only for small perturbations around the origin.

## Observer Design

First, assume only partial state availability \\( y = [\phi, \bar{s}]^T \\). Under these conditions, define \\( y = Cx \\) where \\( C \\) is as follows:

$$
C = \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0
\end{pmatrix}
$$

Next, observability is verified via rank analysis of the observability matrix. A linear observer can then be constructed as seen below:

$$
\dot{\hat{x}} = A\hat{x} + B\bar{\mu} + L(y - \hat{y}), \quad \hat{y} = C\hat{x}, \quad \bar{\mu} = -K\hat{x}
$$

Using pole placement, observer poles are placed 5x faster than the previous system poles to ensure rapid convergence. This results in:

$$
L = \begin{pmatrix}
13.3460 & 3.5943 \\
32.7189 & 49.3415 \\
-0.9738 & 18.6540 \\
-6.5188 & 54.0748
\end{pmatrix}
$$

Simulations employing the linear observer-based control law evaluated both the linearized and full nonlinear pendulum-cart models for initial states ranging from \\( \phi = 0.1 \\) rad to \\( \phi = 0.65 \\) rad with the other states at zero. Notably, \\( \phi = 0.62 \\) is the largest angular displacement before the nonlinear system loses stability under observer control. As the observer reconstructs the linearized dynamics, it does so with negligible error across the entire range of conditions, confirming high estimator veracity near the linearization point. In contrast, the observer's attempt to track the nonlinear dynamics reveals that it performs well for small deviations, but its performance begins to deteriorate as the initial angle departs from equilibrium. This once again reflects the inherent locality of the linear approximation.

## Nonlinear Observer Compensator

To overcome the limitations of the linear observer, a nonlinear observer is employed:

$$
\dot{\hat{x}} = f(\hat{x}, \bar{\mu}) + L(y - \hat{y}), \quad \hat{y} = C\hat{x}, \quad \bar{\mu} = -K\hat{x}
$$


This structure mirrors the nonlinear plant dynamics with an added correction term. Applying this nonlinear observer-based control law, simulations were run for the nonlinear pendulum-cart model for the same range of initial conditions: \\( \phi = 0.1 \\) rad to \\( \phi = 0.65 \\) rad while the other states are at zero. These results demonstrate markedly reduced state-estimation error and overall superior tracking performance relative to the earlier linear observer. Thus, the observer’s effectiveness across the entire operating range is confirmed.

## Conclusion

This project illustrates the efficacy and limitations of linear and nonlinear control strategies for an inherently unstable system. Key takeaways include:

- The linear observer fails to capture nonlinear dynamics far from the origin.
- The nonlinear observer significantly improves robustness in estimating the system state under larger deviations.

## Tools and References

- **Software:** MATLAB (symbolic analysis, simulation)
- **Textbook:** H. K. Khalil, *Nonlinear Systems*, 3rd ed., Prentice Hall, 2002.
