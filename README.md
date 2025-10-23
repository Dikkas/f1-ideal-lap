# F1 2021 Qualifying – Ideal Lap Analysis

This project analyzes qualifying session data from the 2021 Formula 1 season to compute the Ideal Lap — a theoretical lap combining the best sector times from all drivers. The analysis explores timing consistency, circuit performance, and driver-specific contributions to understand how close real laps come to the theoretical maximum performance.

---

## Objectives  
The main goal is to identify the gap between the *Best Real Lap* (the fastest completed lap at each circuit) and the *Ideal Lap* (the sum of the best times in each sector).
By quantifying this difference, we can reveal:
- The optimization potential per circuit.
- The sectors where the most time can be gained.
- The drivers who most frequently contributed to the fastest sectors across the season.

---

## Dataset Summary  
- **Source**: FastF1 API
- **Season**: Formula 1 – 2021 (Qualifying Sessions)
- **Main Columns**:
  - *Driver*, *Circuit*, *Year*
  - *LapTime*, *Sector1Time*, *Sector2Time*, *Sector3Time*
  - *IsAccurate* (lap validity flag)
- **Granularity**: One row per lap per driver
- **Size**: ~2,000 qualifying laps (post-cleaning)


---

## Data Cleaning & Preparation  
1. **Integrity Filtering**:
    - Removed duplicate entries and laps marked as inaccurate (IsAccurate=False).
    - Dropped rows with missing or zero timing data.
2. **Standardization**:
    - Converted column names to snake_case.
    - Optimized string columns (driver, circuit) as categorical types.
3. **Timing Consistency**:
    - Verified the sum of sector times matched total lap_time within ±0.1s tolerance.
    - Confirmed no timing anomalies across circuits.

This produced a clean and consistent dataset suitable for time-based and comparative analysis.

---

## Exploratory Data Analysis (EDA)  
- **Lap Time Distribution**: Checked global range and outliers (60–100s typical).
- **Circuit Comparison**: Visualized lap time dispersion by circuit to observe differences in track length and difficulty.
- **Ideal Lap Calculation**: Combined the fastest recorded sector times per circuit to build the theoretical “perfect lap.”
- **Gap Analysis**:
  - Measured the time difference between *Ideal Lap* and *Best Real Lap*.
  - Expressed differences in both seconds and percentages to rank circuits by optimization potential.
- **Sector Contribution Heatmap**: Highlighted which sectors most influenced each circuit’s performance gap.
- **Driver Contribution**: Identified which drivers most frequently achieved the fastest sector times (sector-level dominance).

---

## Tools & Methods  
- **Python** (pandas, numpy) → data preparation.  
- **matplotlib, seaborn** → visualization.  
- **Google Colab** → development environment.  

---

## Repository Structure

<pre><code>

f1-ideal-lap/
│
├── notebook/
│ └── f1_ideal_lap.ipynb│
│
├── assets/
│ ├── OverallLapTimeDist.png
│ ├── BoxplotLapTimes.png
│ ├── LapTimesCircuit.png
│ ├── IdealBestDist.png
│ ├── ScatterplotIdealBest.png
│ └── SectorLevelIdealBest.png
│
└── README.md

</code></pre>

---

## Key Insights  
- *Ideal Lap* is always faster than the *Best Real Lap*, showing measurable improvement potential.
- Circuits like **Spa-Francorchamps** and **Imola** exhibit the largest theoretical gains.
- The driver contribution breakdown reveals clear sector-specific dominance patterns — no single driver dominates all sectors.

---

## License  
This project is released under the **MIT License**.

You are free to use, modify, and distribute the code with proper attribution.
