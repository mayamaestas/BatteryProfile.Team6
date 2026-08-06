# Analysis and Validation

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 6, 2026  
**Submission Deadline:** August 6, 2026  

This page records the final calculations checked by the team, the corrections made during testing, and the results confirmed before submission.

## Current Status

| Item | Status | Notes |
|---|---|---|
| Dataset and Cycle 1 | Complete | Full `singleCellLifeTimeData.mat` dataset used |
| Time reset to zero | Complete | Cycle 1 time begins at 0 seconds |
| Charging interval | Complete | First 301 seconds of Cycle 1 |
| Current sign | Complete | Positive current represents charging |
| Required fixed 3.6 V model | Complete | Only `tau` was fitted |
| R² and RMSE | Complete | Final values recorded |
| Voltage, current, and power plots | Complete | Labels, titles, and units checked |
| Voltage derivative | Complete | Calculated using `gradient` |
| Charging-time calculations | Complete | Required and measured definitions are separated |
| Delivered energy | Complete | Calculated using `trapz` |
| Resistive energy loss | Complete | Dataset resistance used for the primary result |
| Summary tables | Complete | CSV tables exported to `results/tables` |
| GIF animation | Complete | Battery fills using normalized two-RC voltage progress |

## Data and Units

- [x] Dataset is identified
- [x] Selected cycle is identified
- [x] Time is measured in seconds
- [x] Voltage is measured in volts
- [x] Current is measured in amperes
- [x] Missing or invalid values are checked
- [x] Power is confirmed in watts
- [x] Energy is confirmed in joules and watt-hours
- [x] Resistance is confirmed in ohms
- [x] Voltage rate is confirmed in volts per second

### Data Issues Found

The smaller dataset did not contain the `Cycle_Index` variable and initially included a zero-current rest period. This prevented the code from reliably reproducing Sa’s Cycle 1 selection.

### Action Taken

The final analysis uses the full `singleCellLifeTimeData.mat` dataset. Cycle 1 is selected directly using the `Cycle_Index` column before the time is reset and the 301-second interval is extracted.

## Charging Interval and Current Sign

The final code selects Cycle 1 and resets its time:

```matlab
cycleData = data(data.Cycle_Index == 1,:);

cycleData.Time_s = seconds( ...
    cycleData.DateTime - cycleData.DateTime(1));
