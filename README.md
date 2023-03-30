# fluent2DMeshToFoam
Modified fluentMeshToFoam with separated `frontAndBackPlanes`.

Currently when converting a 2D fluent mesh, two surfaces will be combined to `frontAndBackPlanes` which makes it impossible to extrude. This modified utility creates `frontPlane` and `backPlane` instead.

## Usage
```
fluent2DMeshToFoam -2D <thickness> <filename>.msh
```
Then it is possible to extrude the mesh with the following `extrudeMeshDict`
```
constructFrom patch;
sourceCase      "<case>";
sourcePatches   (frontPlane);
exposedPatchName frontPlane;

flipNormals false;
extrudeModel        linearNormal;
nLayers             100;
expansionRatio      1.1;
linearNormalCoeffs
{
    thickness       0.1;
}

mergeFaces false;
mergeTol 0;
```
