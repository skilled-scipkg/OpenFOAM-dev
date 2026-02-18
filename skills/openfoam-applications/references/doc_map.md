# openfoam documentation map: Applications

Generated from documentation roots:
- `applications/test`
- `test`
- `tutorials`
- `doc`

Use this map to start and validate runs before opening source files.

Total docs grouped in this topic: 10

## Runnable entry docs
- `applications/test/volField/README.txt` | purpose: overview and pointer to runnable case
- `applications/test/volField/cavity/Allrun` | purpose: compile `Test-volField`, run `blockMesh`, execute app
- `applications/test/fieldMapping/README.txt` | purpose: mapping test intent and run pointer
- `applications/test/fieldMapping/pipe1D/Allrun` | purpose: compile `Test-fieldMapping`, run `blockMesh`, execute app
- `applications/test/patchRegion/README` | purpose: pinched-patch detection context
- `applications/test/patchRegion/cavity_pinched/README.txt` | purpose: exact collapse/decompose/parallel sequence

## Critical case inputs for validation
- `applications/test/patchRegion/cavity_pinched/system/blockMeshDict` | check: expected patch name `fixedWalls`
- `applications/test/patchRegion/cavity_pinched/system/collapseDict` | check: `minimumEdgeLength 0.0011`
- `applications/test/patchRegion/cavity_pinched/system/decomposeParDict` | check: `numberOfSubdomains 2`
- `applications/test/patchRegion/Make/files` | check: executable target `Test-patchRegion`
