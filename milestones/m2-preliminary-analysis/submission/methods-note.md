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

We prorated so that adults missing one or two items are not dropped. As a result, some totals are not whole numbers.


## Analytic sample
- We reported missingness among all 6,337 adults before removing anyone.
- We then kept adults with both a family income-to-poverty ratio and a PHQ-9 total (n = 4,831). 
- Adults with missing values may differ from those we kept, so the pattern could change if they were included.


## Table 1 and figure
Table 1 reports N, percent of the sample, PHQ-9 mean (SD) and age mean (SD) for all adults and for each income band. 
For Table 1 and the figure, we grouped the income-to-poverty ratio into one-unit bands. The ratio is top-coded at 5, so the top band holds everyone at 5 or higher; age is likewise top-coded at 80. PHQ-9 scores are skewed, with an SD larger than the mean, but we report mean (SD) to match the figure and the Week 7 worked example. 

Our M1 visual plan proposed a scatter plot of individual adults. We instead plotted mean PHQ-9 by income band, because the scatter overlapped heavily and showed individual records, which our data intake card commits us to avoid. We report only aggregate results, and the self-harm item (`DPQ090`) appears only within the total score. The results are descriptive and unweighted, so they cannot show cause or estimate depressive symptoms for all U.S. adults.


## Software
We used R in the course Codespace with `haven`, `tidyverse` (including `dplyr`), `knitr` and `gt`. `gt` was added after the M1 reproducibility plan.

---

**To confirm before submitting (delete this list and the draft line above):**

- [x] PHQ-9 scoring rule: if the team switches to prorating, update the scoring sentence and the n of 4,797.
- [x] Table 1 format: if Table 1 is rebuilt by income band, check that the summaries paragraph still matches it.
- [x] Figure: confirm the team agrees with the change from the M1 scatter plot. .. if we do, we may want to add a small dated note to the M1 initial-visual-plan.md flagging this change? 
- [ ] Attribution: if M2 builds on anyone's A6 `eda-note.qmd`, add one sentence saying so (M2 readme asks for this).

- Numbers to confirm after render:
- [x] [4,831] analytic sample: check nrow(analysis_df) in the new html (old html shows 4,797)
- [x] [53] adults with a 7 or 9 answer: not computed in the qmd yet. Add a code chunk
- [x] [gt] package list: check library() lines in the final qmd after Morgan's Table 1

