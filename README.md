# European-Football-Analytics-Team-Performance-Expected-Metrics-Evaluation
PL25\26 

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

* **Python (Pandas):** For initial data exploration, descriptive statistical assessment, and data verification.
* **HTML5 & Tailwind CSS:** For building a clean, modern, responsive user interface utilizing a dark-mode theme.
* **Chart.js (JavaScript):** For engineering custom, interactive, dynamic data visualizations including scatter plots with custom parity lines and coordinated cross-chart highlighting.
* **GitHub Pages:** For hosting and deploying the live, production-ready interactive data application.
---

# Methodology & Data Architecture

1. **Data Ingestion & Extraction:** Extracted team statistics from the early-season Premier League tracker (`team_season_stats.csv`), isolating actual production against advanced modeling variables.
2. **Feature Engineering (JavaScript Objects):** Normalized the raw multi-index values into structured JSON objects. Mathematically derived the efficiency differential metric directly within the application schema:
   $$\text{xG\_diff} = \text{Total\_Goals} - \text{Expected\_Goals (xG)}$$
3. **Coordinated Highlighting State Logic:** Programmed a central event listener connected to the DOM dropdown selector. When a user highlights a specific club, the system dynamically calculates state changes, dimming baseline points to `rgba(75, 85, 99, 0.1)` while accenting the target team across all three charts simultaneously using high-contrast vectors (`#f97316`).

   
---

# Dashboard & Visualizations

[***DASHBOARD***](https://jorymansour1.github.io/European-Football-Analytics-Team-Performance-Expected-Metrics-Evaluation/)


### Visualizations Implemented:
* **The Efficiency Quadrant (Scatter Plot):** Plots `Expected Goals` vs. `Actual Goals` paired with an explicit, dashed $y=x$ equilibrium line to expose team clinical variance at a glance.
* **Finishing Efficiency (Horizontal Bar Chart):** Displays the calculated `xG Difference` sorted sequentially to rank the league's most clinical and most wasteful squads.
* **Playstyle Matrix (Scatter Plot):** Correlates `Average Possession (%)` directly against `Progressive Passes` to evaluate structural space penetration efficiency.
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
