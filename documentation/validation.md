# Analysis and Validation

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 1, 2026  
**Submission Deadline:** August 6, 2026  

This page records the calculations our team checked, the results we still need to confirm, and any corrections made before submission.

---

## Current Status

| Item | Status | Notes |
|---|---|---|
| Dataset and Cycle 1 | Complete | `singleCellLifeTimeData` |
| Time reset to zero | Complete | Time recorded in seconds |
| Charging interval | Needs validation | Currently 0–301 seconds |
| Current sign | Needs validation | Must be checked before energy calculation |
| Required fixed 3.6 V model | In progress | Only `tau` should be fitted |
| R² and RMSE | In progress | Final values not recorded |
| Voltage, current, and power plots | Ready for review | Labels and units must be checked |
| Voltage derivative | In progress | Uses `gradient` |
| 80 percent and full-charge times | In progress | Definitions must be approved |
| Delivered energy | In progress | Uses `trapz` |
| Resistive energy loss | Blocked | Internal resistance not finalized |
| Summary table | In progress | Waiting for final results |

---

## Data and Units

- [x] Dataset is identified
- [x] Selected cycle is identified
- [x] Time is measured in seconds
- [x] Voltage is measured in volts
- [x] Current is measured in amperes
- [ ] Missing, invalid, or duplicate values are checked
- [ ] Power is confirmed in watts
- [ ] Energy is confirmed in joules and watt-hours
- [ ] Resistance is confirmed in ohms
- [ ] Voltage rate is confirmed in volts per second

**Data issues found:**  

**Action taken:**  

---

## Charging Interval and Current Sign

The current code uses Cycle 1 from 0 to 301 seconds.

```matlab
chargeData = cycleData( ...
    cycleData.DateTime <= 301, :);
```

### Charging Interval

- [ ] Voltage graph supports the 301-second endpoint
- [ ] Current graph supports the 301-second endpoint
- [ ] The reason for choosing the interval is explained

**Final charging interval:**  

**Reason or evidence:**  

### Current Sign

- [ ] Charging current is positive
- [ ] Charging current is negative
- [ ] Delivered power is made positive before integration
- [ ] The sign convention is explained

**Current-sign decision:**  

**Power calculation used:**  

---

## Required Voltage Model

The required model is:

`V(t) = Vmax(1 - exp(-t/tau))`

The project template gives:

- `Vmax = 3.6 V`
- `tau` as the fitted parameter

### Model Check

- [ ] `Vmax` is fixed at 3.6 V
- [ ] Only `tau` is fitted
- [ ] Measured and fitted voltage are plotted together
- [ ] `tau` is reported with units
- [ ] R² is reported
- [ ] RMSE is reported
- [ ] Plot title, axes, units, and legend are included

### 2-RC Model Results

| Result | Value |
|---|---:|
| `tau 1` | 0.4474 |
| `tau 2` | 22.51  |
| R² | 0.9913 |
| RMSE | 0.0418  |

---

## Optional Model Comparison

| Model | R² | RMSE | Final Decision |
|---|---:|---:|---|
| Required fixed 3.6 V model |  |  | Keep |
| Shifted one-time-constant model |  |  |  |
| Two-time-constant model |  |  |  |

We will only keep the optional models if the required work is complete and we can clearly explain the comparison.

**Team decision:**  

---

## Analytical Results

| Result | Definition or Method | Final Value |
|---|---|---:|
| Voltage rate of change | `gradient` |  |
| Time to 80 percent charge | | | 36.0208 |
| Time to 100 percent charge| | |112.5650 |
| Delivered energy, joules | `trapz(time,power)` | 6.8593e+03 |
| Delivered energy, watt-hours | Joules divided by 3600 | 1.90536 |
| Internal resistance | Source or stated assumption |  |
| Resistive energy loss, joules | Integration of `I²R` |  |
| Resistive energy loss, watt-hours | Joules divided by 3600 |  |

### Analytical Check

- [ ] Derivative uses the correct time spacing
- [ ] 80 percent definition is explained
- [ ] Full-charge definition is explained
- [ ] Voltage percentage is not described as exact state of charge
- [ ] Power uses matching voltage and current samples
- [ ] Delivered power is positive during integration
- [ ] Energy units are correct
- [ ] Internal resistance has a source or is labeled as an assumption
- [ ] Resistive loss uses consistent units and `I²R`
- [ ] Results are physically reasonable

---

## Figures and Summary Table

- [ ] Measured and fitted voltage appear together
- [ ] Voltage, current, and power appear in three subplots
- [ ] Every axis includes a name and unit
- [ ] Titles clearly describe each result
- [ ] Legends identify measured and fitted curves
- [ ] Values use reasonable and consistent significant figures
- [ ] Summary table includes all required analytical results
- [ ] No duplicate figures are included

---

## Corrections Log

| Date | Problem Found | Correction Made | Checked By |
|---|---|---|---|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

---

## Final Technical Review

- [ ] Required model matches the project template
- [ ] Final values match the MATLAB output
- [ ] Calculations and units have been checked
- [ ] Assumptions are clearly stated
- [ ] Figures and summary table match the documented results
- [ ] Open limitations are explained before submission

**Reviewed by:**  

**Date reviewed:**  

**Final notes:**  
