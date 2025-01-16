# Baseball-Analysis
Self-directed project attempting to develop predictive model for MLB games.

As I look at this two years later I realize I hardly got to the predictive side of things and it was mainly an effort of data ingestion.

Questions asked include, what statistics from the weeks prior to the game help us to predict game outcome? Or, what is the best sample size to pull from prior to a game for pitcher and batter data respectively?


One major roadblock which persisted throughout this project was the inability to loop through the bref_daily_batter/pitcher function. I believe there is a limit on the number of times the function can be used to scrape the data from baseball reference in a certain time frame allthough there is no mention of this on the developer page. As a result I was forced to manually run the string of code for each day of 3 seasons in order to amass the data desired.



<img width="269" alt="Screenshot 2023-01-23 172706" src="https://user-images.githubusercontent.com/108891102/214164292-3fd4cfab-cc37-4d82-a224-25450d8409eb.png">
This image illustrates the effectiveness of the expected win percentage metric developed showing the actual win percentage of teams at certain expected win percentage thresholds

-

I am continuously working on this project so check back for updates and further analysis!
