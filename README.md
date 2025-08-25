

## SEC Baseball Transfer Study
### Intro
In collegiate athletics it is often difficult to compare stats. The variance in strength of opponents is wide and it is often hard to properly evaluate surface level stats of athletes in separate conferences. However, recent rule changes has made it much less restrictive to transfer to a new college. This has given us lots of new data to analyze. By comparing the results of incoming transfers with returning players of a particular conference, we can evaluate how much water stats from another conference hold within a new one. For this study, I am limiting the scope to transfer baseball players coming into the SEC, and I am only focusing on hitting stats. **The goal is to find how much correlation there is between a transfer's stats from their previous year to their next, and how much growth or decline should we expect from transfers.**
### Method
The ability for student athletes to transfer to a new college without having to sit out a year started in the spring of 2021 and so shall be where our study with start from. I gathered data for every baseball player in the SEC from 2021 to 2025. The SEC was the conference chosen for this study due its near unanimous consensus of being the best conference in college baseball. Each data point will have the player, the previous year's stats, next year's stats, and whether or not that season is a transfer season for each season of that player's college career. Note I am only taking into account seasons of SEC players returning and incoming transfers. Outgoing transfers leaving the SEC will not be counted.

We will take a look at 5 hitting statistics for this study:

 - **BB% (Walk Percentage)** - The percentage of plate appearances (PAs) that result in a walk
 - **K% (Strikeout Percentage)** - The percentage of PAs that result in a strikeout. Note this the only of the 5 statistics that batters want to be low.
 - **OBP (On-Base Percentage)** - The percentage of PAs that result in a hit, walk, or hit-by-pitch (HBP)
 - **SLG (Slugging)** - The total number of bases a player records per at-bat (AB).
 - **OPS (On-Base Plus Slugging)** - The addition of the OBP and SLG stats. While not intuitive, it provides a good rough value of a hitter's contributions.

You may wonder why some traditional stats like batting average and RBIs weren't chosen for the study. Those stats don't translate as well year over year as the stats above, which is important to isolate the change the new conference caused.

We will look at the distribution for the change in all 5 of these stats from both transfers and returning players. We will also try to make a predictive, singular regression model for both class of players. Both models will be scored using R² to see the strength of correlation and MAE to get a range that our model can approximate 

### BB%
![BB% Distribution](/graphs/bb_distribution.png)
![BB% Regression](/graphs/bb_regression.png)

**Returners**
**R^2- .031**
**MAE- 2.42 percentage points**

**Transfers**
**R^2- -.124**
**MAE- 2.68 percentage points**

Looking at walk percentage first, we can see that returning SEC players and incoming transfers perform remarkably similar. Both on average gain +1 percentage point to their walk rate. The regression models both have similar slopes were scored equally weakly
The returning players do have a larger concentration of players around the mean of the distribution chart. However, that is probably explained by the much larger sample size
Overall, the big take away for BB% is that you can evaluate it for transfers the same you would for returning players

### K%
![K% Distribution](/graphs/k_distribution.png)
![K% Regression](/graphs/k_regression.png)

**Returners**
**R^2- .214**
**MAE- 3.93 percentage points**

**Transfers**
**R^2- .496**
**MAE- 2.58 percentage points**

Strikeouts, to me, paint the most interesting picture. Returning players more often than not lower their K% (remember lower is better for K%) and transfer raise their K% more often than not. It is probably the stat in here that we can say is most concretely effected by the transition from an outside conference to the SEC. According to the R² of the model, it accounts for ~50% of the change year to year.
But, quite interestingly, there is a lot less of a correlation with returning players. According to the available data, it seems K% is a make or break stat for these youthful players during their developmental years before the pros. There are lots of players who significantly decrease their K% and some who do the opposite. Under a controlled environment, the variance of skill in college is shown and the great players truly isolate themselves.

### OBP
![obp Distribution](/graphs/obp_distribution.png)
![obp Regression](/graphs/obp_regression.png)
  
**Returners**  
**R^2- .019**  
**MAE- .029**

**Transfers**  
**R^2- .013**  
**MAE- .024**

Looking at on-base percentage, both returners and transfers show similarly weak predictability. Neither regression has any meaningful forward signal, and the R² values hover close to zero. Returners do carry a small edge in performance, averaging +.017 increase in OBP, but overall the distributions look very in shape.  
The takeaway is that OBP isn’t a reliable projection tool in this dataset. Whether a player is returning or transferring, year-to-year OBP carries very little stability and only shows slight favoritism towards returning players.

### SLG
![slg Distribution](/graphs/slg_distribution.png)
![slg Regression](/graphs/slg_regression.png)

**Returners**  
**R^2- .490**  
**MAE- .005**

**Transfers**  
**R^2- .171**  
**MAE- .070**

Slugging percentage, unlike OBP, shows a clear separation between the two groups. Returning players hold a much stronger correlation year-over-year, with an R² over .3, reflecting the stickiness of power once established in the SEC.  
Transfers, however, display far more scatter. Their slugging values are spread widely in the distribution, producing both big risers and major drop-offs. This variance drags down the regression fit and increases error.  
Overall, SLG is much more stable for returners than transfers. Power skills travel less consistently when players switch conferences.

### OPS
![ops Distribution](/graphs/ops_distribution.png)
![ops Regression](/graphs/ops_regression.png)

**Returners**  
**R^2- .211**  
**MAE- .054**

**Transfers**  
**R^2- .119**  
**MAE- .067**

OPS naturally sits between OBP and SLG since it is the sum of the two. Returning players show a moderate year-to-year relationship, stronger than OBP alone but weaker than SLG. Transfers again lag behind, with a weaker fit and higher error.  

### Conclusion 
BB% and K% are your most key metrics for evaluating incoming transfers into the SEC. BB% stays consistent regardless of conference, and on the other end of spectrum K% is significantly increased by the new pitching environment. OBP can't really be evaluated well, and slug is too varied for transfers to make any informed preseason prediction for transfers.

