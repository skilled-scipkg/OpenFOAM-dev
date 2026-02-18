# openfoam source map: Applications

Generated from source roots:
- `applications`
- `src`
- `wmake`

Use this map only after exhausting the topic docs in
`skills/openfoam-applications/references/doc_map.md`.

## Topic query tokens
- `fieldMapping`
- `volField`
- `patchRegion`
- `collapseEdges`
- `mapFields`
- `pinch`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" applications src wmake`
- `rg -n "FatalError|Volume check OK|Multi region point" applications/test src`
- Search log phrases first, then inspect the corresponding source file.

## Suggested source entry points
- `applications/test/fieldMapping/Test-fieldMapping.C` | function checks: volume conservation, uniform/linear profile preservation, hard fail thresholds (`1e-10`)
- `applications/test/volField/Test-volField.C` | function checks: field read path and `SolverPerformance<symmTensor>` execution
- `applications/test/patchRegion/Test-patchRegion.C` | function checks: patch argument use (`args[1]`) and `Multi region point` detection
- `applications/utilities/preProcessing/mapFields/mapFields.C` | function checks: mapFields driver flow and mapping mode selection
- `applications/utilities/preProcessing/mapFields/MapVolFields.H` | function checks: mapped volume-field transfer branch
- `applications/utilities/preProcessing/mapFields/MapConsistentVolFields.H` | function checks: consistent-map branch behavior
- `src/meshTools/algorithms/PatchEdgeFaceWave/PatchEdgeFaceWave.H` | function checks: patch-edge-face wave propagation used by patch diagnostics
- `src/meshTools/algorithms/PatchEdgeFaceWave/patchEdgeFaceRegions.H` | function checks: per-face/per-edge region bookkeeping
