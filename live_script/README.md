# MATLAB Live Script

**Team:** BatteryProfile.Team6  
**Updated by:** Yovany Gaspar  
**Date:** August 6, 2026  
**Submission Deadline:** August 6, 2026  

## Purpose of This Folder

This folder contains the official MATLAB files for the BatteryProfile.Team6 project. The Live Script is the main technical report and includes the data preparation, voltage models, electrical calculations, figures, summary tables, interpretation, assumptions, limitations, and conclusion.

## Official Files

- `BatteryProfile_Team6_Final.mlx`  
  Official MATLAB Live Script containing the complete analysis and displayed results.

- `BatteryProfile_Team6_Final.m`  
  Plain-text MATLAB version of the final analysis for code review and GitHub viewing.

- `BatteryProfile_Team6_Final.pdf`  
  Exported version of the completed Live Script for viewing without MATLAB.

The `.mlx` file is the primary project file. The `.m` and `.pdf` files are supporting versions of the same analysis. :contentReference[oaicite:0]{index=0}

## Current Status

| Item | Status |
|---|---|
| Official Live Script selected | Complete |
| Final `.mlx` file prepared | Complete |
| Plain-text `.m` file prepared | Complete |
| PDF exported | Complete |
| Dataset loading and Cycle 1 selection | Complete |
| Charging interval verified | Complete |
| Required fixed-3.6-volt model | Complete |
| Shifted one-RC and two-RC comparisons | Complete |
| Task 3 calculations | Complete |
| Summary tables | Complete |
| Sa and Maya validation | Complete |
| Final clean run | Complete |
| GitHub upload | Pending |
| Fresh-copy teammate test | Pending |

## Analysis Included

The final Live Script:

- Loads `singleCellLifeTimeData.mat`
- Selects Cycle 1
- Converts time to seconds and removes invalid or duplicate values
- Uses the selected 0-to-301-second charging interval
- Fits the required fixed-3.6-volt one-RC model
- Compares the required model with shifted one-RC and two-RC models
- Reports fitted parameters, R-squared values, and RMSE values
- Plots measured voltage, current, and power
- Calculates voltage rate of change
- Estimates charging times
- Calculates delivered energy using numerical integration
- Calculates internal resistive loss using measured current and dataset resistance
- Generates figures and summary tables
- Compares the final calculations with Sa’s and Maya’s results
- Explains the assumptions, limitations, and practical next steps

## How to Run the Project

1. Download or clone the complete GitHub repository.
2. Confirm the dataset is located at:

   `data/singleCellLifeTimeData.mat`

3. Open MATLAB and set the Current Folder to the repository root.
4. Open:

   `live_script/BatteryProfile_Team6_Final.mlx`

5. Confirm that:

   ```matlab
   createAnimation = false;
