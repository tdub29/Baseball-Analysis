# Baseball-Analysis
Self-directed project attempting to develop predictive model for MLB games. Questions asked include, what statistics from the weeks prior to the game help us to predict game outcome? Or, what is the best sample size to pull from prior to a game for pitcher and batter data respectively?


One major roadblock which persisted throughout this project was the inability to loop through the bref_daily_batter/pitcher function. I believe there is a limit on the number of times the function can be used to scrape the data from baseball reference in a certain time frame allthough there is no mention of this on the developer page. As a result I was forced to manually run the string of code for each day of 3 seasons in order to amass the data desired.

Below are various graphs illustrating the relationship between different predictive metrics developed and actual score

![Rplotexscore](https://user-images.githubusercontent.com/108891102/213932899-a1339103-97ec-4635-b7af-a81d39bb05e8.png)

Exscore is a metric which includes the formula used for a multiple linear regression model with a high R-Squared

![Rplotexpected_score](https://user-images.githubusercontent.com/108891102/213932931-dfde9280-2dda-40ac-b138-0fb7d4ecac68.png)

Expected_score is the same as exscore, but includes the coefficients given by the regression model

![Rplot01r2](https://user-images.githubusercontent.com/108891102/213932941-8b14648a-cc75-4cc3-bc45-641dbc058f1a.png)

This is a plot of the formula used in the model itself rather than a calculated metric of it, R squared included

![Rplothistoricalpred](https://user-images.githubusercontent.com/108891102/213932946-bc003790-cfd2-41ad-bc4a-8bfdcf2f0a02.png)

This is a model of historical scores according to exscore. To create historical scores I searched for exscore values within 95% of that observation and returned the average actual scores those teams produced.



<img width="269" alt="Screenshot 2023-01-23 172706" src="https://user-images.githubusercontent.com/108891102/214164292-3fd4cfab-cc37-4d82-a224-25450d8409eb.png">
This image illustrates the effectiveness of the expected win percentage metric developed showing the actual win percentage of teams at certain expected win percentage thresholds

-

I am continuously working on this project so check back for updates and further analysis!
