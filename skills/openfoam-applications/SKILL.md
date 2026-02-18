---
name: openfoam-applications
description: This skill should be used when users ask about applications in openfoam; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openfoam: Applications

## High-Signal Playbook

### Route conditions
- Use this skill for `applications/test/volField`, `applications/test/fieldMapping`, and `applications/test/patchRegion`.
- Route to `openfoam-examples-and-tutorials` for full tutorial runs under `tutorials/`.
- Route to `openfoam-inputs-and-modeling` for case parameterization and model/BC tuning.

### Triage questions
- Which case path: `applications/test/volField/cavity`, `applications/test/fieldMapping/pipe1D`, or `applications/test/patchRegion/cavity_pinched`?
- Is the goal a smoke run, a failed-run debug, or strict mapping/pinch invariants?
- For patch-region checks, which patch argument should be passed (default case patch is `fixedWalls`)?
- For parallel checks, is `applications/test/patchRegion/cavity_pinched/system/decomposeParDict` still set to `numberOfSubdomains 2`?

### Canonical workflow
1. Read local docs/scripts first:
- `applications/test/volField/README.txt`
- `applications/test/fieldMapping/README.txt`
- `applications/test/patchRegion/README`
- `applications/test/patchRegion/cavity_pinched/README.txt`
2. Compile executables:
- `cd applications/test/volField/cavity && wmake ..`
- `cd applications/test/fieldMapping/pipe1D && wmake ..`
- `cd applications/test/patchRegion && wmake`
3. Run `volField` and `fieldMapping` via case scripts:
- `applications/test/volField/cavity/Allrun`
- `applications/test/fieldMapping/pipe1D/Allrun`
4. Run patch pinch detection manually:
- `cd applications/test/patchRegion/cavity_pinched`
- `blockMesh`
- `collapseEdges`
- `decomposePar`
- `mpirun -np 2 Test-patchRegion -parallel fixedWalls`
5. Validate logs with the checkpoints below before changing source.

### Minimal working examples
```bash
cd applications/test/fieldMapping/pipe1D
. "$WM_PROJECT_DIR/bin/tools/RunFunctions"
wmake ..
runApplication blockMesh
runApplication Test-fieldMapping
```

```bash
cd applications/test/patchRegion/cavity_pinched
blockMesh
collapseEdges
decomposePar
mpirun -np 2 Test-patchRegion -parallel fixedWalls
```

### Pitfalls and fixes
- `Test-volField` or `Test-fieldMapping` not found: compile from the corresponding case directory with `wmake ..`.
- `Test-patchRegion` not found: compile from `applications/test/patchRegion` with `wmake`.
- `Test-patchRegion` exits early: pass patch argument `fixedWalls`; the code reads `args[1]`.
- Parallel mismatch: keep `numberOfSubdomains 2` in `applications/test/patchRegion/cavity_pinched/system/decomposeParDict` and launch with `mpirun -np 2`.
- No pinch diagnostics: verify `collapseEdgesCoeffs.minimumEdgeLength 0.0011` in `applications/test/patchRegion/cavity_pinched/system/collapseDict`.

### Convergence and validation checks
- `Test-fieldMapping` log contains `Volume check OK`.
- `Test-fieldMapping` log contains `Uniform field mapping check OK`, `Linear profile mapping check OK`, and `Uniform surfaceScalarField mapping check OK`.
- `Test-patchRegion` log prints `Multi region point:` for the pinched geometry.
- `Test-volField` log prints `Detailed SolverPerformance<symmTensor>` and finishes without `FatalError`.

### Source-code entry links
- `applications/test/fieldMapping/Test-fieldMapping.C` (mapping invariants and hard failure criteria)
- `applications/test/volField/Test-volField.C` (field IO and solver path in the test app)
- `applications/test/patchRegion/Test-patchRegion.C` (pinch detection and patch argument handling)
- `applications/utilities/preProcessing/mapFields/mapFields.C` (mapFields utility driver)
- `applications/utilities/preProcessing/mapFields/MapVolFields.H` (volume-field mapping behavior)
- `applications/utilities/preProcessing/mapFields/MapConsistentVolFields.H` (consistent mapping branch)
- `src/meshTools/algorithms/PatchEdgeFaceWave/PatchEdgeFaceWave.H` (patch-edge-face wave traversal)
- `src/meshTools/algorithms/PatchEdgeFaceWave/patchEdgeFaceRegions.H` (region bookkeeping used by pinch logic)

## Scope
- Handle questions about documentation grouped under the `applications` theme.
- Keep answers practical: runnable commands first, source deep dives only when docs and run logs are insufficient.

## Primary documentation references
- `applications/test/volField/README.txt`
- `applications/test/fieldMapping/README.txt`
- `applications/test/patchRegion/cavity_pinched/README.txt`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `skills/openfoam-applications/references/doc_map.md`.
- If ambiguity remains after docs, inspect `skills/openfoam-applications/references/source_map.md`.
- Cite exact file paths in responses.

## Tutorials and examples
- `tutorials`

## Test references
- `applications/test`
- `test`

## Optional deeper inspection
- `applications`
- `src`
- `wmake`

## Source entry points for unresolved issues
- `applications/test/fieldMapping/Test-fieldMapping.C`
- `applications/test/volField/Test-volField.C`
- `applications/test/patchRegion/Test-patchRegion.C`
- `applications/utilities/preProcessing/mapFields/mapFields.C`
- `applications/utilities/preProcessing/mapFields/MapVolFields.H`
- `applications/utilities/preProcessing/mapFields/MapConsistentVolFields.H`
- `src/meshTools/algorithms/PatchEdgeFaceWave/PatchEdgeFaceWave.H`
- `src/meshTools/algorithms/PatchEdgeFaceWave/patchEdgeFaceRegions.H`
- Prefer targeted source search: `rg -n "<symbol_or_keyword>" applications src wmake`.
