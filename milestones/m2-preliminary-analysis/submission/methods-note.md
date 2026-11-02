# Methods note

## Data and cohort
- We used two linked public-use NHANES files from August 2021 to August 2023: the depression screener (DPQ_L) and demographics (DEMO_L), joined by participant ID (`SEQN`). 
- The screener file includes only adults aged 18 and older who could read English or Spanish and did not need a proxy or interpreter, so all 6,337 linked records met our age criterion. 


## PHQ-9 total score
We followed a project-specific rule for missing items. The full rule is in `data/README.md`.

| Situation | How we handled it |
|---|---|
| Answer of 7 (refused) or 9 (don't know) | Treated as missing (53 adults gave at least one) |
| All nine items answered | Sum of the items (0 to 27) |
| One or two items missing | Prorated: mean of answered items × 9 |
| Three or more items missing | Total left missing |
| Item 9 (`DPQ090`) missing | Total left missing |

We prorated so that adults missing one or two items are not dropped. As a result, some totals are not whole numbers. We set this rule because the NHANES DPQ_L documentation does not say how to handle partly missing answers. We required item 9 because it asks about self-harm, and an average of the other items should not stand in for it.


## Analytic sample
- We reported missingness among all 6,337 adults before removing anyone.
- We then kept adults with both a family income-to-poverty ratio and a PHQ-9 total (n = 4,831). 
- Adults with missing values may differ from those we kept, so the pattern could change if they were included.


## Table 1 and figure
Table 1 reports N, percent of the sample, PHQ-9 mean (SD) and age mean (SD) for all adults and for each income band. 
For Table 1 and the figure, we grouped the income-to-poverty ratio into one-unit bands. The ratio is top-coded at 5, so the top band holds everyone at 5 or higher; age is likewise top-coded at 80. PHQ-9 scores are skewed, with an SD larger than the mean, but we report mean (SD) to match the figure and the Week 7 worked example. 

Our M1 visual plan proposed a scatter plot of individual adults. We instead plotted mean PHQ-9 by income band, because the scatter overlapped heavily and showed individual records, which our data intake card commits us to avoid. We report only aggregate results, and the self-harm item (`DPQ090`) appears only within the total score. 


## What the results can and cannot claim

The results describe the adults in this sample and how their PHQ-9 scores differ across income bands. They are descriptive and unweighted, so the analysis cannot show cause or estimate depressive symptoms for all U.S. adults.


## Software
We used R in the course Codespace with `haven`, `tidyverse` (including `dplyr`), `knitr` and `gt`. `gt` was added after the M1 reproducibility plan.

