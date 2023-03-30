# fluent2DMeshToFoam
Modified fluentMeshToFoam to have separated `frontAndBackPlanes`

Currently when converting a 2D fluent mesh, two surfaces will be combined to `frontAndBackPlanes` which makes it impossible to extrude. This modified utility creates `frontPlane` and `backPlane` instead.

## Usage
```
fluent2DMeshToFoam -2D <thickness> <filename>.msh
```
