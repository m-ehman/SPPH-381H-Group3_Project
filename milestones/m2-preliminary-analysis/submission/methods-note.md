# Methods note

*Draft started by Morgan (part C) on 31 October for Jade to review and finalize.*

We used two linked public-use NHANES files from August 2021 to August 2023: the depression screener (DPQ_L) and demographics (DEMO_L), joined by participant ID (`SEQN`). The screener file includes only adults aged 18 and older who could read English or Spanish and did not need a proxy or interpreter, so all 6,337 linked records met our age criterion. We set PHQ-9 answers of 7 (refused) and 9 (don't know) to missing, and calculated the PHQ-9 total (0 to 27) only when all nine items were answered, as the NHANES codebook describes. After reporting missingness, we kept adults with both a family income-to-poverty ratio and a PHQ-9 total (n = 4,797). Adults with missing values may differ from those we kept, so the pattern could change if they were included.

For the summaries, we grouped the income-to-poverty ratio into one-unit bands. The ratio is top-coded at 5, so the top band holds everyone at 5 or higher. PHQ-9 scores are skewed, with an SD larger than the mean, but we report mean (SD) to match the figure and the Week 7 worked example. Our M1 visual plan proposed a scatter plot of individual adults. We instead plotted mean PHQ-9 by income band, because the scatter overlapped heavily and showed individual records, which our data intake card commits us to avoid. We report only aggregate results, and the self-harm item (`DPQ090`) appears only within the total score. The results are descriptive and unweighted, so they cannot show cause or estimate depressive symptoms for all U.S. adults.

---

**To confirm before submitting (delete this list and the draft line above):**

- PHQ-9 scoring rule: if the team switches to prorating, update the scoring sentence and the n of 4,797.
- Table 1 format: if Table 1 is rebuilt by income band, check that the summaries paragraph still matches it.
- Figure: confirm the team agrees with the change from the M1 scatter plot. .. if we do, we may want to add a small dated note to the M1 initial-visual-plan.md flagging this change? 
- Attribution: if M2 builds on anyone's A6 `eda-note.qmd`, add one sentence saying so (M2 readme asks for this).
