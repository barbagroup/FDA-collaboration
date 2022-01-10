From FDA project there were a few different geometries:

- a channel
- a channel with coils
- a channel with coils and mouthpiece
- a channel with coils and extended mouthpiece

There are comparison data after which in project was decided to use geometry with coils.&#x20;

[Coils\_Vs\_NoCoils\_V2.pdf](files/5b943e4b-70a3-43aa-832e-02a740b5f220/Coils_Vs_NoCoils_V2.pdf)

schematic view lines where measurements were made

![Screenshot 2021-09-27 at 15.06.14.png](<files/82583c3d-4118-4a86-9bbe-b74a2b84eefb/Screenshot 2021-09-27 at 15.06.14.png>)

From results of velocity profiles we interested in velocity at outlet, i.e line 3, green lines, and there is small visible difference→ if we will think that mesh with coils leads us to way bigger computational costs then it is reasonable to neglect coils.&#x20;

![Screenshot 2021-09-27 at 15.08.26.png](<files/6560566b-5fd0-4605-928e-93fd1ee29561/Screenshot 2021-09-27 at 15.08.26.png>)

# OpenFoam geometry parameters:

cylinder parameters:

- **inlet tube:** Length: 34.485\[mm] diameter 4.54\[mm]
- **mouthpiece:** Length: 13.00\[mm] diameter: 7.96\[mm]
- **open air:** Length: 56.05 \[mm] diameter: 16.0 \[mm]

Parameters for Geometry G1 according to geometry document. Was chosen for the better analysis with Ansys, because I have mesh which was used for simulation in Ansys.
