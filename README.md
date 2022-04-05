# WARP vs Salaray - A Dive into Player Value and Team Spending in MLB

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
