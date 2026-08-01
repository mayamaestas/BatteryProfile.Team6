# Battery Model Decisions

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 1, 2026  

This page keeps track of what our team has decided so far and what we still need to confirm. We are using it so everyone works from the same information while we finish the MATLAB Live Script and calculations.

---

## Current Status

| Project Item | Status |
|---|---|
| Dataset loaded | Complete |
| Cycle 1 selected | Complete |
| Time reset to zero | Complete |
| Charging interval selected | Needs verification |
| One-RC model | In progress |
| Two-time-constant model | Ready for review |
| Voltage, current, and power plots | Ready for review |
| Task 3 calculations | In progress |
| Summary table | In progress |
| Reproducibility test | Not started |

---

## Dataset

We are using the MathWorks `singleCellLifeTimeData` dataset.

Our current setup is:

- **Selected cycle:** Cycle 1
- **Time units:** seconds
- **Voltage units:** volts
- **Current units:** amperes

The code resets Cycle 1 so that the time begins at zero.

```matlab
cycleData = data(data.Cycle_Index == 1, :);

cycleData.DateTime = seconds( ...
    cycleData.DateTime - cycleData.DateTime(1));
```

---

## Charging Interval

Our current code uses the first 301 seconds as the charging section.

```matlab
chargeData = cycleData( ...
    cycleData.DateTime <= 301, :);
```

We still need to confirm from the voltage and current graphs that 301 seconds is the correct endpoint.

- **Current interval:** 0 to 301 seconds
- **Status:** Needs verification
- **Reason:** To be confirmed during the August 1 meeting

---

## Required One-RC Model

The project template asks us to use:

`V(t) = Vmax(1 - exp(-t/tau))`

The required values are:

- `Vmax = 3.6 V`
- `tau` is the fitted time constant

We still need to confirm that the final Live Script includes this exact model with 3.6 V fixed.

### Still Needed

- [ ] Run or verify the fixed 3.6 V model
- [ ] Record `tau`
- [ ] Record R-squared
- [ ] Record RMSE
- [ ] Plot the measured and fitted voltage together

---

## Shifted One-Time-Constant Model

Our current code also uses a model with a starting voltage:

`V(t) = V0 + A(1 - exp(-t/tau))`

We tested this because the real battery does not begin at zero volts.

- `V0` is the starting voltage
- `A` is the voltage increase
- `tau` is the time constant

We will compare this model with the required model and explain whether including the starting voltage improves the fit.

---

## Two-Time-Constant Model

We also tested:

`V(t) = V0 + A1(1 - exp(-t/tau1)) + A2(1 - exp(-t/tau2))`

This is an extra model and is not required by the original project.

We will only keep it if:

1. The required project work is completed first.
2. It improves the results.
3. We can explain what the extra parameters mean.

- **Current status:** Ready for review
- **Final decision:** Not made yet

---

## Current and Power

Power is calculated using:

`P = V × I`

Our current code is:

```matlab
power = chargeData.Voltage .* chargeData.Current;
```

We still need to confirm whether charging current is positive or negative in the dataset.

This decision affects how we calculate delivered power and total energy.

### Still Needed

- [ ] Check the current sign
- [ ] Keep the original sign in the current graph
- [ ] Use positive delivered power for the energy calculation
- [ ] Explain the sign convention in the final project

---

## Charge Thresholds

We have not finalized how we will define 80 percent and full charge.

One option for 80 percent is:

`V80 = Vinitial + 0.80(3.6 - Vinitial)`

This would mean 80 percent of the voltage increase from the starting voltage to 3.6 V.

For practical full charge, we still need to decide whether to use:

- The first measured point at 3.6 V
- A 99 percent threshold
- The final point in the charging interval

### Still Needed

- [ ] Approve the 80 percent definition
- [ ] Approve the practical full-charge definition
- [ ] Use the same definitions in the code and summary table

---

## Energy and Resistance

Total delivered energy will be calculated from the power-versus-time data using `trapz`.

```matlab
energyDelivered_J = trapz( ...
    chargeData.DateTime, ...
    powerDelivered);
```

Resistive power loss will be estimated using:

`P_loss = I^2R`

We still need to agree on an internal-resistance value. We will either use a reliable source or clearly state that the value is an assumption.

### Still Needed

- [ ] Confirm the power sign
- [ ] Calculate total energy in joules
- [ ] Convert energy to watt-hours
- [ ] Select and justify internal resistance
- [ ] Calculate resistive energy loss

---

## Decisions for the August 1 Meeting

- [ ] Confirm the 301-second charging endpoint
- [ ] Confirm the current sign
- [ ] Verify the fixed 3.6 V model
- [ ] Record `tau`, R-squared, and RMSE
- [ ] Approve the 80 percent definition
- [ ] Approve the full-charge definition
- [ ] Select an internal-resistance value
- [ ] Decide whether the two-time-constant model stays
- [ ] Finish the derivative calculation
- [ ] Finish the energy calculations
- [ ] Create the summary table

---

## Before We Call the Project Finished

Another teammate needs to download the files and run the Live Script without fixing file paths or missing information.

The final run should recreate:

- All required graphs
- Model-fit results
- Charging-time results
- Energy calculations
- Resistive-loss estimate
- Final summary table
