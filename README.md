# Battery Charging Analysis Using MATLAB

## Overview
This project analyzes lithium-ion battery charging data using MATLAB. The goal is to model the battery charging of a lithium-ion battery cell as a simple first-order RC system. This was completed by fitting experimental voltage data with equivalent circuit models and comparing their performance.

## Objectives
- Import and analyze battery lifetime data.
- Plot voltage, current, and power versus time.
- Extract the charging portion of the first battery cycle.
- Analyze rate of voltage change at different Intervals
- Compute total energy delivered to battery, using integration 
- Fit a one-RC charging model.
- Fit a two-RC charging model.
- Compare model performance using goodness-of-fit statistics.
- Calculate and visualize charging power.
- Calculate time required to reach 80 and 100 percent charge and estimated of resistive energy loss

## Dataset
This project uses the `singleCellLifeTimeData` dataset provided by MATLAB. The dataset contains battery measurements including voltage, current, time, and cycle number.

## Methods
The analysis includes:
1. Loading the battery dataset.
2. Selecting the first charging cycle.
3. Plotting voltage and current over time.
4. Fitting one-RC and two-RC exponential charging models.
5. Comparing model accuracy.
6. Comparing with handwritten calculations
7. Plotting voltage, current, and power during charging.

## Results
The project generates:
- Voltage vs. Time
- Current vs. Time
- One-RC model fit
- Two-RC model fit
- Power vs. Time
- Summary table

## Software
- MATLAB
- Curve Fitting Toolbox


## Repository Structure

```
MATLAB-simulink-challenge-project/
├── README.md                    
├── data/
│   ├── README.md                 
│   └── singleCellLifeTimeData.mat
├── live_script/
│   └── battery_charging_analysis.mlx
├── results/
│   ├── figures/                 
│   └── tables/                   
├── documentation/
│   ├── assumptions.md
│   ├── validation.md
│   └── meeting_notes/
└── tests/
    └── reproducibility_check.md
```
