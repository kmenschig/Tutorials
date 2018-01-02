### Parallel Visualization of Two Cases:

Create paraview case file by typing:

```
touch $FOAM_RUN/<case>/<case>.OpenFOAM
```
in terminal.


### Processing in Parallel:
```
decomposePar (-force) in scotch mode
```
Solver execution with 4 processors with progress stored in log00 file:

```
mpirun -np 4 interFoam – parallel > log00 &
```

After the CFD results are captured in *.jpg files like U.jpg, the pictures can be summarized in a mpg file like U.mpg and played with mplayer:

```
mencoder "mf://*.jpg" -mf fps=2 -o U.mpg -ovc lavc -lavcopts vcodec=mpeg4:autoaspect
mplayer -loop 0 U.mpg
```

Showing only the blockMesh in paraFoam before the simulation is run:
```
paraFoam -block
```
Rescale stl files (from mm to m):
```
surfaceTransformPoints -scale '(0.001 0.001 0.001)' input_mm.stl output_m.stl
```
Check Mesh Quality:
```
checkMesh -allGeometry -allTopology
```
Check stl file quality
```
surface
```
m4 blockMeshDict.m4 > blockMeshDict
