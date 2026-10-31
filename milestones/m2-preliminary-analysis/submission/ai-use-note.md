# AI use note 

AI was used to help with making the PHQ-9 scoring variable based on the scoring rule that we researched. Checked the code components to make sure that scoring manual was followed. 

## Part C: preliminary figure, interpretation and claim boundary (Morgan) - draft for Jade to merge

### Audit trail

```
# AI prompt: R/dplyr. analysis_df has numeric INDFMPIR (0 to 5; 5 = "5 or higher") and numeric
#   dpq_score (PHQ-9 total, 0-27, no NAs). Write cut() bands [0,1) to [5,Inf) labelled
#   "Under 1" to "5 or higher" so every row gets a band.
# Verified: test values 0, 0.99, 1, 4.99 and 5 landed in the expected bands; band counts
#   summed to nrow(analysis_df).

# AI prompt: Add a label "n = <count>" above each point from column n, and add headroom at
#   the top of the y axis.
# Verified: the n labels matched income_band_summary$n; the "5 or higher" mean matched a
#   direct calculation.
```

### What AI helped with

Claude drafted the income-band code and the n labels for the preliminary figure, and first drafts of the Interpretation and "What this analysis cannot claim." The grouped summary and plot follow the M2 worked example's code, adapted to our variables.

### What I changed

I compared the AI-recommended figure with the scatter plot from our M1 visual plan before keeping it. I declined the suggestion to pull interpretation numbers in with inline R and wrote them as plain text instead, to be updated if the PHQ-9 scoring rule changes.

### How I verified the result

1. Boundary values fell in the expected income bands.
2. No rows were lost: the band counts summed to the analytic sample (4,797).
3. The "5 or higher" mean matched a direct calculation, and the figure's n labels matched the counts.
4. Each number in the Interpretation matched `income_band_summary` or Table 1.
5. The text says the results are descriptive and unweighted, and makes no causal or population claim.