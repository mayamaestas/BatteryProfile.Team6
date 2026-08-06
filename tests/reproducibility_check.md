# Reproducibility Tests

This folder documents the checks used to confirm that the final MATLAB project runs correctly and reproduces the team’s results.

## Required Test File

Open:

`live_script/BatteryProfile_Team6_Final.mlx`

Use:

`data/singleCellLifeTimeData.mat`

## Test Procedure

1. Open the final Live Script in MATLAB.
2. Select **Run All**.
3. Choose `singleCellLifeTimeData.mat` when prompted.
4. Confirm that Cycle 1 is selected.
5. Confirm that the selected interval extends from 0 to approximately 301 seconds.
6. Confirm that all model-fitting sections run without errors.
7. Confirm that figures and CSV tables are exported.
8. Run the optional battery-animation section separately.

## Data Checks

- [x] The selected MAT file contains a variable named `data`
- [x] The `data` variable is a MATLAB table
- [x] The full dataset contains `Cycle_Index`
- [x] Cycle 1 is present
- [x] Time, voltage, current, and resistance variables are present
- [x] The selected interval contains enough data points
- [x] Invalid resistance values are handled before integration

## Model Checks

- [x] Required fixed-3.6-V one-RC model runs
- [x] Only `tau` is fitted in the required model
- [x] Shifted one-RC model runs
- [x] Two-RC model runs
- [x] R-squared and RMSE values are reported
- [x] Measured and fitted voltage curves are plotted together

## Expected Approximate Results

| Result | Expected Value |
|---|---:|
| Required-model tau | 0.3871 s |
| Required-model R-squared | 0.2458 |
| Required-model RMSE | 0.3854 V |
| Shifted one-RC tau | 7.902 s |
| Shifted one-RC R-squared | 0.9109 |
| Shifted one-RC RMSE | 0.1332 V |
| Two-RC tau1 | 0.4474 s |
| Two-RC tau2 | 22.51 s |
| Two-RC R-squared | 0.9913 |
| Two-RC RMSE | 0.0418 V |
| Measured 80% rise time | 20.4860 s |
| Maximum measured voltage | 3.5557 V |
| Delivered energy | 6859.3 J |

Small differences caused by numerical precision are acceptable.

## Output Checks

The following folders should contain the exported results:

- `results/figures`
- `results/tables`
- `results/animations`

The final GIF should show a battery that:

- Fills according to the normalized two-RC voltage response
- Appears yellow from 0% through 79%
- Changes to green from 80% through 100%

## Pass Criteria

The project passes the reproducibility test when:

- The Live Script runs from beginning to end without errors
- The expected model values are reproduced closely
- The figures and tables are generated
- The battery GIF is created successfully
- The results match the values documented in `documentation/validation.md`
**Date approved:**  
