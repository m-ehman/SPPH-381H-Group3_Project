# Data

- `nhanes_merged.csv` is created from `raw/DEMO_L.xpt` and `raw/DPQ_L.xpt` by the setup chunk in `milestones/m2-preliminary-analysis/submission/preliminary-analysis.qmd`, joining on `SEQN`. It contains 6,337 rows, with exactly one row per participant `SEQN`. `dpq_score` prorates one or two missing DPQ010–DPQ090 items, while scores with three or more missing items or missing DPQ090 are NA.

- `age_cat` categorizes `RIDAGEYR` into `<18`, `18-29`, `30-39`, `40-49`, `50-59`, `60-69`, `70-79`, and `80+`. NHANES top-codes `RIDAGEYR` at 80, so `80` is categorized as `80+`; missing age remains missing.

- `dpq_score` is calculated from the nine PHQ-9 items `DPQ010`–`DPQ090`, as follows:
  - Valid item responses are 0–3. Responses coded as 7 (refused) or 9 (don't know) are treated as missing.
  - If all nine items are valid, their sum is the `dpq_score` (range 0–27).
  - If one or two items are missing, the score is prorated: the mean of the completed items is multiplied by nine.
  - If three or more items are missing, `dpq_score` is missing.
  - If `DPQ090` (thoughts of death or self-harm) is missing, `dpq_score` is also missing regardless of whether enough other items were answered.
  - The `dpq_score` was produced according to these project-specific PHQ-9 rules. The scoring guide we referred to is available at https://casrai.org/guides/phq-9. 