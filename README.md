# WARP vs Salary - A Dive into Player Value and Team Spending in MLB

## Which Predicts MLB Team Success Better? WARP vs Team Salary

Our initial question was whether we could predict Major League Baseball Team success (as defined by making the playoffs) by looking at their overall team salary. And as we dug through the data we started looking at a possible correlation between WARP scores and winning records.

## How Did We Get Here?
2022 highlighted to the average fan that there was a discrepancy between teams trying to win and those who were not. The main differentiator? Money. 

In November of 2021, Major League Baseball's Collective Bargaining Agreement (CBA) expired, requiring the MLB Players Assocation (MLBPA) to have to renegotiate the with the owners in the MLB on fair salaries and rules. 

Every since the Billy Beane Moneyball A's, owners/General managers in baseball have realized that one may not need to spend to win baseball games. The following items were discovered:
- Pay for players has historically been given based on past performance. 
- Rookie players under the prior CBA were under team controll for *7 years* after the reached MLB. These players were held at league minimum salaries for the 7 years with the final 3 to 4 years allowing for arbitration raises still under market value
- With the adjustment in analysis of when players could get paid, free agents past their prime saw drops in their ability to make "premium money" by the time they reached free agency

Teams began to lose or "tank" in order to get as many top picks in the drafts for multiple seasons prior to trying to win to create low salaried, competive windows. 

### WAR...What is it Good For?

![War Calc](https://github.com/damienfranco/MLB_WARP_vs_Salary/blob/main/Presentation_Resources/WAR-Formulas.png)


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
