# Battery Charging Analysis Using MATLAB

**Team:** BatteryProfile.Team6  
**Program:** Engineering Pathway Program  
**Instructor:** Kevin Graham  
**Submission Deadline:** August 6, 2026  

## Overview

This project uses MATLAB to analyze the charging behavior of a lithium-ion battery cell. Our team models the experimental voltage data using equivalent-circuit charging models and compares how well each model represents the measured battery response.

The analysis includes voltage, current, power, charging time, delivered energy, voltage rate of change, and estimated resistive energy loss. The required one-RC model serves as the baseline for the project. Additional models are included only when they provide a useful comparison that our team can clearly explain.

---

## Team Members

| Team Member | Role |
|---|---|
| Yovany Gaspar | Project Manager and QA Lead |
| Sa | Modeling Lead |
| Maya Maestas | Analysis and Validation Lead |
| Kailey Neri | Documentation and Visualization Lead |

---

## Project Objectives

The main objectives of this project are to:

- Import and inspect battery lifetime data
- Select and isolate the charging portion of Cycle 1
- Reset the selected cycle so time begins at zero seconds
- Plot voltage, current, and power versus time
- Fit the required one-RC charging model
- Report the fitted time constant, R-squared, and RMSE
- Compare the required model with optional expanded models
- Analyze voltage rate of change during charging
- Estimate the time required to reach 80 percent charge
- Define and calculate a practical full-charge time
- Calculate the total energy delivered to the battery
- Estimate resistive energy loss using an internal-resistance value
- Compare selected MATLAB results with hand calculations
- Present the final results through figures and a summary table

---

## Dataset

This project uses the MathWorks `singleCellLifeTimeData` dataset. The dataset contains measurements from multiple battery charging and discharging cycles.

The main variables used in the analysis are:

| Variable | Description | Unit |
|---|---|---|
| `DateTime` | Recorded time | Converted to seconds |
| `Voltage` | Battery-cell voltage | Volts |
| `Current` | Battery current | Amperes |
| `Cycle_Index` | Battery-cycle number | Unitless |

Our current analysis uses Cycle 1. Additional dataset information and access instructions are available in [`data/README.md`](data/README.md).

---

## Analysis Methods

The MATLAB analysis follows these main steps:

1. Download and load the battery dataset.
2. Inspect the available variables and units.
3. Select Cycle 1.
4. Reset the cycle time so it begins at zero seconds.
5. Isolate the charging interval.
6. Use the voltage and current graphs to review the selected interval.
7. Fit the required one-RC charging model.
8. Report the fitted time constant and goodness-of-fit results.
9. Compare optional shifted and two-time-constant models when useful.
10. Calculate charging power from matching voltage and current samples.
11. Calculate voltage rate of change using `gradient`.
12. Estimate charge times using team-approved definitions.
13. Calculate delivered energy using numerical integration with `trapz`.
14. Estimate resistive energy loss using `I^2R`.
15. Compare selected results with hand calculations.
16. Generate the final figures and summary table.

The required baseline model is:

`V(t) = Vmax(1 - exp(-t/tau))`

For this model:

- `Vmax = 3.6 V`
- `tau` is the fitted time constant

Optional models will only remain in the final project when the required analysis is complete and the comparison can be explained clearly.

---

## Project Outputs

The completed project will include:

- Measured and fitted voltage figure
- Voltage-versus-time figure
- Current-versus-time figure
- Power-versus-time figure
- Voltage rate-of-change results
- Fitted value of `tau`
- R-squared and RMSE
- Time to 80 percent charge
- Practical full-charge time
- Delivered energy in joules and watt-hours
- Internal-resistance assumption or source
- Estimated resistive energy loss
- Final summary table
- Optional model-comparison results

---

## Software

The project uses:

- MATLAB
- Curve Fitting Toolbox

The final MATLAB version, required toolboxes, and known warnings will be recorded in [`live_script/README.md`](live_script/README.md) after the official Live Script is tested.

---

## Repository Structure

```text
MATLAB-simulink-challenge-project/
├── README.md
├── data/
│   ├── README.md
│   └── singleCellLifeTimeData.mat
├── live_script/
│   ├── README.md
│   └── battery_charging_analysis.mlx
├── results/
│   ├── figures/
│   │   └── README.md
│   └── tables/
│       └── README.md
├── documentation/
│   ├── assumptions.md
│   ├── validation.md
│   └── meeting_notes/
│       ├── 2026-07-24_meeting.md
│       └── 2026-08-01_meeting.md
└── tests/
    └── reproducibility_check.md
