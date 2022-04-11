# WARP vs Salary - A Dive into Player Value and Team Spending in MLB
## Table of Contents
<details>
<summary>"Click to expand"</summary>
    
<img align="left" width="470" height="470" src="https://s22927.pcdn.co/wp-content/uploads/2020/01/world-series-trophy.jpg">
    
- [**How Did We Get Here?**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#how-did-we-get-here)
    - [*CBA Hooray?*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#cba-hooray)
    - [*WARP...What is it Good For?*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#warpwhat-is-it-good-for)
- [**Questions We Are Looking to Answer**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#questions-we-are-looking-to-answer)
- [**Our Null Hypothesis**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#our-null-hypothesis)
- [**Technology and Methodology**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#technology-and-methodology)
- [**Flow Chart**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#flow-chart)
- [**Data**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#data)
    - [*Data Sources*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#data-sources)
    - [*Data Caveats*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#data-caveats)
- [**Communication**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#communication)
- [**Machine Learning**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#machine-learning)
    - [*Preliminary Data Preprocessing*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.preliminary-data-preprocessing)
    - [*Preliminary Feature Engineering*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#preliminary-feature-engineering)
    - [*How is Data Split Between Training and Testing Groups*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#how-is-data-split-betweein-training-and-testing-groups)
    - [*Explanation of model choice*](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#explanation-of-model-choice)
- [**Sources**](https://github.com/damienfranco/MLB_WARP_vs_Salary/edit/main/README.md#sources)


</details>

## Which Predicts MLB Team Success Better? WARP vs Team Salary

Our initial question was whether we could predict Major League Baseball Team success (as defined by making the playoffs) by looking at their overall team salary. And as we dug through the data we started looking at a possible correlation between WARP scores and winning records.

## How Did We Get Here?

### CBA Hooray?
2022 highlighted to the average fan that there was a discrepancy between teams trying to win and those who were not. The main differentiator? Money. 

In November of 2021, Major League Baseball's Collective Bargaining Agreement (CBA) expired, requiring the MLB Players Assocation (MLBPA) to have to renegotiate the with the owners in the MLB on fair salaries and rules. Negotiations were extremely contentious as many items were at play. The main issues included
- The MLBPA felt that teams were manipulating when players were called to the majors in order to increase control. 
- The luxury tax threshold, which was installed to provide financial penalties to deter runaway spending from large market teams(there is not a salary cap in baseball) started to act as a cap, decreasing opportunities for players based on a imposed ceiling. 
- The MLBPA argued there should be a salary floor to try to increase the number of teams competing. 

Why were all of these things issues? Ever since the Billy Beane Moneyball A's, owners/General managers in baseball have realized that one may not need to spend to win baseball games. The following items were discovered:
- Pay for players has historically been given based on past performance. 
- Rookie players under the prior CBA were under team controll for *7 years* after the reached MLB. These players were held at league minimum salaries for the 7 years with the final 3 to 4 years allowing for arbitration raises still under market value.
- With the adjustment in analysis of when players could get paid, free agents past their prime saw drops in their ability to make "premium money" by the time they reached free agency.

Teams began to lose or "tank" in order to get as many top picks in the drafts for multiple seasons prior to trying to win to create low salaried, competive windows. Owners have challenged players on proof of this concept, while many others have admitted these tactics are how small market teams compete. Players challenge the market size concept as MLB teams have seen record profits. Major League Baseball has market size issues compared to other sports, as they do not have robust revenue sharing [^1]. While baseball is making about $9 Billion in revenue, all profits are tied to specific teams. There discrepancies in revenues for teams like the Chicago Cubs versus the Pittsburgh Pirates. These discrepancies have empowered owners to justifiy some of these tactics as necessary in order to compete, as they would claim their market size would limit their ability to compete on top free agents.

While not all of these issues were directly addressed, players and the league agreed to a new CBA in March of 2022 after the longest lockout in the history of the sport [^2]. MLB teams conceded on increasing the luxury tax thresholds while also adding incentives for teams to promote their top players sooner. Only time will tell if these are enough to move the needle on this contentious matter. 

### WARP...What is it Good For?

Wins Above Replacement Player, or **WARP** for short is a new age statistic to try to derive value of players. It was first seen in some version in Bill James' book *Baseball Abstracts* in the 1980s[^3].

![War Calc](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/Presentation_Resources/WAR-Formulas.png)

The above looks like a lot, doesnt it? So what does it mean? 
#### WARP MADE EASY

<img align="left" width="150" height="150" src="https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/Presentation_Resources/WAR%20Chart.webp">
**WARP** measures a players value in all aspects of the game in order to determine if how many "wins" that player is worth on the filed vs the average player: 

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
- MLB.com
- Baseball Prospectus
- ESPN.com

### Data Caveats
- We were unable to scrape data for the "Florida Marlins." The franchise was established as an expansion team in 1993. They rebranded to the Miami Marlins at the start of the 2012 season. They were both a playoff team and World Series winner in 1997 and 2003.
- Given the data we were able to access, our analysis is of player stats and payroll from 2000 to 2021. 
- There were 8 postseason teams from 2000-2011. In 2012, MLB expanded the Wild Card round to have the top two non-division winners to play each other in a 1 game playoff. This increases our playoff teams to 10 for data starting in 2012. 
- In 2020, MLB had a COVID shortened season of 60 games with expanded playoffs. 16 teams made the playoffs this year: 2 teams from each division in the American League and National League, then 2 additional Wild Card teams from each league. The first round format for the playoffs was a best of 3 series. The remainder of the playoff game formating remainded the same. 


![MLB Salary WARP database](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/images/Screen%20Shot%202022-03-23%20at%207.40.38%20PM.png)

## Communcation
The team is communicating through Slack and using Zoom and Google Meet for peer coding and live collaboration.

## Machine Learning

The team is using a pair or machine learning sections in order to determine if success is tied more closely to team payroll, WARP, or another statistic.  

### Preliminary Data Preprocessing
After the construction of our database, we had more than 60 hitting, pitching, and fielding statistics that we will use measuer the success of each athlete on each team in Major League Baseball over the past 20 years. We will total each statistic and group them by each of the 30 teams from the years 2000 - 2019.  We also need to create a success factor to determine how well a team performed over the year.  That success factor will be our Y Variable with the retotaled 

### Preliminary Feature Engineering
The first model we used was a principal component analysis which determined inter-relations between variables in the dataset. Specifically, it helped us create a subset of variables from our larger dataset which we could apply towards the next machine learning module.  Once we have our subset, we will apply that data intoa  Random Forest Identifier which will allow us to determine the level at which each x variable affects the Y Variable.

### How is Data Split Between Training and Testing Groups
We use sklearn to assign training and testing values to our X and Y variables, therefore, splitting them.

### Explanation of model choice
We believe that a random foreest identifier is appropriate for this project beacuse it produces better results, works well on large datasets, and can work with missing data by creating estimates for them. However, they can be limited by their inability to predict data outside of their current dataset. This is fine because we are not looking to predict future results.  We are only looking to determine which variables are most effective in determining our Y variables.

## Sources
[^1]: Revenues - https://www.wsn.com/nfl/nfl-vs-mlb/
[^2]: CBA Agreement Reached - https://www.cbssports.com/mlb/news/mlb-lockout-ends-as-mlbpa-owners-reach-cba-agreement-five-takeaways-with-baseball-set-to-return/live/
[^3]: WAR History - https://www.baseball-reference.com/bullpen/Wins_Above_Replacement#:~:text=Although%20Bill%20James%20hinted%20at,to%20measure%20a%20player's%20value
