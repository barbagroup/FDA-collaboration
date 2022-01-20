Tools for FDA 25e445f2.mdcheck list for grid convergence analysis

- [ ] Provided at least 3 meshes (Coarse, medium, fine) with a constant refinement ratio **r**
- [ ] Perform a Richardson extrapolation to predict the value at **h=0**
- [ ] Calculate Courant Number for given research, with idea in mind that a liquid particle should not advance more than one spatial step in one time step **|u|\*delta t / delta x < C**
