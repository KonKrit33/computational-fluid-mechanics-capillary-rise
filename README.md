# Computational Fluid Mechanics: Nonlinear Capillary-Rise Modelling with Finite Differences and Newton-Raphson

This repository presents a computational fluid mechanics project focused on the numerical solution of nonlinear capillary-rise boundary-value problems.

The project studies the shape of a liquid-air interface near vertical solid surfaces, where surface tension, gravity and contact angle effects determine the equilibrium interface profile. The governing equation is nonlinear because the curvature of the free surface depends on the local slope of the interface.

The numerical solution is implemented in MATLAB using finite-difference discretization and Newton-Raphson iteration.

## Project Overview

Capillary rise is a classical fluid mechanics phenomenon that occurs when a liquid interface is deformed near a solid surface due to surface tension and wetting effects.

In this project, the liquid-air interface is modelled as a nonlinear boundary-value problem. The governing equation is nondimensionalized using the capillary length, and the resulting nonlinear differential equation is solved numerically.

The project investigates:

- capillary rise near a single vertical surface,
- capillary rise or depression between two vertical surfaces,
- the effect of hydrophilic and hydrophobic contact angles,
- the effect of the distance between two vertical plates,
- grid sensitivity with respect to the number of discretization nodes,
- convergence of the Newton-Raphson method,
- comparison between the full nonlinear numerical solution and a small-slope analytical approximation.

## Physical Problem

The physical system consists of a liquid-air interface near one or two vertical solid surfaces.

The liquid forms a contact angle with the solid wall. Depending on the value of the contact angle, the surface may behave as hydrophilic or hydrophobic:

- for contact angles below 90°, capillary rise is observed,
- for contact angles above 90°, capillary depression is observed.

The interface profile is governed by the balance between hydrostatic pressure and surface-tension-induced curvature.

After nondimensionalization with the capillary length, the problem becomes a nonlinear boundary-value problem for the dimensionless interface height.

## Numerical Method

The nonlinear boundary-value problem is solved using:

- finite-difference discretization,
- central-difference approximations for spatial derivatives,
- Newton-Raphson iteration,
- analytical construction of the Jacobian matrix,
- convergence monitoring through the norm of the Newton update.

The spatial domain is discretized into a finite number of nodes, and the nonlinear differential equation is converted into a system of nonlinear algebraic equations.

At each Newton-Raphson iteration, the linearized system is solved to update the interface-height vector.

## Case A: Single Vertical Surface

The first case studies the capillary interface near a single vertical surface.

The boundary conditions are:

- prescribed slope at the wall based on the contact angle,
- zero interface height far from the wall.

The numerical solution is computed for:

```text
θ = 60°   hydrophilic surface
θ = 110°  hydrophobic surface
```

A grid-sensitivity analysis is performed using different numbers of discretization nodes:

```text
11, 31, 101, 301, 1001 nodes
```

The results show that increasing the number of nodes improves the accuracy of the finite-difference approximation and leads to convergence of the computed interface profile.

## Case B: Two Vertical Surfaces

The second case studies the liquid-air interface between two vertical plates.

The nonlinear boundary-value problem is solved for different dimensionless distances between the two walls:

```text
L = 2, 4, 6, 8
```

The analysis is performed for both hydrophilic and hydrophobic contact angles:

```text
θ = 60°
θ = 110°
```

The results show that the magnitude of capillary rise or depression decreases as the distance between the two vertical surfaces increases.

The midpoint interface height is used as the capillary rise or depression measure.

## Case C: Small-Slope Analytical Approximation

The third case compares the full nonlinear numerical solution with an analytical approximation obtained under the small-slope assumption:

```text
(dy/dx)^2 << 1
```

Under this assumption, the nonlinear curvature equation reduces to a linear differential equation.

The analytical and numerical solutions are compared for:

```text
L = 2
θ = 85°
θ = 95°
θ = 130°
```

The comparison shows that the small-slope approximation is accurate only when the contact angle is close to 90°, where the interface deformation is weak and the slope remains small throughout the domain.

For larger deviations from 90°, such as θ = 130°, the nonlinear numerical solution differs significantly from the analytical approximation.

## Key Results

The project demonstrates the following results:

- finite differences can be used to discretize the nonlinear capillary-rise equation,
- Newton-Raphson iteration provides rapid convergence for the nonlinear algebraic system,
- the computed interface profile depends strongly on the contact angle,
- hydrophilic surfaces produce capillary rise,
- hydrophobic surfaces produce capillary depression,
- increasing the distance between two vertical surfaces reduces the magnitude of capillary rise or depression,
- the small-slope analytical approximation is valid mainly for contact angles close to 90°,
- the nonlinear model is necessary when interface slopes become significant.

## MATLAB Implementation

The numerical implementation was developed in MATLAB.

The computational workflow includes:

- definition of contact angles and grid sizes,
- construction of the finite-difference residual vector,
- analytical construction of the Jacobian matrix,
- Newton-Raphson iteration,
- convergence monitoring,
- plotting of interface profiles,
- sensitivity analysis with respect to grid refinement,
- comparison between numerical and analytical solutions.

## Repository Structure

```text
.
├── README.md
├── report/
│   └── Capillary_Rise_Nonlinear_BVP_Computational_Fluid_Mechanics_Report.pdf
└── src/
    ├── Question_A.m
    ├── Question_B.m
    ├── Question_C.m
    ├── Capillary_ND.m
    └── Capillary_NN.m
```

If the MATLAB source files are not available separately, the full implementation is included in the report appendix.

## Skills Demonstrated

This project demonstrates practical skills in:

- computational fluid mechanics,
- nonlinear boundary-value problems,
- scientific computing,
- numerical methods,
- finite-difference discretization,
- Newton-Raphson methods,
- analytical Jacobian formulation,
- MATLAB programming,
- convergence analysis,
- grid-sensitivity analysis,
- physical interpretation of numerical results.

## Relevance

This project is relevant to computational engineering, numerical modelling and scientific computing.

It shows how a physical fluid mechanics problem can be transformed into a mathematical model, nondimensionalized, discretized and solved numerically.

The methodology is relevant to broader engineering problems involving:

- nonlinear differential equations,
- free-surface flows,
- capillarity,
- interface phenomena,
- numerical simulation,
- model validation,
- computational process modelling.

## Limitations

This project is a deterministic numerical study based on a simplified capillary-rise model.

The main limitations are:

- the model assumes static equilibrium,
- dynamic effects are not included,
- contact angle hysteresis is not considered,
- fluid properties are treated as constant,
- the analysis is two-dimensional,
- the analytical approximation is valid only for small interface slopes.

## Future Work

Potential extensions of this project include:

- dynamic simulation of capillary rise,
- inclusion of contact angle hysteresis,
- comparison with experimental data,
- implementation in Python,
- adaptive mesh refinement,
- continuation methods for difficult nonlinear regimes,
- parameter estimation from observed interface profiles,
- extension to more complex geometries,
- coupling with CFD simulations.

## Attribution

Prepared for public portfolio use by:

Konstantinos Kritsotakis

This repository highlights computational fluid mechanics, numerical methods, nonlinear modelling and MATLAB-based scientific computing.
