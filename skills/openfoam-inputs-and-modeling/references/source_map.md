# openfoam source map: Inputs and Modeling

Generated from source roots:
- `applications`
- `src`
- `wmake`

Use this map only after exhausting the topic docs in
`skills/openfoam-inputs-and-modeling/references/doc_map.md`.

## Topic query tokens
- `shockFluid`
- `maxwellSlip`
- `smoluchowskiJump`
- `skinFrictionCoeff`
- `wallShearStress`
- `codedFunctionObject`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" applications src wmake`
- `rg -n "shockFluid|maxwellSlip|smoluchowski|wallShearStress" applications src`
- Search from run-log terms and dictionary object names first.

## Suggested source entry points
- `tutorials/shockFluid/diffuserIntake/system/skinFrictionCoeff` | function checks: Cf definition and normalization using `Uinlet`, `Tinlet`, `pInlet`
- `applications/modules/shockFluid/shockFluid.H` | function checks: solver class structure and interfaces
- `applications/modules/shockFluid/shockFluid.C` | function checks: solver setup, Courant control, predictor/corrector orchestration
- `applications/modules/shockFluid/fluxPredictor.C` | function checks: flux construction and transport coupling
- `applications/modules/shockFluid/pressureCorrector.C` | function checks: pressure correction branch and coupling terms
- `applications/modules/shockFluid/correctDensity.C` | function checks: density update path
- `applications/modules/shockFluid/derivedFvPatchFields/U/maxwellSlipUFvPatchVectorField.H` | function checks: velocity-slip BC dictionary/API
- `applications/modules/shockFluid/derivedFvPatchFields/U/maxwellSlipUFvPatchVectorField.C` | function checks: velocity-slip BC evaluation
- `applications/modules/shockFluid/derivedFvPatchFields/T/smoluchowskiJumpTFvPatchScalarField.H` | function checks: thermal-jump BC dictionary/API
- `applications/modules/shockFluid/derivedFvPatchFields/T/smoluchowskiJumpTFvPatchScalarField.C` | function checks: thermal-jump BC evaluation
- `src/functionObjects/field/wallShearStress/wallShearStress.H` | function checks: wall-shear function-object interface
- `src/functionObjects/field/wallShearStress/wallShearStress.C` | function checks: wall-shear field computation
- `src/functionObjects/utilities/codedFunctionObject/codedFunctionObject.H` | function checks: coded FO interface and lifecycle
- `src/functionObjects/utilities/codedFunctionObject/codedFunctionObject.C` | function checks: dynamic compilation/load path for coded FO
