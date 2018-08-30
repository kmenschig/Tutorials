#### Parallel Visualization of Two Cases:

Create paraview case file by typing:

```
touch $FOAM_RUN/<case>/<case>.OpenFOAM
```
in terminal.


#### snappyHexMesh - Processing in Parallel:
```
No need for a 0 directory yet. Dependent on the number of actions by snappyHexMesh,
one will get upto 3 time folders, first time folder for castellation, second 
time folder for snapping and third time folder for additional layers.
```
blockMesh

```
decomposePar (-force) in scotch mode
```
Solver execution with 4 processors with progress stored in logSHM file:

```
mpirun -np 4 snappyHexMesh – parallel > logSHM &
```
Reconstruction into time files is done by

```
reconstructParMesh -time 'last time folder'
```
cp -r 'last time folder'/polyMesh constant/

```
Delete the Processor Files by

```
rm -r proce*
```

#### Processing in Parallel:

```
decomposePar (-force) in scotch mode
```
Solver execution with 4 processors with progress stored in log00 file:

```
mpirun -np 4 interFoam – parallel > log00 &
```

Reconstruction into time files is done by

```
reconstructPar
```
Delete the Processor Files by

```
rm -r proce*
```

#### Capturing Fluid Flow in 'mpg' File Format:

After the CFD results are captured in \*.jpg files like U.jpg, the pictures 
can be summarized in a mpg file like U.mpg and played with mplayer:

```
mencoder "mf://*.jpg" -mf fps=2 -o crossSectionZ.mpg -ovc lavc -lavcopts vcodec=mpeg4:autoaspect
mplayer -loop 0 crossSectionZ.mpg
```

Showing only the blockMesh in paraFoam before the simulation is run:
```
paraFoam -block
```

#### Rescale stl files (from mm to m):

```
surfaceTransformPoints -scale '(0.001 0.001 0.001)' input.stl output.stl
```
#### Check Mesh Quality:

```
checkMesh -allGeometry -allTopology
```
#### Check stl file quality

Do this if you want to test whether you have a leak free surface file. Add all
regional files into one file by e.g.

```
cat <*>.stl >> <name>.stl 
```

Check surface by

```
surfaceCheck <name>.stl
```

m4 blockMeshDict.m4 > blockMeshDict

#### Procedure to create mesh file with AMI and to check for AMI properties

Make sure that the case has only 0.org and constant/polyMesh and 
constant/extendedFeatureEdgeMesh are deleted. The folder constant should only
contain the triSurface folder and the properties files. Do not use the overwrite
option. Also, make sure that the time steps in controlDict are long enough to
be able to observe the movement of the mesh. 

```
rm -r 0
rm -r constant/polyMesh
rm -r constant/extendedFeatureEdgeMesh
```
```
blockMesh
```
```
mkdir 0
```
```
cp -r constant/polyMesh 0/
```
```
surfaceFeatureExtract
```
```
snappyHexMesh
```
```
createBaffles
```
```
mergeOrSplitBaffles -split
```
```
cp -r <latestTimeFolder>/polyMesh constant/
```
```
moveDynamicMesh -checkAMI
```


