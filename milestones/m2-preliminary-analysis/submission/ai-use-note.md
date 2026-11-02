# AI use note 

AI was used to merge the two datasets into our working dataset. AI also helped to make new variables (categorical age and PHQ-9 score) in the dataset. 
#AI prompt: Read the NHANES 2021-2023 DEMO_L.xpt and DPQ_L.xpt datasets, merge them into a csv dataset, and create a new variable dpq_score that is the sum of DPQ010 through DPQ090. Also create a categorical age variable age_cat with bands <18, 18-29, 30-39, 40-49, 50-59, 60-69, 70-79, and 80+.
#Verified: The merged dataset has 6,337 rows, and the dpq_score variable matches independent calculations of the PHQ-9 total score. The age_cat variable has the expected distribution of adults across the bands. All of this was compared with the NHANES data codebook.

## Part C: preliminary figure, Table 1, missingness updates, interpretation and claim boundary (Morgan) - draft for Jade to merge

### Audit trail

```
# AI prompt: R/dplyr. analysis_df has numeric INDFMPIR (0 to 5; 5 = "5 or higher") and numeric
#   dpq_score (PHQ-9 total, 0-27, no NAs). Write cut() bands [0,1) to [5,Inf) labelled
#   "Under 1" to "5 or higher" so every row gets a band.
# Verified: test values 0, 0.99, 1, 4.99 and 5 landed in the expected bands; no band was NA.

# AI prompt: Keep the worked example's group_by + summarise pattern for Table 1, but add an
#   "All adults" row above the income-band rows and a percent-of-sample column.
# Verified: the "All adults" N equals nrow(analysis_df); the band Ns add up to the same total
#   and match the figure's n labels; the "All adults" PHQ-9 mean (SD) matches mean() and sd().

# AI prompt: Add a label "n = <count>" above each point from column n, far enough above that
#   it clears the line, and add headroom at the top of the y axis.
# Verified: the n labels matched income_band_summary$n; the "5 or higher" mean matched a
#   direct calculation.

# Update to Humnah's missingness code (her original pair stays in the chunk)
# AI prompt: Add RIDAGEYR (numeric age in years) to key_vars with the label "Age", so every
#   Table 1 variable has a missingness row, and round missing_percent to one decimal.
# Verified: the Age row shows 0 missing (the age 18+ filter already drops any missing age);
#   sum(is.na(adult_cohort$RIDAGEYR)) is 0; the CSV percents have one decimal.

# AI prompt: Add a row to the cohort_counts table for the complete-case step, with
#   n = nrow(analysis_df), and print it with kable().
# Verified: the new last row's n equals nrow(analysis_df); the first two rows are unchanged.

# AI prompt: Count, across the nine raw PHQ-9 items, the total answers coded 7 (refused), the
#   total coded 9 (don't know), and the adults with at least one 7 or 9.
# Verified: DPQ010 alone gives 5 refused and 16 don't know, matching the CDC DPQ_L codebook.
```

### What AI helped with

Claude drafted the income-band code, the "All adults" row and percent column in Table 1, the n labels for the preliminary figure, the age row and rounding added to Humnah's missingness table, the complete-case row in the cohort table, and the count of refused and don't know answers. It also drafted first versions of the Interpretation and "What this analysis cannot claim." The Table 1 summary, grouped summary and plot follow the M2 worked example's code, adapted to our variables.

### What I changed

I compared the AI-recommended figure with the scatter plot from our M1 visual plan before keeping it, and the team agreed on the change. I declined the suggestion to pull interpretation numbers in with inline R and wrote them as plain text instead. After the PHQ-9 scoring rule changed, I rechecked each number against the new output; none of them changed.

### How I verified the result

1. Boundary values fell in the expected income bands.
2. No rows were lost: the band counts summed to the analytic sample.
3. The "5 or higher" mean matched a direct calculation, and the figure's n labels matched the Table 1 counts.
4. The refused and don't know counts for the first item matched the CDC codebook.
5. Each number in the Interpretation matched `income_band_summary` or Table 1.
6. The text says the results are descriptive and unweighted, and makes no causal or population claim.
