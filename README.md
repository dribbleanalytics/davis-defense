# METHODOLOGY: Introducing DAVIS: a holistic and transparent defensive metric

[Link to blog post.](https://dribbleanalytics.blog/2019/11/davis-defense)

## Data collection

All data was collected from [Basketball-Reference](http://basketball-reference.com/) and [NBA.com/Stats](https://stats.nba.com/). 

In the Excel file, each sheet is named by the source of the data. Specifically, advanced stats (DBPM, DWS, etc.) are from Basketball-Reference, while most other stats (DFGA, DRTG, STL, etc.) are from NBA.com/Stats. ESPN RPM data is from ESPN.

We limited the data set to players who played at least 41 games and 10 MPG.

## DAVIS creation

DAVIS stands for defensive average value below ideal stats. We used the following stats for DAVIS:

- STL
- BLK
- STL%
- BLK%
- DFGA
- DWS
- DBPM
- DRTG

We normalized each stat between 0 and 1 to avoid stats having different weights on DAVIS (i.e. DRTG has a higher range than STL, so without normalization, we would naturally weight it more).

After normalizing, we took the distance between each player's stats and the best possible stats for each category. We used three distance metrics:

1. Euclidean distance
2. Manhattan distance
3. Wasserstein distance

The closer a player is to the best possible stats, the better he is as a defender. However, being closer to the best possible stats means the player's distance is lower. So, after calculating this distance, we inverted it such that higher is better (and the best possible DAVIS would be 1). Then, we averaged the distance achieved from these 3 metrics.

