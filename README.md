# Baseball-Analysis
Self-directed project attempting to develop predictive model for MLB games.

As I look at this two years later I realize I hardly got to the predictive side of things and it was mainly an effort of data ingestion.

Questions asked include, what statistics from the weeks prior to the game help us to predict game outcome? Or, what is the best sample size to pull from prior to a game for pitcher and batter data respectively?


One major roadblock which persisted throughout this project was the inability to loop through the bref_daily_batter/pitcher function. I believe there is a limit on the number of times the function can be used to scrape the data from baseball reference in a certain time frame allthough there is no mention of this on the developer page. As a result I was forced to manually run the string of code for each day of 3 seasons in order to amass the data desired.

Coming back to this 2 years later --- in my defense my analytics professor couldn't figure out the issue either! lol

