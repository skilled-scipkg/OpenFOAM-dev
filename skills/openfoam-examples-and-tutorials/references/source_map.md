# openfoam source map: Examples and Tutorials

Generated from source roots:
- `applications`
- `src`
- `wmake`

Use this map only after exhausting the topic docs in
`skills/openfoam-examples-and-tutorials/references/doc_map.md`.

## Topic query tokens
- `wallCondensation`
- `wallBoiling`
- `TJunction`
- `createZones`
- `phaseChange`
- `nucleation`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" applications src wmake`
- `rg -n "wallBoiling|wallCondensation|createZones" applications src`
- Match failures from run logs to class/function names before broad code reading.

## Suggested source entry points
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensation.H` | function checks: wall-condensation model setup and dictionary interface
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensation.C` | function checks: condensation rate update and coupling path
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensationPhaseChangeRateFvPatchScalarField.H` | function checks: patch-field interface for phase-change rate
- `applications/modules/multiphaseEuler/fvModels/wallCondensation/wallCondensationPhaseChangeRateFvPatchScalarField.C` | function checks: patch-field evaluation path
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoiling.H` | function checks: wall-boiling model controls and public API
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoiling.C` | function checks: boiling source update and model coupling
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoilingPhaseChangeRateFvPatchScalarField.H` | function checks: patch coupling contract
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/wallBoilingPhaseChangeRateFvPatchScalarField.C` | function checks: patch-level phase-change computation
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/partitioningModels/partitioningModel/partitioningModelNew.C` | function checks: runtime model selection for partitioning
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/nucleationSiteModels/nucleationSiteModel/nucleationSiteModelNew.C` | function checks: runtime model selection for nucleation-site density
- `applications/modules/multiphaseEuler/fvModels/wallBoiling/departureDiameterModels/departureDiameterModel/departureDiameterModelNew.C` | function checks: runtime model selection for departure diameter
- `applications/modules/incompressibleFluid/incompressibleFluid.C` | function checks: predictor-corrector flow used by TJunction tutorial
- `applications/utilities/mesh/manipulation/createZones/createZones.C` | function checks: face/cell zone creation used before TJunction solve
