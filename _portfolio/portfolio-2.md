---
title: "Nonlinear Control of an Inverted Pendulum on a Cart"
excerpt: "January 2025 - May 2025<br/><img src='/images/Pendulum.png' alt='inverted_pendulum' style='max-width:100%; height:auto; width:450px;'>"
collection: portfolio
---

## Overview

This project implements and analyzes control strategies for stabilizing an inverted pendulum on a cart, which is a classic problem in nonlinear control theory. We use both linear and nonlinear models to design controllers and observers, evaluate their performance, and compare system behavior across a range of initial conditions.

## System Modeling

The nonlinear dynamics of the inverted pendulum system are governed by two second-order differential equations. To simplify analysis, the equations are made dimensionless:

\[
\ddot{\phi} = \frac{-c\dot{\phi}^2 \sin(\phi)\cos(\phi) + \sin(\phi) - \cos(\phi)\mu}{1 + c\sin^2(\phi)}, \quad
\ddot{\bar{s}} = \frac{d\dot{\phi}^2 \sin(\phi) - \cos(\phi)\sin(\phi) + b\bar{\mu}}{1 + c\sin^2(\phi)}
\]

Where \( \bar{s} \) and \( \bar{\mu} \) are normalized position and input force. Derivations confirm these expressions from the original equations of motion.

## Linearization & State-Space Form

Linearization around the upright equilibrium yields the state-space model:

\[
\dot{x} = Ax + B\bar{\mu}, \quad x = [\phi, \dot{\phi}, \bar{s}, \dot{\bar{s}}]^T
\]

The Jacobians \( A \) and \( B \) are computed at the equilibrium point \([0, 0, 0, 0]\) using MATLAB.

## State Feedback Control

Controllability was verified via full-rank controllability matrix. A pole placement controller was designed using:

\[
K = [-19.3, -22.975, -1.59, -5.525], \quad \bar{\mu} = -Kx
\]

Applying this controller, the linearized and nonlinear systems were simulated for various initial angles. The system remained stable up to \( \phi(0) = 0.65 \) radians before diverging in the nonlinear case.

### Simulation Snapshots

| Initial Condition | Linear System | Nonlinear System |
|------------------|---------------|------------------|
| \( [0.1, 0, 0, 0] \) | Stable | Stable |
| \( [0.5, 0, 0, 0] \) | Stable | Mild oscillation |
| \( [0.65, 0, 0, 0] \) | Stable | Unstable |

## Luenberger Observer Design

With outputs limited to \( y = [\phi, \bar{s}]^T \), an observer was constructed:

\[
\dot{\hat{x}} = A\hat{x} + Bu + L(y - \hat{y}), \quad \hat{y} = C\hat{x}, \quad u = -K\hat{x}
\]

Poles for \( L \) were placed 5× faster than the controller to ensure fast convergence. The observer is effective for small deviations from equilibrium but degrades for larger angles due to linear approximation.

## Nonlinear Observer

To improve accuracy for large deviations, a nonlinear observer was implemented:

\[
\dot{\hat{x}} = f(\hat{x}, u) + L(y - \hat{y}), \quad \hat{y} = C\hat{x}, \quad u = -K\hat{x}
\]

Simulations show improved tracking and reduced estimation error compared to the linear observer, even at \( \phi(0) = 0.62 \) radians:contentReference[oaicite:3]{index=3}.

## Conclusion

- **Linear controllers** perform well near the equilibrium.
- **Full-state feedback** stabilizes the system up to \( \phi(0) = 0.65 \) radians.
- **Linear observers** struggle beyond small angles.
- **Nonlinear observers** significantly improve performance for larger deviations.

This project demonstrates the effectiveness of combining classical control theory with practical implementation for nonlinear systems.

## Tools Used

- MATLAB (simulation, linearization, observer design)
- State-space control theory
- Nonlinear system modeling

## Reference

Khalil, H. K. *Nonlinear Systems*, 3rd ed., Prentice Hall, 2002.

---
