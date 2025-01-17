# Baseball-Analysis
Self-directed project attempting to develop predictive model for MLB games.

As I look at this two years later I realize I hardly got to the predictive side of things and it was mainly an effort of data ingestion. Understand this is intended to reflect my passion and roots in baseball data!

Questions asked include, what statistics from the weeks prior to the game help us to predict game outcome? Or, what is the best sample size to pull from prior to a game for pitcher and batter data respectively?


One major roadblock which persisted throughout this project was the inability to loop through the bref_daily_batter/pitcher function. I believe there is a limit on the number of times the function can be used to scrape the data from baseball reference in a certain time frame allthough there is no mention of this on the developer page. As a result I was forced to manually run the string of code for each day of 3 seasons in order to amass the data desired.

Coming back to this 2 years later --- in my defense my analytics professor couldn't figure out the issue either! lol



Below is a simplified, nontechnical summary of what the script does:


**Collect Game Schedules**  ---- the part that took most of my time lol

The script starts by choosing a baseball season (for example, 2016) and uses a library to look up the official start and end dates of that regular season. It then goes through every date in that season to pull a list of games that happened on each day.


**Gather Daily Game Data**

For each day, the script fetches information about the matchups—like which teams played, what the game identifier was, and other game details. It combines all of this into one master table so there is a single record for each game of the season.


**Add Player Statistics**

Once the list of games is ready, the code brings in hitting and pitching stats for players on each team. It totals things like hits, runs, walks, or strikeouts and sums them up by team for each day, then joins these stats back to the game records.


**Calculate Advanced Metrics**

Using the hitting and pitching stats, the script calculates more advanced baseball statistics (e.g., weighted On-Base Average or “wOBA,” Fielding Independent Pitching or “FIP,” slugging percentage, etc.).


**Create Predictions**

Based on these stats, the code builds formulas to estimate how many runs a team might score (referred to as “expected score”). It also looks at the likelihood of winning for each team, using historical data to see how often teams with similar “expected score” or run-differences ended up winning.


**Refine the Predictions**

The script then adjusts or “regresses” these predictions back toward the overall league average in cases where the data sample is very small or looks unreliable. That helps avoid extremes when there’s not enough information.


**Compare and Analyze**

Finally, the script compares its predictions to actual outcomes—such as actual runs scored or who won—and logs how accurate these metrics and models are. It creates charts and calculates correlations to see how close the predictions match reality.


Overall, this code automates gathering baseball game data, links it with player stats, calculates performance metrics, and tries to predict how many runs teams will score and how likely they are to win, all while refining those predictions based on historical patterns.

