# Premier League Match Predictor (C2)
A project made during the course Introduction to Data Science in the Univesity of Tartu, 2025.

### Authors:
Karl Markus Kiudma, Rene Dapon, Karl Joonas Jõepere

### Motivation & goal:
The **English Premier League (EPL)** is the top tier of English football and one of the most competitive and widely followed leagues worldwide. 
EPL match outcomes are highly unpredictable and heavily debated. Many existing predictions rely on intuition or biased opinions. 
Modern football data provides measurable performance indicators.

**Goal:** Build a machine learning model that predicts match outcomes  
(**Home Win**, **Draw**, **Away Win**) using match-level and team-level performance metrics.

### Guide to Contents:

**CSV_files/** <br>
Contains a subfolder for each season. Every season folder includes all data collected by the scrapers.

- **Team_Leaderboard.csv** – the Premier League table at the moment the leaderboard scraper was last run.  
- **squad_player_stats.csv** – team-level possession, shooting and attacking statistics.  
- **{season}_fixtures.csv** – full season fixture list with dates, home/away teams, expected goals and match results.  
- **{season}_squad_team_merged.csv** – merged table combining *Team_Leaderboard.csv* with *squad_player_stats.csv*.

Newly scraped data is always written into the corresponding season folder.

---

**scrapers/** <br>
Contains all notebooks that generate the CSV files.

- **LeaderboardScraper.ipynb** – creates or updates *Team_Leaderboard.csv*.  
- **matchinfo.ipynb** – creates or updates *{season}_fixtures.csv*.  
  - If run on a match day, fbref adds future empty rows at the bottom of the fixtures table; these must be manually removed in the season folder.  
- **squad&player_stats.ipynb** – produces *squad_player_stats.csv*.  
- **merger.ipynb** – merges *Team_Leaderboard.csv* and *squad_player_stats.csv* into *{season}_squad_team_merged.csv*.

---

**predictor/** <br>
Contains the prediction notebook.

- **predictor.ipynb** – used to generate predictions for upcoming matches.  
  At the bottom of the notebook, the user can select home and away teams and view the resulting predictions.

### Analaysis replication:
Step 1) 
