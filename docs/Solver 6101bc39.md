## OpenFoam case for incompressible

in OF every  equation  term could be discretized differently and its settings could be changed in the file `system/fvSchemes`

in our case we choosing&#x20;

- **time discretization** with Euler method
- **pressure gradien**t discretized with linear Gauss method
- convection term as well discretized with linear Gauss method (Second order, unbounded)
- diffusion discretized with Gauss (the only choice for interpolation) linear (how we treat viscosity term) orthogonal(how we treat gradient)

numerical schemes for each part of the solving equation.

For solving equations there is settings in the file `system/fvSolution`

- for pressure&#x20;
  - **solver PGG (Preconditioned conjugate gradient)**
  - preconditioner(Simplified **D**iagonal-based **I**ncomplete **C**holesky preconditioner)
  - tolerance 1e-06
  - relative tolerance t = 0.05
- for velocity&#x20;
  - solver smooth Solver which require to specify the smoother
  - smoother&#x20;
  - tolerance 1e-05
  - relative tolerance 0&#x20;
  settings for PISO loop:
- number corrector cycles 3
- non Orthogonal correctors number 0;

we choose icoFoam solver&#x20;

if you  want to use adjusted time step it is better to use pisoFoam solver or modify icoFoam solver

if you wanna add temperature in the future you could follow this steps:

[How to add temperature to icoFoam - OpenFOAMWiki](https://openfoamwiki.net/index.php/How_to_add_temperature_to_icoFoam "How to add temperature to icoFoam - OpenFOAMWiki")
