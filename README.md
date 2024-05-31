# **Predicting NFL prospect contribution to team success (Project Overview)**
The National Football League (NFL) is one of the largest professional sports organizations in the United States; generating nearly $12 billion dollars in revenue in 2022 (NBC). Currently, there are 32 NFL teams and each year, the teams share the same goal-- winning the Super Bowl. 

A major part of acheiving this goal is having an excellent team-building process in which high quality players are brought in while navigating the NFL's salary cap. Teams can sign free agents from others teams, but they are often very expensive and make dealing with the salary cap difficult. Because of this, the annual NFL draft is highly anticipated as it allows  teams to select players eligible to leave college football in the hopes of adding talented, young individuals on team-friendly (cheap)contracts.

Owing to the complicated nature of playing football, evaluating players eligible for the draft (called prospects) is notoriously difficult. There are 22 players on the field for every play; each player typically assigned different tasks depending on their position. Teams use a combination of scouting reports, player measurements, and watching player tape to give themselves a better chance of selecting players that will do well in the NFL. 

Here, we attempt to predict a prospect's contribution to their respective team over several years based on their workout statistics at the annual NFL combine (simply a workout session for many prospects) and the value of the draft slot they are taken at.

 

## Proposed approach to modeling prospect contribution


## Data cleaning, processing, and exploratory data analysis

(Combine Dataset) After reading in the combine performance data, we noticed that some cleaning/ processing would be necessary. These included the following: 

- Removing duplicates
- Removing Undrafted Free Agents (We only focus on drafted players)
- Calculating percentage of missing data for informing interpolation
- NA %s as follows: 40 yd dash (1.1%), Vertical Jump (20.42%), Bench Press (29.77%), Broad Jump (21.18%), Cone Drill (33.14%), Shuttle Drill (32.3%)
- Removing very low count positions such as Kicker, Punter, and Long Snappers
- Lowering the amount of player positions (25 initially) to be more accurate and applicable to the entire dataset. This was accomplished by merging positions usually considered similar listed here:
  - Defensive Backs - SS, FS, S, DB as DB
  - Interior Offensive Line - C, G, OG, OL as IOL
  - Tight End/Fullback - TE, FB as TE/FB
  - Defensive Tackle - NT as DT
  - Interior LineBacker - LB as ILB
  - Defensive End - EDGE as DE
            
This narrows the data to 12 positions which is more accurate and makes for easier visualization when plotting variables. 

After cleaning the data, we used matplotlib to create box plots for each combine measurement/exercise grouped by position to visualize averages and outliers.


(Draft Picks Dataset) The primary alteration needed for this dataset was to retain the same Position group naming used in the combine data set, so the same Position changes listed above were used here. This dataset does not contain many quantitative variables, but we did uncover some interesting findings:

- The 3 most frequent position drafted in this dataset were Defensive Back (839), Wide Receiver (619), and Inside Linebacker (543). It is likely that the common lumping of both Safety positions and nickel cornerback into DBs led to this being the most frequent position

- 62% of first round picks selected in this dataset have been a Pro Bowler or All Pro at least once (a good proxy for success in the NFL, but limited number of selections can exclude other top performers)

- Only 12.5% of the entire dataset has been at least a one time Pro Bowler or All Pro; showing both the importance of first round picks having a high ratio and the difficulty to be a top performer in the NFL.






## Resulting model performance and implications of results


## Potential shortcomings and how to improve our approach

The performance of our approach to model player contribution based on draft pick selection and combine results was (Great? Terrible?)

Issues we came across include:

- Interpolating combine data when missing
- Inaccurate modeling due to inherent draft positional value
- Having more features to allow for more accurate predictions
- Innaccessible on-the-field based metrics which could provide new insights into actual player performance
- The difficulty associated with quantitatively assessing player performance as football is a complicated game.

Improvements for future research:

- Get more complete, higher detailed data
- Incorporate collegiate and professional on-field performance for predictive modeling
- Use a wide variety of modeling approaches to compare against each other. 
