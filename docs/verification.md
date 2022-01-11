For verification we will use pipe flow solutions. It has analytical solution [Hagen–Poiseuille equation - Wikipedia](https://en.wikipedia.org/wiki/Hagen%E2%80%93Poiseuille_equation#Startup_of_Poiseuille_flow_in_a_pipe "Hagen–Poiseuille equation - Wikipedia")

For this reason we run pipe flow computational case with initial settings:

Mesh has 52800 cell mesh

- Length  of pipe: 0.034485 meters
- r = 0.00227 meters

Initial conditions:

- velocity v = 0.0521646 m/s ~ 0.5 LPM
- kinematic viscosity nu = 1.48e-05 m^2/s
- density rho = 1  kg/m^3
- pressure at the inlet is zero gradient and 0 at the outlet
- data at the outlet[velocity\_outlet.csv](files/e47a8b8f-00b0-46c1-b20f-050baa349b26/velocity_outlet.csv)

  plot of velocity

**The velocity profile:** where velocity changes from 0.05 to 1.0391 m/s

![Screenshot from 2021-11-04 11-08-41.png](<files/d9f7fece-b09b-4f44-acf5-7e17ea868bda/Screenshot from 2021-11-04 11-08-41.png>)

**max velocity at the outlet** v\_max = 1.0391 m/s

velocity should be equal to v\_max/2 → computational velocity= 1.0391/2 = 0.5196

while initial velocity is **0.521646** it is 0.4% difference

Re = 159 → flow is laminar

Another way to calculate analytical velocity presented in the pdf:

[Pipe\_flow\_solution\_of\_NS\_equation.pdf](files/28865103-5de7-4fff-8dc3-5e67a340866d/Pipe_flow_solution_of_NS_equation.pdf)

Final comparison saved in the jupyter notebook:

[velocity\_manipulation.ipynb](files/ff591943-6f65-4c7d-ad5f-9c2ca7585d77/velocity_manipulation.ipynb)

[velocity\_outlet.csv](files/60e3c8a2-749e-4099-9bbd-6934189b3ec5/velocity_outlet.csv)

[pressure\_at0.csv](files/4fed7bb2-7157-45cb-8aed-cdc04ecddc33/pressure_at0.csv)

Is it fully developed flow? Check two stations at the end

[Entrance length (fluid dynamics) - Wikipedia](https://en.wikipedia.org/wiki/Entrance_length_\(fluid_dynamics\)#Calculating_hydrodynamic_entrance_length "Entrance length (fluid dynamics) - Wikipedia")

the length should be 0.041641

<br>

Do  mesh convergence analysis

<br>

We trying to understand where errors are come from

# Verification Code&#x20;

### Software Quality Assurance (SQA)

The objective of SQA is to ensure that the software is functioning correctly and produces repeatable results on a specified computer resource in a specified software environment.  Types of computational model software include, but are not limited to, off-the-shelf (OTS), modified off-the-shelf (MOTS), and user-developed.  SQA is achieved through software validation on OTS and MOTS software and software quality development assurance on MOTS and user-developed software \[3, 6-9]. For the selected software, it is important to understand unresolved anomalies and their potential effect(s) on the COU, as well as any workarounds, before starting software validation.  For user-developed code, it is also important to understand the anomaly list for the software development environment, such as compilers and libraries applicable to the computational model.

- **GRADATION: SQA procedures were specified and documented;**
  - Explanation for picking this gradation&#x20;
- LBG Activities Performed:  \*\*\*Configured Github, Reproducibility setup and infrastructure, OpenFOAM documentation, version, docker container\*\*\*

### Numerical Code Verification (NCV)

The objective of NCV is to demonstrate correct implementation and functioning of the numerical algorithms.  NCV relies on careful investigation of numerical aspects, such as spatial and temporal convergence rates, spatial convergence in the presence of discontinuities, independence to coordinate transformations, and symmetry tests related to various types of system conditions.  NCV is typically conducted by comparing numerical solutions to exact benchmark solutions, e.g. using the method of manufactured solutions, that are analytical or semi-analytical in nature.

- **NCV was not performed; **
- Explanation:&#x20;

<br>

<br>
