# Battery Dataset

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 1, 2026  

This folder contains information about the dataset used in our battery charging analysis.

---

## Dataset Information

| Item | Information |
|---|---|
| Dataset | `singleCellLifeTimeData` |
| Source | MathWorks example data |
| MATLAB file | `singleCellLifeTimeData.mat` |
| Selected cycle | Cycle 1 |
| Time unit | Seconds |
| Voltage unit | Volts |
| Current unit | Amperes |

The main variables used in our analysis are:

- `DateTime`
- `Voltage`
- `Current`
- `Cycle_Index`

---

## How the Data Is Loaded

The current MATLAB code downloads and unzips the dataset automatically using `downloadSupportFile`.

It then loads:

`singleCellLifeTimeData.mat`

Because the script can download the data, the team still needs to decide whether the `.mat` file should also be stored in this folder.

---

## Data Folder Decision

- [ ] Confirm that the automatic download works for another teammate
- [ ] Decide whether to upload `singleCellLifeTimeData.mat`
- [ ] Confirm the official Live Script does not depend on a personal file path
- [ ] Record any data-access instructions in the main README

**Final decision:** To be confirmed after the clean test.

---

## Files in This Folder

| File | Purpose | Status |
|---|---|---|
| `README.md` | Dataset information and access instructions | Complete |
| `singleCellLifeTimeData.mat` | Local copy of the MathWorks dataset | Not yet decided |

The team should avoid storing extra or renamed copies of the same dataset.
