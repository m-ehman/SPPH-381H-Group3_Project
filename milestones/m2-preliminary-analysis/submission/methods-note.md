# Methods note

*Draft started by Morgan (part C) on 31 October and updated on 1 November for Jade to review and finalize.*

We used two linked public-use NHANES files from August 2021 to August 2023: the depression screener (DPQ_L) and demographics (DEMO_L), joined by participant ID (`SEQN`). The screener file includes only adults aged 18 and older who could read English or Spanish and did not need a proxy or interpreter, so all 6,337 linked records met our age criterion. We set PHQ-9 answers of 7 (refused) and 9 (don't know) to missing; across the nine items there were 23 refused and 51 don't know answers, from 53 adults. Following a common convention, we prorated the PHQ-9 total when one or two items were missing (the mean of the answered items multiplied by nine), so some totals are not whole numbers. As a project-specific rule, the total was set to missing when three or more items, or the self-harm item (`DPQ090`), were missing; the full rule is in `data/README.md`. We reported missingness for the income ratio, PHQ-9 total and age, then kept adults with both an income ratio and a PHQ-9 total (n = 4,831). Adults with missing values may differ from those we kept, so the pattern could change if they were included.

For Table 1 and the figure, we grouped the income-to-poverty ratio into one-unit bands. The ratio is top-coded at 5, so the top band holds everyone at 5 or higher; age is likewise top-coded at 80. PHQ-9 scores are skewed, with an SD larger than the mean, but we report mean (SD) to match the figure. Our M1 visual plan proposed a scatter plot of individual adults. We instead plotted mean PHQ-9 by income band, because the scatter overlapped heavily and showed individual records, which our data intake card commits us to avoid. We report only aggregate results, and the self-harm item appears only within the total score. The results are descriptive and unweighted, so they cannot show cause or estimate depressive symptoms for all U.S. adults. The analysis runs in R with the tidyverse, haven, knitr and gt packages.

---

**To confirm before submitting (delete this list and the draft line above):**

- Attribution: if M2 builds on anyone's A6 `eda-note.qmd`, add one sentence saying so (the M2 brief asks for this).
- M1 note: decide whether to add a short dated note to the M1 `initial-visual-plan.md` about the figure change.
