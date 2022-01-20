From FDA project there were a few different meshes, all of them tetrahedral meshes:

- a channel
- a channel with coils
- a channel with coils and mouthpiece
- a channel with coils and extended mouthpiece

Mesh with extended mouthpiece was used because with shorter mouthpiece had problems in simulation with Ansys

This is mesh with short mouthpiece:

![Screenshot 2021-09-27 at 15.15.14.png](<files/cc02e870-68e7-4043-ae22-c9e996200e2e/Screenshot 2021-09-27 at 15.15.14.png>)

<br>

<br>

## Conversion from Ansys to OpenFoam mesh:

Sometime ANSYS mesh file might be too large to send if via email. For this save mesh in ASCII format in Ansys (starts at 9:36 <https://www.youtube.com/watch?v=CfTE5U7AAdA> ) with extension .msh, as a Fluid file. Then open/save as .txt file and save as a few smaller .txt files, archived in 7z and sent to linux machine.

`unzip 7za e meshfile.7z`

to combine 2 files together we needed to add space at the end of first file and then combine files:

`cat mesh1.txt mesh.txt > outputfile.msh`

to convert mesh to OF format we need:

1. copy OF case folder (in our case just copied simple cavity case)
2. delete if any constant/polyMesh folder
3. copy mesh to the main case folder
4. fluentMeshToFoam outputfile.msh
5. adjust BC in /0 folder
6. open paraFoam to see the converted mesh

Tried out OpenFoam tool to check mesh quality:

`checkMesh` `> log.checkMesh &`

the result should say at the end :

`Mesh OK.`

<br>

## Cylindric mesh in OpenFOAM

This mesh could be used to build a cylinder with few parameters adjustment.

[blockMeshDict.m4](files/4ef50197-b0c1-426f-8669-613327298c21/blockMeshDict.m4)

store this file in system folder then in the folder run:

`m4 blockMeshDict.m4 > blockMeshDict`

to view the mesh with `paraFoam` you need to adjust BC, make sure that your boundaries called inlet, outlet and walls.

!! when creating mesh it is important to set inner square side half and inner square side curvature smaller than radius

inlet on the left, outlet is on the right

We going to build 3 cylinders with different diameter:

- **inlet tube:** Length: 34.485\[mm] diameter 4.54\[mm][blockMeshDict.m4](files/18ee3935-01ee-43bc-a6a3-511237f67ef5/blockMeshDict.m4)
- **mouthpiece:** Length: 13.00\[mm] diameter: 7.96\[mm][blockMeshDict.m4](files/fd7ab2e4-09b0-419a-a781-2e257caec726/blockMeshDict.m4)
- **open air:** Length: 56.05 \[mm] diameter: 16.0 \[mm][blockMeshDict.m4](files/f55f0d63-96bf-4047-b09a-0fdb9c79ad7d/blockMeshDict.m4)

Creating 3 folders for 3 different cylinder geometry correspondingly. Then

next step to merge and stitch the meshes&#x20;

`mergeMeshes Case1 Case2`

`stitchMesh outlet inlet2`

we also need to translate corresponding meshes to combine them at proper location

```
transformPoints -translate "(0 0 0.034485)"
stitchMesh inlet2 outlet
```

BC of Overlap w/ mouthpiece: 6.0514\[mm] length of mouthpiece was reduced to 50.0\[mm]

```
transformPoints -translate "(0 0 0.047485)"
mergeMeshes channel1 channel3
stitchMesh inlet3 outlet2 -overwrite
```

Final mesh and script to build the mesh is here:

[mesh3cylScript.zip](files/622e3252-1530-4843-af58-0769de9e2704/mesh3cylScript.zip)

[Allrun](files/eb384cbd-dd03-41cb-bca9-136ad15c12d2/Allrun)

the script is good to use for the mesh analysis

it could be run as `sh Allrun`&#x20;

but I will need to adjust number of mesh cells in `blockMeshDict.m4 `file

<br>

<br>

# Grid convergence analysis

main material [Examining Spatial (Grid) Convergence](https://www.grc.nasa.gov/www/wind/valid/tutorial/spatconv.html "Examining Spatial (Grid) Convergence")

<br>
