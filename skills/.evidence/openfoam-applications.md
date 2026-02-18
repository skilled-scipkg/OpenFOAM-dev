# Evidence: openfoam-applications

## Primary docs
- `applications/test/volField/README.txt`
- `applications/test/fieldMapping/README.txt`
- `applications/test/patchRegion/cavity_pinched/README.txt`

## Primary source entry points
- `skills/openfoam-applications/references/doc_map.md`
- `applications/utilities/preProcessing/setFields/setVolFields.C`
- `applications/utilities/preProcessing/mapFields/MapVolFields.H`
- `applications/utilities/preProcessing/mapFields/MapConsistentVolFields.H`
- `applications/utilities/postProcessing/graphics/PVReaders/vtkPVFoam/vtkPVFoamVolFields.H`
- `src/functionObjects/field/volField/volFieldTemplates.C`
- `src/functionObjects/field/volField/volField.H`
- `src/functionObjects/field/volField/volField.C`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/uniformFixedValueGroupSurfaceAreaVolumeRatio/uniformFixedValueGroupSurfaceAreaVolumeRatioFvScalarFieldSource.H`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/uniformFixedValueGroupSurfaceAreaVolumeRatio/uniformFixedValueGroupSurfaceAreaVolumeRatioFvScalarFieldSource.C`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/singleGroupFraction/singleGroupFractionFvScalarFieldSource.H`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/singleGroupFraction/singleGroupFractionFvScalarFieldSource.C`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/ParkRogakGroupSurfaceAreaVolumeRatio/ParkRogakGroupSurfaceAreaVolumeRatioFvScalarFieldSource.H`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/ParkRogakGroupSurfaceAreaVolumeRatio/ParkRogakGroupSurfaceAreaVolumeRatioFvScalarFieldSource.C`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/interfacialGrowthGroupSurfaceAreaVolumeRatio/interfacialGrowthGroupSurfaceAreaVolumeRatioFvScalarFieldSource.H`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/interfacialGrowthGroupSurfaceAreaVolumeRatio/interfacialGrowthGroupSurfaceAreaVolumeRatioFvScalarFieldSource.C`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/interfacialGrowthGroupFraction/interfacialGrowthGroupFractionFvScalarFieldSource.H`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/interfacialGrowthGroupFraction/interfacialGrowthGroupFractionFvScalarFieldSource.C`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/hardSphereGroupSurfaceAreaVolumeRatio/hardSphereGroupSurfaceAreaVolumeRatioFvScalarFieldSource.H`
- `applications/modules/multiphaseEuler/populationBalance/derivedFvFieldSources/hardSphereGroupSurfaceAreaVolumeRatio/hardSphereGroupSurfaceAreaVolumeRatioFvScalarFieldSource.C`

## Extracted headings
- (none extracted)

## Executable command hints
- mpirun -np 2 Test-patchRegion -parallel

## Warnings and pitfalls
- (none extracted)
