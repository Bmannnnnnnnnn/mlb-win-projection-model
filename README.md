Team Win Projection Model (Monte Carlo Simulation)

Overview
This project builds a **data-driven MLB projection model** to estimate the **New York Yankees’ 2026 season performance** using Statcast metrics, player-level projections, and Monte Carlo simulation.

The model converts individual player performance into team-level run estimates, then simulates thousands of seasons to generate a full distribution of possible outcomes.

---
Objective
To estimate:
- Expected wins over a 162-game season  
- Distribution of outcomes (best-case / worst-case scenarios)  
- Probabilities of key win thresholds (90+, 95+, 100+ wins)  
- Comparison to sportsbook market expectations (FanDuel)

---
 Methodology

 1. Data Collection
- Source: **MLB Statcast (Baseball Savant)**
- Metrics used:
  - Hitters: xwOBA, xSLG, Plate Appearances (PA)
  - Pitchers: xERA, Innings Pitched (IP)
- Data aggregated across **2023–2025 seasons**

---

2. Player Projections
- Created weighted multi-year projections (2023–2025)
- Scaled playing time to team totals:
  - 6200 PA (hitters)
  - 1458 IP (pitchers)

---

3. Age Adjustments
- Applied age-based performance curves:
  - Younger players → slight improvement
  - Prime-age players → stable performance
  - Older players → gradual decline

---

4. Injury & Replacement Modeling
- Modeled reduced playing time for injured players (e.g., Anthony Volpe, Gerrit Cole)
- Reallocated lost opportunities to replacement players
- Applied **replacement-level penalties** to simulate depth risk

---

5. Run Estimation

Runs Scored:
- Converted xwOBA → wRAA → team runs

Runs Allowed:
- Converted xERA → runs allowed
- Added injury-related replacement penalties

---

6. Win Projection (Pythagorean Expectation)

\[
Win\% = \frac{RS^2}{RS^2 + RA^2}
\]

Where:
- RS = Runs Scored  
- RA = Runs Allowed  

---

7. Monte Carlo Simulation
- Simulated **10,000 seasons**
- Introduced randomness:
  - ±7% variation in runs scored  
  - ±8% variation in runs allowed  

Generated:
- Win distribution
- Probability outcomes

---

Results

Base Projection
- Runs Scored: 814  
- Runs Allowed: 686  
- Expected Wins: **92.9**

---

Simulation Results
- Average Wins: **92.9**
- Median Wins: **92.9**
- 5th Percentile: **81 wins**
- 95th Percentile: **108 wins**

---

Probabilities
- 90+ Wins: **71%**
- 95+ Wins: **48%**
- 100+ Wins: **26%**
- Below .500: **5.5%**

---

Visualization

<img width="918" height="834" alt="Screenshot 2026-04-24 170310" src="https://github.com/user-attachments/assets/3ea24d39-2379-4275-863c-090bf33d14cc" />


*Distribution of simulated Yankees win outcomes (10,000 simulations)*

---

 Comparison to Market (FanDuel)

- Model Projection: **92.9 wins**
- FanDuel Win Total: **93.5 wins**

Interpretation:
- The model is **closely aligned with the betting market**
- Slight lean toward the **UNDER (52.9%)**, but not significant
- No clear betting edge which indicates a strong model calibration



The full simulation and projection model can be found here:
https://colab.research.google.com/drive/1yWaU53pPLXU5tNqbx-eQTYxHlkNao4uP
"""

