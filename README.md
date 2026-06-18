# European-Football-Analytics-Team-Performance-Expected-Metrics-Evaluation
PL25\26 
Here is the complete, formatted Markdown text for your `README.md` file. You can copy and paste this directly into your GitHub repository or portfolio platform.

---

# Project Overview

This project analyzes the early-season performance of English Premier League teams. By evaluating both actual output (Goals, Assists) and underlying advanced metrics (Expected Goals - xG, Possession, Progressive Play), this analysis identifies teams that are overperforming or underperforming relative to their statistical baseline. The resulting dashboard provides actionable insights for team management, scouting, and sports analysts.

# Business Problem

Football clubs, betting syndicates, and sports media need to evaluate team performance beyond basic win/loss records. Short-term variance and luck can heavily skew actual match results. The objective of this project is to leverage advanced statistical models (such as xG and xAG) to determine which teams are genuinely playing well and which are relying on unsustainable luck, thereby predicting future performance and informing strategic decisions.

---

# Dataset Description

* **Source:** `team_season_stats_2.csv` (Early-season snapshot of 20 Premier League teams).
* **Structure:** 20 rows, 35 columns (initially structured with a multi-level index).
* **Key Metrics Evaluated:**
* **Actual Output:** Total Goals, Total Assists.
* **Expected Quality:** Expected Goals (xG), Non-Penalty xG (npxG), Expected Assisted Goals (xAG).
* **Playstyle Indicators:** Ball Possession (%), Progressive Carries (PrgC), Progressive Passes (PrgP).
* **Efficiency KPI:** Goals vs. xG Differential.



---

# Tools Used

* **Python (Pandas):** For initial Data Exploration, MultiIndex header flattening, and data cleaning.
* **Microsoft Power BI:** For data modeling, DAX measure creation, and interactive data visualization.

---

# Methodology & Data Cleaning

Before visualization, the raw dataset required transformation to be ingested correctly by Power BI:

1. **Header Flattening:** Python was used to merge the 3-level MultiIndex headers into single descriptive strings (e.g., `('Expected', 'xG')` to `Expected_xG`).
2. **Feature Engineering:** Calculated key differentials to measure performance efficiency.
* `xG_Difference = Total_Goals - Expected_xG`


3. **Data Type Formatting:** Converted Possession to decimal percentages and ensured match metrics were typed as whole integers.

# Key DAX Measures

```dax
Total Goals = SUM(TeamStats[Total_Goals])
Total xG = SUM(TeamStats[Expected_xG])

xG Difference = [Total Goals] - [Total xG]

Avg Possession % = AVERAGE(TeamStats[Possession])

Overperformance Status = 
IF([xG Difference] > 0, "Overperforming", "Underperforming")

```

---

# Dashboard & Visualizations

[***DASHBOARD***](https://jorymansour.github.io/European-Football-Analytics-Team-Performance-Expected-Metrics-Evaluation/)


# Core Visuals Include:

* **The Efficiency Quadrant (Scatter Plot):** `Expected_xG` vs. `Total_Goals` with a 45-degree parity line to visually separate clinical/lucky teams from wasteful/unlucky ones.
* **Over/Under-Performance Bar Chart:** Highlighting `xG_Difference` sorted by magnitude.
* **Playstyle Matrix:** `Possession %` vs. `Progressive Passes` to evaluate if teams are effectively using the ball to advance up the pitch.

---

# Key Insights & Findings

1. **The Clinical Finishers:** Early data suggests teams like Arsenal are overperforming their expected metrics, scoring more actual goals than their xG dictates. This points to either exceptionally high-quality finishing or an impending regression to the mean.
2. **Possession vs. Penetration:** High ball possession does not universally equate to high offensive output (xG). Teams must pair possession with high `Progressive Passes` to generate quality scoring opportunities.
3. **Variance Targets:** Certain teams generate high `Expected_xG` but suffer from a negative `xG_Difference`. These teams are playing well systemically but suffering from poor finishing or bad luck, making them prime candidates for an upcoming positive turnaround.

---

# Recommendations

* **For Scouting & Betting:** Target teams with a negative xG difference but high overall xG. Their underlying metrics suggest their actual results will likely improve as variance normalizes.
* **For Tactical Adjustments:** Teams clustering in the "High Possession / Low Progressive Passes" quadrant need tactical shifts in training to focus on line-breaking, vertical passes rather than safe, lateral ball retention.

---

# Future Work

To expand upon this project, the next phases of analysis could include:

* **Playstyle Clustering:** Implementing a K-Means clustering algorithm in Python to group teams into specific tactical profiles (e.g., Counter-Attacking vs. High-Press).
* **Expected Points (xPts) Simulation:** Running Monte Carlo simulations based on match-by-match xG to build an "Expected League Table" to see who truly deserves to be in first place.
