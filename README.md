<p align="center">
  <img width="1100" height="400" src="https://i.redd.it/ctuaxotubqh31.jpg">
</p>

# WARP vs Salary - A Dive into Player Value and Team Spending in MLB

## Visualization

We created an interactive dashboard using Tableau where you can see MLB Team WARP and Salary side by side. Toggle between totals and seasonal stats to see how each team fared from 2000 to 2019.
[**Click Here For Our Visualization**](https://public.tableau.com/app/profile/damien.franco/viz/MLBWARPvsSalary/WARPSalaryTotals)

<p align="center">
  <img width="1024" height="576" src="https://img.mlbstatic.com/mlb-images/image/private/t_16x9/t_w1024/mlb/m33oxultuhrzukqctxaf">
</p>

## Table of Contents

<details>
<summary>"Click to expand"</summary>
    
<img align="right" width="480" height="480" src="https://s22927.pcdn.co/wp-content/uploads/2020/01/world-series-trophy.jpg">

  
- [**How Did We Get Here?**](#how-did-we-get-here)
    - [*CBA Hooray?*](#cba-hooray)
    - [*WARP...What is it Good For?*](#warpwhat-is-it-good-for)
- [**Questions We Are Looking to Answer**](#questions-we-are-looking-to-answer)
- [**Our Null Hypothesis**](#our-null-hypothesis)
- [**Technology and Methodology**](#technology-and-methodology)
- [**Flow Chart**](#flow-chart)
- [**Data**](#data)
    - [*Data Sources*](#data-sources)
    - [*ETL*](#etl)
    - [*Data Caveats*](#data-caveats)
- [**Communication**](#communication)
- [**Machine Learning**](#machine-learning)
    - [*Data Preprocessing*](#data-preprocessing)
    - [*Feature Engineering*](#feature-engineering)
    - [*How is Data Split Between Training and Testing Groups*](#how-is-data-split-between-training-and-testing-groups)
    - [*Machine Learning Results*](#machine-learning-results)
- [Visualization](#visualization)
- [**Sources**](#sources)

</details>

## Which Predicts MLB Team Success Better? WARP vs Team Salary

Our initial question was whether we could predict Major League Baseball Team success (as defined by making the playoffs) by looking at their overall team salary. As we dug through the data, we started looking at a possible correlation between WARP scores and winning records.

## How Did We Get Here?

### CBA Hooray?
2022 highlighted to the average fan that there was a discrepancy between teams trying to win and those who were not. The main differentiator? Money.
<img align="right" width="180" height="170" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/Presentation_Resources/CBA_Negotiations.jpeg">
 
In November of 2021, Major League Baseball's Collective Bargaining Agreement (CBA) expired, requiring the MLB Players Association (MLBPA) to have to renegotiate the with the owners in the MLB on fair salaries and rules. Negotiations were extremely contentious as many items were at play.[^1] The main issues included:
- The MLBPA felt that teams were manipulating when players were called to the majors in order to increase the number of years of control. 
- The luxury tax threshold, which was installed to provide financial penalties to deter runaway spending from large market teams (there is not a salary cap in baseball) started to act as a cap, decreasing opportunities for players based on a imposed ceiling. 
- The MLBPA argued there should be a salary floor to try to increase the number of teams competing.

Why were all these thing’s issues? Ever since the Billy Beane Moneyball A's, owners/General managers in baseball have realized that one may not need to spend to win baseball games. The following items were discovered:
- Pay for players has historically been given based on past performance. 
- Rookie players under the prior CBA were under team control for *7 years* after the reached MLB. These players were held at league minimum salaries for the 7 years with the final 3 to 4 years allowing for arbitration raises still under market value.
- With the adjustment in analysis of when players could get paid, free agents past their prime saw drops in their ability to make "premium money" by the time they reached free agency.

Teams began to lose or "tank" in order to get as many top picks in the draft for multiple seasons prior to trying to win to create low salaried, competitive windows. Owners have challenged players on proof of this concept, while many others have admitted these tactics are how small market teams compete. Players challenge the market size concept as MLB teams have seen record profits. Major League Baseball has market size issues compared to other sports, as they do not have robust revenue sharing [^2]. While baseball is making about $9 Billion in revenue, all profits are tied to specific teams. There are discrepancies in revenues for teams like the Chicago Cubs versus the Pittsburgh Pirates. These discrepancies have empowered owners to justify some of these tactics as necessary to compete, as they would claim their market size would limit their ability to compete on top free agents.

<p align="center">
  <img width="470" height="202" src="https://www.gannett-cdn.com/presto/2022/03/11/USAT/5541044b-8fde-47bf-82cd-5101a9c8800a-AP_Baseball_Lockout.jpg?crop=4795,2021,x0,y374">
</p>

While not all these issues were directly addressed, players and the league agreed to a new CBA in March of 2022 after the longest lockout in the history of the sport [^3]. MLB teams conceded on increasing the luxury tax thresholds while also adding incentives for teams to promote their top players sooner. Only time will tell if these are enough to move the needle on this contentious matter.

### WARP...What is it Good For?

Wins Above Replacement Player, or **WARP** for short is a new age statistic to try to derive value of players. It was first seen in some version in Bill James' book *Baseball Abstracts* in the 1980s[^4].

![War Calc](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/Presentation_Resources/WAR-Formulas.png)

The above looks like a lot, doesnt it? So what does it mean? 
#### WARP MADE EASY

<img align="left" width="150" height="150" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/Presentation_Resources/WAR%20Chart.webp">
**WARP** measures a players value in all aspects of the game in order to determine how many "wins" that player is worth on the field vs the average player: 

- Negative WARP means a player is costing you wins
- 0 WARP means the player is average
- Any other WARP score means the player is above average and helping your baseball team succeed.

## Questions We are looking to Answer?
- Does increasing payroll lead to success?
- Is WARP more effective when it comes to building a championship team?
- Are there other variables that may affect the success of a team?

## Our Null Hypothesis: 
Neither WARP scores nor team salary are reliable predictors of an MLB team making the playoffs.

## Technology and Methodology
- Python
- AWS
- Tableau
- Lucid Chart
- Google Slides (for presentation)

## Flow Chart

Below is our current flowchart for scoping out the work

![MLB WARP Salary Flowchart](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/Screen%20Shot%202022-03-23%20at%205.02.26%20PM.png)

## Data

Our data needs included the following:
- Player WARP Data
- Team Payroll
- Team Records
- Playoff Appearances
- World Series Champions List

### Data Sources
- MLB Stats API
- Baseball Prospectus

### ETL
The only free option for detailed MLB salary data that we found was on [Baseball Prospectus](https://legacy.baseballprospectus.com/compensation/), which was extracted using a webscraper built with BeautifulSoup. The player stats were not easily accessed using a webscraper, so the stats were extracted using the [MLB Stats API](https://statsapi.mlb.com). The stats had to be requested in three different groups, hitting, fielding, and pitching, because of how the endpoint was structured. The stats datasets were joined and cleaned to match the format of the salary dataset using regex replacements.

The stats and salary datasets came from two completely sources, using separate processes for collection, and did not contain a common primary key that they could be joined on. The stats dataset contained a unique `player_id` (ETL Figure 1), that was absent in the salary data (ETL Figure 2). The tables were inner joined by player name, team name, and year. Extra records were produced, either created by the lack of a primary key to join on, or by differences in how the two sources organized their data (ETL Figure 3). Simply using the `.drop_duplicates()` function from the Pandas library would not work because of the non-duplicated stats. The columns in the final dataset were grouped by the strings, and the `.agg()` function was applied to in order to keep the player salary data constant, but sum/average their stats (ETL Figure 4). This eliminated the duplicated player entries, while keeping their stats accurate.

**ETL Figure 1: Stats dataset**
<p align="center">
  <img width="673" height="159" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/stats_csv.png">
</p>

**ETL Figure 2: Salary dataset**

<p align="center">
  <img width="702" height="161" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/player_salaries.png">
</p>

**ETL Figure 3:**

<p align="center">
  <img width="1090" height="211" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/readme_duplicates.png">
</p>

Extra rows created containing duplicated salary data but having unique stats. In `season` 2016, Josh Fields appears twice, and has the same salary information but different pitching stats.

**ETL Figure 4:** 

<p align="center">
  <img width="783" height="122" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/cleaning_duplicates.png">
</p>

The `groupby()` function grouped the final joined table by their names, ids, teams, positions, and season. The `.agg()` function took a dictionary defining each column as the key, and whether to keep the first (or last) record or sum/average the records together as the value.


### Data Caveats
- We were unable to scrape data for the "Florida Marlins." The franchise was established as an expansion team in 1993. They rebranded to the Miami Marlins at the start of the 2012 season. They were both a playoff team and World Series winner in 1997 and 2003. WARP and Salary information was added via a CSV from Baseball Reference. 
- Given the data we were able to access, our analysis is of player stats and payroll from 2000 to 2019. 2020 was omitted due to the nature of the shortened season. Not all finalized data for 2021 was available for scraping. 
- There were 8 postseason teams from 2000-2011. In 2012, MLB expanded the Wild Card round to have the top two non-division winners to play each other in a 1 game playoff. This increases our playoff teams to 10 for data starting in 2012. 
- In 2020, MLB had a COVID shortened season of 60 games with expanded playoffs. 16 teams made the playoffs this year: 2 teams from each division in the American League and National League, then 2 additional Wild Card teams from each league. The first-round format for the playoffs was a best of 3 series. The remainder of the playoff game formatting remained the same. 


![MLB Salary WARP database](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/Screen%20Shot%202022-03-23%20at%207.40.38%20PM.png)

## Communication

The team is communicating through Slack and using Zoom and Google Meet for peer coding and live collaboration.

## Machine Learning

The team is using a pair or machine learning sections to determine if success is tied more closely to team payroll, WARP, or another statistic.

### Data Preprocessing

After the construction of our database, we had more than 30 hitting, pitching, and fielding statistics that we will use measure the success of each athlete on each team in Major League Baseball over the past 20 years. We will total each statistic and group them by each of the 30 teams from the years 2000 - 2019*. We will utilize wins and playoff appearances as our Y variable to determine the success of the team.

*See [**Data Caveats**](#data-caveats)*

### Feature Engineering

The first model we used was a principal component analysis which determined inter-relations between variables in the dataset. Specifically, it helped us create a subset of variables from our larger dataset which we could apply towards the next machine learning module. Once we have our subset, we will apply that data into a Random Forest Classifier which will allow us to determine the level at which each X Variable affects the Y Variable.
We believe that a random forest identifier is appropriate for this project because it produces better results, works well on large datasets, and can work with missing data by creating estimates for them. However, they can be limited by their inability to predict data outside of their current dataset. This is fine because we are not looking to predict future results. We are only looking to determine which variables are most effective in determining our Y variables.


### How is Data Split Between Training and Testing Groups

The train-test split is used to evaluate the performance of a machine learning algorithm, and it is typically used for classification or regression problems
Testing and training splits the data into two subsets.  The first is used to fit the model, and it is referred to as training. The second portion is applied to the machine learning model and used to make predictions and compared to the expected value.
We use sklearn to assign training and testing values to our X and Y variables, therefore, splitting them.  The test size will contain 25% of the values while the train size will contain 75%

![](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/data_training.png)

### Machine Learning Results

Through our PCA, we were able to determine that Team Payroll, WARP, and Runs had the largest overall effect on making the playoffs.
In these box plots, the difference in the medians with these variables is much greater than any other variable in our data set.  From the PCA, we determined that WARP, Salary, and Runs most greatly affected a team's playoff chances.

![](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/PCA_Payroll.png)

![](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/PCA_WARP.png)

![](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/PCA_runs.png)

![](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/explained_variance.png)

Using these variables, we tested to see if WARP and Runs were more effective than Team Payroll when it came to determining the success of the team.  We were able to confirm that WARP is the factor that most closely determines wins and playoff appearances.  

![warp runs](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/Warp_Runs.png)

![features rank](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/features_rank.png)

One step further, we also determine runs were a more effective variable than team_salary when it came to determining the success of a team.

![runsrank](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/runs_features_rank.png) 

*See [Data Caveats](#data-caveats)*


## Sources
[^1]: CBA Negotiations - https://www.bostonglobe.com/2021/11/03/sports/how-will-cba-negotiations-affect-baseballs-offseason/
[^2]: Revenues - https://www.wsn.com/nfl/nfl-vs-mlb/
[^3]: CBA Agreement Reached - https://www.cbssports.com/mlb/news/mlb-lockout-ends-as-mlbpa-owners-reach-cba-agreement-five-takeaways-with-baseball-set-to-return/live/
[^4]: WAR History - https://www.baseball-reference.com/bullpen/Wins_Above_Replacement#:~:text=Although%20Bill%20James%20hinted%20at,to%20measure%20a%20player's%20value
