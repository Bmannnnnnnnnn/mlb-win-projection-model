# mlb-win-projection-model
MLB win projection model using Statcast data, Pythagorean expectation, and Monte Carlo simulation
MLB Team Win Projection Model (Monte Carlo Simulation)
Overview

This project builds a data-driven model to project MLB team performance, specifically estimating the New York Yankees' expected wins for the 2026 season.

Using Statcast-based metrics (xwOBA, xERA), the model converts player-level projections into team-level run estimates and simulates season outcomes using Monte Carlo methods.

 Objective

To estimate:

Expected wins over a 162-game season
Distribution of possible outcomes (best-case / worst-case scenarios)
Probabilities of key benchmarks (90+, 95+, 100+ wins)
Methodology
1. Data Collection
Source: MLB Statcast (Baseball Savant)
Metrics used:
Hitters: xwOBA, xSLG, Plate Appearances (PA)
Pitchers: xERA, Innings Pitched (IP)
Data aggregated across 2023–2025 seasons
2. Player Projections
Created weighted projections using multi-year data
Adjusted playing time:
Scaled total team PA (6200)
Scaled total team IP (1458)
Applied age-based adjustments:
Younger players → improvement factor
Older players → decline factor
3. Injury & Replacement Modeling
Modeled key injuries:
Reduced workload for injured players (e.g., Anthony Volpe, Gerrit Cole)
Reallocated lost PA/IP to replacement players
Applied replacement-level performance penalties:
Replacement pitchers assigned higher ERA
Captures real-world depth risk
4. Run Estimation
Runs Scored:
Converted xwOBA → wRAA → team runs
Runs Allowed:
Converted xERA → runs allowed
5. Win Projection (Pythagorean Expectation)
Win%=
RS
2
+RA
2
RS
2
	​


Where:

RS = Runs Scored
RA = Runs Allowed
6. Monte Carlo Simulation
Simulated 10,000 seasons
Introduced randomness:
±7% variation in runs scored
±8% variation in runs allowed

Generated:

Win distribution
Probabilities of key thresholds
Results

Base Projection:

Runs Scored: ~814
Runs Allowed: ~686
Expected Wins: ~94.6

Simulation Results:

Average Wins: 94.6
5th Percentile: ~81 wins
95th Percentile: ~108 wins

Probabilities:

90+ Wins: ~71%
95+ Wins: ~48%
100+ Wins: ~26%
Below .500: ~5.5%
Visualization

<img width="1034" height="912" alt="Screenshot 2026-04-24 155648" src="https://github.com/user-attachments/assets/261373a2-8063-45e0-b7f4-1610d5cdfe74" />

Comparison to Market

- Model Projection: 94.6 wins
- FanDuel Win Total: 93.5 wins

Interpretation:
- The model is closely aligned with the betting market
- The model is slightly more optimistic by about 1 win
- This suggests the projection is realistic and not overly aggressive
Tech Stack
Python
Pandas
NumPy
Matplotlib
Key Takeaways
The Yankees project as a strong playoff team with mid-90s win potential
There is meaningful upside (100+ wins) but also realistic downside risk
Incorporating injuries, aging, and replacement-level performance significantly improves model realism
🔧 Future Improvements
Simulate probabilistic injuries
Add strength of schedule adjustments
Model bullpen volatility
Compare with Fangraphs / PECOTA projections
  Author:

Brandon Anelli
Business Analytics | Python | Sports Analytics
