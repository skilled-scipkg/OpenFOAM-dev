---
name: openfoam-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in openfoam; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openfoam: Inputs and Modeling

## High-Signal Playbook

### Route conditions
- Use this skill for case setup and model/BC parameterization in `tutorials/shockFluid/diffuserIntake`.
- Route to `openfoam-examples-and-tutorials` for broader tutorial execution patterns.
- Route to `openfoam-applications` for `applications/test/*` utility/test-app internals.

### Triage questions
- Are you reproducing the reference baseline (`plateAngle=10`) or changing geometry/physics?
- Do you need pressure-only, Cf-only, or both comparisons against Schulein data?
- Are input references consistent in `tutorials/shockFluid/diffuserIntake/0/U` (`Uinlet`), `0/T` (`Tinlet`), and `0/p` (`pInlet`)?
- Is `gnuplot` available for `tutorials/shockFluid/diffuserIntake/createGraphs`?
- Do you need turbulence/model changes in `tutorials/shockFluid/diffuserIntake/constant/momentumTransport`?

### Canonical workflow
1. Read case context in `tutorials/shockFluid/diffuserIntake/README`.
2. Set geometry knob `plateAngle` in `tutorials/shockFluid/diffuserIntake/system/blockMeshDict`.
3. Run baseline sequence using `tutorials/shockFluid/diffuserIntake/Allrun`.
4. If running manually, execute `blockMesh`, `foamRun`, then `foamPostProcess` graph extraction exactly as in `Allrun`.
5. Compare CFD with reference data using `tutorials/shockFluid/diffuserIntake/createGraphs`.
6. If mismatch persists, inspect `system/functions`, `system/skinFrictionCoeff`, `system/fvSchemes`, and `system/fvSolution` before source changes.

### Minimal working example
```bash
cd tutorials/shockFluid/diffuserIntake
./Allrun
```

### Pitfalls and fixes
- Graph generation skipped: `createGraphs` exits when `gnuplot` is unavailable.
- Wrong benchmark branch: keep `plateAngle 10` when comparing against supplied beta=10 reference columns.
- Cf scaling mismatch: keep `Uinlet`, `Tinlet`, and `pInlet` coherent with `tutorials/shockFluid/diffuserIntake/system/skinFrictionCoeff` and `constant/physicalProperties`.
- Missing Cf field output: ensure `tutorials/shockFluid/diffuserIntake/system/functions` includes `wallShearStress` and `skinFrictionCoeff`.
- Unstable transient behavior: retain conservative controls in `tutorials/shockFluid/diffuserIntake/system/controlDict` (`deltaT 1e-7`, `endTime 2e-3`) unless intentionally changed.

### Convergence and validation checks
- `postProcessing/graph/0.002/line.xy` exists after `foamPostProcess`.
- `Cf.png` and `p.png` are created by `createGraphs` and overlay CFD with `schulein1996Cf.txt` and `schulein1996P.txt`.
- Pressure and Cf trends along `x` are qualitatively aligned with reference datasets.
- Solver settings remain at intended tolerances in `tutorials/shockFluid/diffuserIntake/system/fvSolution`.

### Source-code entry links
- `tutorials/shockFluid/diffuserIntake/system/skinFrictionCoeff` (coded function object for Cf definition)
- `applications/modules/shockFluid/shockFluid.H` (solver class API and state)
- `applications/modules/shockFluid/shockFluid.C` (solver setup and control flow)
- `applications/modules/shockFluid/fluxPredictor.C` (flux scheme behavior)
- `applications/modules/shockFluid/pressureCorrector.C` (pressure update behavior)
- `applications/modules/shockFluid/correctDensity.C` (density update path)
- `applications/modules/shockFluid/derivedFvPatchFields/U/maxwellSlipUFvPatchVectorField.H` (velocity slip BC interface)
- `applications/modules/shockFluid/derivedFvPatchFields/U/maxwellSlipUFvPatchVectorField.C`
- `applications/modules/shockFluid/derivedFvPatchFields/T/smoluchowskiJumpTFvPatchScalarField.H` (temperature jump BC interface)
- `applications/modules/shockFluid/derivedFvPatchFields/T/smoluchowskiJumpTFvPatchScalarField.C`
- `src/functionObjects/field/wallShearStress/wallShearStress.C` (wall shear calculation used by Cf)
- `src/functionObjects/utilities/codedFunctionObject/codedFunctionObject.C` (runtime coded function-object execution path)

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses runnable and diagnostic-first; use source only when case dictionaries and scripts are insufficient.

## Primary documentation references
- `tutorials/shockFluid/diffuserIntake/README`
- `tutorials/shockFluid/diffuserIntake/Allrun`
- `tutorials/shockFluid/diffuserIntake/createGraphs`
- `tutorials/shockFluid/diffuserIntake/schulein1996P.txt`
- `tutorials/shockFluid/diffuserIntake/schulein1996Cf.txt`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `skills/openfoam-inputs-and-modeling/references/doc_map.md`.
- If ambiguity remains after docs, inspect `skills/openfoam-inputs-and-modeling/references/source_map.md`.
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
- `applications/modules/shockFluid/shockFluid.H`
- `applications/modules/shockFluid/shockFluid.C`
- `applications/modules/shockFluid/fluxPredictor.C`
- `applications/modules/shockFluid/pressureCorrector.C`
- `applications/modules/shockFluid/correctDensity.C`
- `applications/modules/shockFluid/derivedFvPatchFields/U/maxwellSlipUFvPatchVectorField.H`
- `applications/modules/shockFluid/derivedFvPatchFields/U/maxwellSlipUFvPatchVectorField.C`
- `applications/modules/shockFluid/derivedFvPatchFields/T/smoluchowskiJumpTFvPatchScalarField.H`
- `applications/modules/shockFluid/derivedFvPatchFields/T/smoluchowskiJumpTFvPatchScalarField.C`
- `src/functionObjects/field/wallShearStress/wallShearStress.C`
- `src/functionObjects/utilities/codedFunctionObject/codedFunctionObject.C`
- Prefer targeted source search: `rg -n "<symbol_or_keyword>" applications src wmake`.
