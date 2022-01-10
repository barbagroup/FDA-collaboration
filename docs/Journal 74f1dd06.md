<br>

# Friday 3, 2021

- Was made few simulations with geometry of pipe for hexahedral regular and tetrahedral mesh.

![Screenshot from 2021-09-02 11-15-33.png](<files/ca179349-4e7f-406f-b2a4-3ab06dc6185e/Screenshot from 2021-09-02 11-15-33.png>)

![Screenshot from 2021-09-02 10-34-32.png](<files/4020d4c9-c952-4e83-b3ad-e9fb12cb4f1d/Screenshot from 2021-09-02 10-34-32.png>)

- Now going to add coils to  hexahedral regular geometry and then to compare results with more sophisticated geometry.

and do *mesh sensitivity analysis*

# September 10, 2021 Friday

Didn't add coils because it takes time to develop new geometry with coils with openFoam tools.

Deciding how to conduct *mesh sensitivity analysis*

## Discussion:

Presentation for Friday, inside just some mesh example

[MeshAnalisysForSIR.key](files/446f2985-994b-484a-be48-06b6adbc22f6/MeshAnalisysForSIR.key)

- Decision making process should be well documented. In that way that reader could understand why this decision was made.

<br>

# September 17, Friday 2021

During development of computational process in OpenFOAM.

Prof Barba said that we need to question every decision what was made during initial project with Ansys

**Important note:** How to do good and efficient documentation

# September 27, Monday 2021

Going to make more complicated geometry, with 3 cylinders. Before was only 2 cylinders.

cylinder parameters:

- **inlet tube:** Length: 34.485\[mm] diameter 4.54\[mm]
- **mouthpiece:** Length: 13.00\[mm] diameter: 7.96\[mm]
- **open air:** Length: 56.05 \[mm] diameter: 16.0 \[mm]

# October 21, Thursday 2021

- questions: should I use model with temperature if it said that for the basic case was used just a model for incompressible fluid?
- planning just got profile 1 mm above

to be consistent choosing the color palette as standard to ansys, to better visual understanding

![Screenshot from 2021-10-21 17-41-32.png](<files/bf01fd54-1aec-410b-9095-2bb727081901/Screenshot from 2021-10-21 17-41-32.png>)

generated 3 meshes with different number of cells

- 15900
- 34000
- 63000

correspondingly, for easier Richardson extrapolation in the future.

Made air simulation in model with velocity 0.5 liters per second

![Screenshot from 2021-10-21 17-45-21.png](<files/50b783ab-557b-47b3-86e0-6d9176b60952/Screenshot from 2021-10-21 17-45-21.png>)

for visual representation how mesh for 15900 elements looks like

![Screenshot from 2021-10-21 17-46-03.png](<files/35ca982f-eeff-49dc-a227-7c8f4f346d99/Screenshot from 2021-10-21 17-46-03.png>)

to get steady state we need to run simulation for 1 second, this is enough for velocity y 0.5 liters per second → enough for other cases, because for other simulation velocity even higher.

The picture below not for velocity comparison, but for geometry comparison. The one which is on top some geometry from ansys and below is current OF case mesh.

![Screenshot from 2021-10-21 18-19-45.png](<files/bf1f504c-51ac-471c-8e96-de829313e2e3/Screenshot from 2021-10-21 18-19-45.png>)

## Velocity profile 1 mm above mouthpiece

below results from physical and computational experiment

![Screenshot 2021-09-27 at 15.14.13.png](<files/4f561576-8f1c-4844-a5c1-cdf58674a398/Screenshot 2021-09-27 at 15.14.13.png>)

Easiest way to get velocity profile it is use paraView filter plotOverLine

for the line coordinates: (0, -0.008,0.049)(0, 0.008,0.049)

![Screenshot from 2021-10-21 18-49-53.png](<files/77d4a144-0782-4d4d-84d7-50a791ba32e0/Screenshot from 2021-10-21 18-49-53.png>)

[velocity\_profile.csv](files/3ea25429-7816-41d4-b6d0-d725b25e96f2/velocity_profile.csv)

then you can use data in python

# October 25

find some differences between tetrahedral geometry and regular one for the velocity 0.5 LPM. for the fist case velocity changing only to the range ~0.5

![Screenshot from 2021-10-25 14-37-38.png](<files/563524d3-9405-4f95-84be-7eec66bddd15/Screenshot from 2021-10-25 14-37-38.png>)
![Screenshot from 2021-10-25 14-38-01.png](<files/ebb1f277-9196-470e-8384-bc3e7e3db591/Screenshot from 2021-10-25 14-38-01.png>)

<br>

# 3 November

checked out python notebooks from Paulina

- coils-no-coils low
- Validation - Airflow\_Only  (didn't understand what is the airflow rate for the analysis)
- Analisys OA Complete not running because name convention

Saw results form notebook Analysis&#x20;

```
Max Velocity: 
 Experiments:  1.024403179 
 Simulation @1mm:  0.9981606007
Volumetric Flow Rates:
!!! Experiments:  0.5796991535812704 [LPM] 
 Simulation @1mm:  0.2881095414087508 [LPM] 
 Simulation @MP:  0.2925687241728016 [LPM] 
 Simulation @Out:  0.19914935105792236 [LPM]
```

Calculated based on Volumetric Airflow Rates of: 0.5 LPM, 0.95 LPM, 2 LPM\
Low Inlet Airflow: Mass flow rate = 9.865833 e-6 \[kg/s]\
Medium Inlet Airflow: Mass flow rate =1.874508 e-5 \[kg/s]\
High Inlet Airflow: Mass flow rate = 3.946333e-5 \[kg/s]

<br>

# November 15, 2021

- run cases in longer pipe

run cases for 25,50,100 thousand cells, and compared 50 and 100

currently case for 50000 cells shows better results

<br>

# TODO

- write down how calculated metric for fully developed flow
- &#x20;understand where errors are come from. is it round error or not?
- create a draft for checklist for pipe flow&#x20;
