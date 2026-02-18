---
name: openfoam-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in openfoam; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openfoam: Examples and Tutorials

## High-Signal Playbook

### Route conditions
- Use this skill for runnable tutorials under `tutorials/incompressibleFluid/TJunction`, `tutorials/multiphaseEuler/wallCondensation`, and wall-boiling validation families.
- Route to `openfoam-inputs-and-modeling` for deep tuning of `tutorials/shockFluid/diffuserIntake` inputs/models.
- Route to `openfoam-applications` for `applications/test/*` utility/test-app internals.

### Triage questions
- Which case family is required: `wallCondensation`, `TJunction`, or one of the wall-boiling cases?
- Is the goal quick run completion or reproduction of validation plots vs experiment?
- Is `gnuplot` available for `validation/createGraph*` scripts?
- Are parallel runs acceptable (wall-boiling `Allrun` uses decomposition and `runParallel`)?

### Canonical workflow
1. Open case-level docs/scripts:
- `tutorials/multiphaseEuler/wallCondensation/README.txt`
- `tutorials/incompressibleFluid/TJunction/README.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperseTwoGroups/Allrun`
- `tutorials/multiphaseEuler/wallBoilingPolydisperse/Allrun`
- `tutorials/multiphaseEuler/wallBoilingIATE/Allrun`
- `tutorials/multiRegion/CHT/wallBoiling/Allrun`
2. Run the case-local `Allrun` script from the selected case directory.
3. If `Allrun` is not usable, mirror its sequence (`blockMesh`, optional `extrudeMesh`/`createZones`, solver run, reconstruct/post-process).
4. Run validation scripts where present (`validation/createGraph*`) and compare against bundled `validation/exptData/*`.
5. Escalate to source only when outputs diverge and docs/scripts are insufficient.

### Minimal working examples
```bash
cd tutorials/multiphaseEuler/wallCondensation
./Allrun
```

```bash
cd tutorials/incompressibleFluid/TJunction
./Allrun
```

```bash
cd tutorials/multiphaseEuler/wallBoilingPolydisperseTwoGroups
./Allrun
```

### Pitfalls and fixes
- `createGraph*` scripts skipped: install `gnuplot` or treat plotting as optional post-processing.
- `Allrun` helper errors: load OpenFOAM env before running (`source etc/bashrc` from repo root).
- TJunction fails after meshing: `createZones` is mandatory and already encoded in `tutorials/incompressibleFluid/TJunction/Allrun`.
- Wall-boiling output files missing: do not skip `reconstructPar -latestTime` in the provided `Allrun` scripts.

### Convergence and validation checks
- WallCondensation: `postProcessing/outflow/0/surfaceFieldValue.dat` exists and `validation/wallCondensation.eps` is generated when `gnuplot` is available.
- TJunction: `postProcessing/probes` data is generated and outlet/face-zone flow-rate outputs are written under `postProcessing`.
- Wall-boiling (single/multi-phase Euler): `postProcessing/graph/<latest>/line.xy` and `postProcessing/patchWallBoilingProperties/<latest>/patch.xy` exist.
- Wall-boiling (CHT): `postProcessing/fluid/graph/<latest>/line.xy` and `postProcessing/fluid/patchWallBoilingProperties/<latest>/patch.xy` exist.
- Wall-boiling validation plots: `validation/<caseName>.eps` and `validation/<caseName>Properties.eps` are generated when `gnuplot` is available.

### Source-code entry links
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensation.H` (wall-condensation model entry)
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensation.C`
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensationPhaseChangeRateFvPatchScalarField.H`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoiling.H` (wall-boiling model entry)
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoiling.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/partitioningModels/partitioningModel/partitioningModelNew.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/nucleationSiteModels/nucleationSiteModel/nucleationSiteModelNew.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/departureDiameterModels/departureDiameterModel/departureDiameterModelNew.C`
- `applications/modules/incompressibleFluid/incompressibleFluid.C` (TJunction solver behavior path)
- `applications/utilities/mesh/manipulation/createZones/createZones.C` (TJunction zone setup utility)

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep answers runnable first; only deepen into source after validating case scripts and outputs.

## Primary documentation references
- `tutorials/multiphaseEuler/wallCondensation/README.txt`
- `tutorials/incompressibleFluid/TJunction/README.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperseTwoGroups/validation/exptData/vof_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperseTwoGroups/validation/exptData/d_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperseTwoGroups/validation/exptData/T_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperse/validation/exptData/vof_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperse/validation/exptData/d_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingPolydisperse/validation/exptData/T_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingIATE/validation/exptData/vof_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingIATE/validation/exptData/d_deb1.txt`
- `tutorials/multiphaseEuler/wallBoilingIATE/validation/exptData/T_deb1.txt`
- `tutorials/multiRegion/CHT/wallBoiling/validation/exptData/vof_deb1.txt`
- `tutorials/multiRegion/CHT/wallBoiling/validation/exptData/d_deb1.txt`
- `tutorials/multiRegion/CHT/wallBoiling/validation/exptData/T_deb1.txt`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `skills/openfoam-examples-and-tutorials/references/doc_map.md`.
- If ambiguity remains after docs, inspect `skills/openfoam-examples-and-tutorials/references/source_map.md`.
- Cite exact documentation file paths in responses.

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
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensation.H`
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensation.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoiling.H`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoiling.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/partitioningModels/partitioningModel/partitioningModelNew.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/nucleationSiteModels/nucleationSiteModel/nucleationSiteModelNew.C`
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/departureDiameterModels/departureDiameterModel/departureDiameterModelNew.C`
- `applications/modules/incompressibleFluid/incompressibleFluid.C`
- `applications/utilities/mesh/manipulation/createZones/createZones.C`
- Prefer targeted source search: `rg -n "<symbol_or_keyword>" applications src wmake`.
