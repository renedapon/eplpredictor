# Premier League Match Predictor (C2)
A project made during the course Introduction to Data Science in the Univesity of Tartu, 2025.

### Authors:
Karl Markus Kiudma, Rene Dapon, Karl Joonas Jõepere
<br />
<br />
<br />

### Motivation & goal:
The **English Premier League (EPL)** is the top tier of English football and one of the most competitive and widely followed leagues worldwide. 
EPL match outcomes are highly unpredictable and heavily debated. Many existing predictions rely on intuition or biased opinions. 
Modern football data provides measurable performance indicators.
<br />

**Goal:** Build a machine learning model that predicts match outcomes  
(**Home Win**, **Draw**, **Away Win**) using match-level and team-level performance metrics.
<br />
<br />
<br />

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

---
**ResultsConclusion/** <br>
Contains notebooks for creating plots to illustrate our results.  
- **PredictionsOutcomeComparisonGW14.ipynb** - to assess how closely our model aligns with bookmaker expectations and to visualise it.
- **gw14_predictions_table.png** - the table created in *PredictionsOutcomeComparisonGW14.ipynb*.
- **ModelvsBet365ProbabilyComparisonGW14.ipynb** - to contrast our model’s predicted probabilities against the implied probabilities from Bet365 odds for all Gameweek 14 fixtures in 2025-2026 season.
- **model_vs_bet365.png** - the plot created in *ModelvsBet365ProbabilyComparisonGW14.ipynb*.
- **bet365odds.png** - shows the odds from Bet365 for gameweek 14 in 2025-2026 season.
<br />
<br />
<br />

### Analaysis replication:
**Steps**
1) Clone the project onto your device.
2) Run the following scrapers (in no particular order): 'LeaderboardScraper', 'matchinfo', 'squad&player_stats'.
3) Follow the instructions provided by each scraper (choosing which seasons to scrape etc).
4) Now run the scraper 'merger'. This merges the collected leaderboard data with the squad&player_stats scraper data since both datasets contain some matching data, which we want to merge into one.
5) Open 'predictor' and follow the instructions provided by that notebook. The predictor should display the chances of each team winning or drawing after inputing two teams as parameters.
* PS! Since the notebook doesn't scrape the newest data automatically, it is advised to run the scrapers after a period of time to have up to date matchdata. Keep in mind this project is created to use seasons from the period 2020-2026 so after the end of the 25/26 season, an updated version is required.

**Troubleshooting**
* Sometimes, when using scrapers on FBRef.com, it might display an error saying 'No matching table found.' or something along those lines. To solve this, try using CTRL+X on the whole cell and then copying it back in again. Sometimes commenting out some scraping code lies and scraping seasons individually can also work. <br/>
Since FBRef.com has recently started cracking down on scraping, it has become increasingly difficult and troublesome to scrape data from their website. In the future, it is possible that our scrapers will not function as intended and need updating by using some other type of scrape-blocking bypass.
* It might happen that after scraping something, the created .csv file is put into the root directory. To solve this, check after scraping if the desired dataset was put into the correct folder and if not, check the root directory and move it into the correct folder manually. To verify the correct file, refer to the creation timestamp of the file. This way you can check that the created file was created just now.
* Scraping match data when a Premier League match is about to start or is ongoing might cause problems for the scrapers. Since FBRef publishes the match on their website a couple hours before the game actually starts, the initial score values are NaN, which confuses the scraper and likely causes it to throw an error. The other outcome is that the scraper still works when a match with unfinished matchdata is on the website but the score in the fixtures table is just left blank. Verify the data after each scrape to not cause further errors in the process!

