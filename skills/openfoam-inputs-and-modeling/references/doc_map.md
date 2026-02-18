# openfoam documentation map: Inputs and Modeling

Generated from documentation roots:
- `tutorials`
- `doc`
- `applications/test`
- `test`

Use this map to reproduce the diffuser case before source inspection.

Total docs grouped in this topic: 11

## Case-level entry docs and scripts
- `tutorials/shockFluid/diffuserIntake/README` | purpose: geometry/modeling intent and reference context
- `tutorials/shockFluid/diffuserIntake/Allrun` | purpose: canonical run and post-processing sequence
- `tutorials/shockFluid/diffuserIntake/createGraphs` | purpose: CFD-vs-reference plotting (`Cf.png`, `p.png`)
- `tutorials/shockFluid/diffuserIntake/system/blockMeshDict` | key input: `plateAngle`
- `tutorials/shockFluid/diffuserIntake/system/controlDict` | key input: time-step and end-time controls
- `tutorials/shockFluid/diffuserIntake/system/functions` | key input: enabled function objects (`wallShearStress`, `skinFrictionCoeff`)
- `tutorials/shockFluid/diffuserIntake/system/skinFrictionCoeff` | key input: Cf normalization and coded function-object logic
- `tutorials/shockFluid/diffuserIntake/system/fvSchemes` | key input: discretization controls
- `tutorials/shockFluid/diffuserIntake/system/fvSolution` | key input: solver tolerances and controls
- `tutorials/shockFluid/diffuserIntake/schulein1996P.txt` | validation: pressure reference data
- `tutorials/shockFluid/diffuserIntake/schulein1996Cf.txt` | validation: skin-friction reference data
