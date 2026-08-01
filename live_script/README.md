# MATLAB Live Script

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 1, 2026  
**Submission Deadline:** August 6, 2026  

This folder will hold the main MATLAB Live Script our team is using. Before uploading it, we need to confirm which version is the newest so we do not end up working from different files.

---

## Current Status

| Item | Status |
|---|---|
| Official Live Script selected | Needs confirmation |
| Official `.mlx` file uploaded | Not yet |
| Dataset loading and Cycle 1 selection | Complete |
| Charging interval | Needs validation |
| Required fixed 3.6 V model | In progress |
| Optional models | Ready for review |
| Task 3 calculations | In progress |
| Summary table | In progress |
| Final clean run | Not started |

---

## Official File

**Official filename:** To be confirmed during the August 1 meeting  

Before uploading the Live Script, we need to confirm:

- [ ] Who has the newest version
- [ ] The official filename
- [ ] The file includes the team’s newest work
- [ ] The script runs from beginning to end
- [ ] No newer copy is stored somewhere else

We should avoid uploading several copies named `final`, `final2`, or anything that makes it unclear which file is current.

---

## What the Script Must Include

### Data and Model

- [x] Load `singleCellLifeTimeData`
- [x] Select Cycle 1
- [x] Reset the time to zero
- [ ] Confirm and explain the charging interval
- [ ] Use the required model with `Vmax = 3.6 V`
- [ ] Fit and report `tau`
- [ ] Report R-squared and RMSE
- [ ] Plot the measured and fitted voltage together

### Calculations and Results

- [ ] Plot voltage, current, and power
- [ ] Confirm the charging-current sign
- [ ] Calculate voltage rate of change using `gradient`
- [ ] Calculate time to 80 percent charge
- [ ] Calculate practical full-charge time
- [ ] Calculate delivered energy using `trapz`
- [ ] State or source the internal-resistance value
- [ ] Calculate resistive energy loss using `I^2R`
- [ ] Generate the final summary table

### Explanation

- [ ] Explain the main results
- [ ] State the assumptions
- [ ] Explain the model limitations
- [ ] Compare the optional models only when the comparison is useful
- [ ] Include practical next steps

---

## How to Run the Project

1. Download or clone the full repository.
2. Open the official `.mlx` file in this folder.
3. Confirm MATLAB can access the dataset.
4. Select **Run All**.
5. Confirm the script finishes without stopping.
6. Check that all required figures and the summary table are created.
7. Compare the results with `documentation/validation.md`.

Another teammate should be able to download the project and run the Live Script without changing the file paths.

---

## MATLAB Setup

**MATLAB version:** To be confirmed  

**Required toolboxes:** To be confirmed  

**Known warnings or errors:** None recorded yet  

This information will be updated after the official file is selected and tested.

---

## Team Update Rules

- Tell the team before editing the official `.mlx` file.
- Only one person should edit the file at a time.
- Download the newest GitHub version before making changes.
- Run the entire script before uploading an update.
- Use a commit message that clearly explains what changed.
- Record important errors and corrections in `documentation/validation.md`.

---

## Upload Record

| Date | File Uploaded | Update Made | Uploaded By |
|---|---|---|---|
|  |  |  |  |
