# Battery Model Decisions

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 6, 2026  

This page records the final modeling and calculation decisions used in the submitted MATLAB project. Detailed numerical checks are documented in `documentation/validation.md`.

## Final Decisions

| Project Area | Final Decision |
|---|---|
| Dataset | Use the complete `singleCellLifeTimeData.mat` dataset |
| Selected data | Use Cycle 1 |
| Time | Reset Cycle 1 so time begins at zero seconds |
| Charging interval | Use the first 301 seconds |
| Required model | Keep the fixed-3.6-V one-RC model as the assignment baseline |
| Additional models | Keep the shifted one-RC and two-RC models for comparison |
| Best voltage fit | Use the two-RC model as the strongest numerical fit |
| Current | Use measured current because no separate current model was provided |
| Voltage rate | Calculate using MATLAB’s `gradient` function |
| Delivered energy | Calculate by integrating measured power with `trapz` |
| Resistive loss | Use the internal-resistance measurements recorded in the dataset |
| Animation | Fill the battery using the normalized two-RC voltage response |

## Dataset and Interval

The final project uses:

```text
data/singleCellLifeTimeData.mat
```

Cycle 1 is selected using:

```matlab
cycleData = data(data.Cycle_Index == 1,:);
```

The cycle time is reset to zero, and the analysis uses the first 301 seconds.

```matlab
cycleData.Time_s = seconds( ...
    cycleData.DateTime-cycleData.DateTime(1));

chargeData = cycleData( ...
    cycleData.Time_s <= 301,:);
```

The 301-second interval was retained because it matches the charging segment used in the team’s original modeling work.

## Voltage Models

Three voltage models are included.

### Required Fixed-3.6-V One-RC Model

This model is kept because it is required by the project instructions. It produced the weakest fit because it assumes the battery begins at zero volts.

### Shifted One-RC Model

This model includes the measured starting voltage and produced a better fit than the required model.

### Two-RC Model

This model represents a fast voltage response and a slower voltage response. It produced the highest R-squared value and lowest RMSE.

| Model | R-squared | RMSE |
|---|---:|---:|
| Required fixed-3.6-V one-RC | 0.2458 | 0.3854 V |
| Shifted one-RC | 0.9109 | 0.1332 V |
| Two-RC | 0.9913 | 0.0418 V |

**Final model decision:** The required model remains the official baseline, while the two-RC model is identified as the best numerical description of the selected voltage response.

## Current, Power, and Energy

Measured current is used because the project does not provide a separate current-versus-time equation.

Power is calculated using matching measured voltage and current samples:

```matlab
powerDelivered_W = ...
    voltageMeasured .* currentMeasured;
```

Delivered energy is calculated using:

```matlab
energyDelivered_J = ...
    trapz(x,powerDelivered_W);
```

The final delivered-energy result is approximately:

```text
6859.3 J
1.9054 Wh
```

## Charging-Time Definitions

The required-model time to 80 percent is calculated from the required exponential equation.

Five time constants are used only as a mathematical practical-full estimate.

Measured charging behavior is reported separately:

| Measured Result | Value |
|---|---:|
| Time to 80% of the observed voltage rise | 20.4860 s |
| Maximum measured voltage | 3.5557 V |
| Time of maximum measured voltage | 300.4845 s |

The maximum measured-voltage time is not described as an exact 100 percent state-of-charge measurement.

## Internal Resistance and Energy Loss

The primary resistive-loss calculation uses the internal-resistance values recorded in the dataset.

```matlab
resistivePowerLoss_W = ...
    currentMeasured.^2 .* resistanceUsed_Ohm;

resistiveEnergyLoss_J = ...
    trapz(x,resistivePowerLoss_W);
```

The primary result is approximately:

```text
Representative resistance: 0.017634 ohm
Resistive energy loss: 230.45 J
Resistive energy loss: 0.06401 Wh
```

Alternative resistance methods from Sa and Maya are kept only as validation comparisons because they use different resistance definitions.

## Battery Animation

The GIF uses the normalized two-RC voltage response.

The battery:

- Fills from left to right
- Remains yellow from 0% through 79%
- Changes to green from 80% through 100%
- Displays normalized modeled-voltage progress

The displayed percentage is not presented as the battery’s exact state of charge.

## Final Output Decision

The final repository includes:

- MATLAB Live Script
- Plain MATLAB code
- PDF report
- Final figures
- CSV result tables
- Validation documentation
- Reproducibility instructions
- Battery-charging GIF

Detailed calculations and comparisons are located in:

```text
documentation/validation.md
```

Instructions for testing the project are located in:

```text
tests/README.md
```
