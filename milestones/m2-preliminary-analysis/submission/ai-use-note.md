# AI use note 
<br>

## Data setup and PHQ-9 scoring (Yoon)

### Audit trail
```
# AI prompt: Read the NHANES 2021-2023 DEMO_L.xpt and DPQ_L.xpt datasets, merge them into a csv dataset, and create a new variable dpq_score that is the sum of DPQ010 through DPQ090. Also create a categorical age variable age_cat with bands <18, 18-29, 30-39, 40-49, 50-59, 60-69, 70-79, and 80+.

# Verified: The merged dataset has 6,337 rows, and the dpq_score variable matches independent calculations of the PHQ-9 total score. The age_cat variable has the expected distribution of adults across the bands. All of this was compared with the NHANES data codebook.
```

### What AI helped with

AI was used to merge the two datasets into our working dataset. AI also helped to make new variables (categorical age and PHQ-9 score) in the dataset. 

<br>

## Missingness and first Table 1 (Humnah)

### Audit trail
```r
# AI prompt: Help draft code to summarize missingness for INDFMPIR and dpq_score before
#   complete-case filtering and export the result as a CSV.

# Verified: Missing counts were independently checked using is.na() on the adult cohort.

# AI prompt: Help create and export a simple Table 1-style descriptive summary of the
#   analytic sample.

# Verified: Analytic N and mean (SD) values for age, INDFMPIR, and PHQ-9 matched
#   independent calculations.
```

### What AI helped with

AI helped draft the code to summarize missingness for `INDFMPIR` and `dpq_score` before complete-case filtering and export the results as a CSV. AI also helped create the first Table 1-style descriptive summary of the analytic sample.

### What I changed

I applied the code to our adult cohort and key analysis variables and used it to produce the missingness summary and first Table 1 for our analysis. The Table 1 format was later revised by the group for the final analysis.

### How I verified the result

1. I independently checked the number of missing values for `INDFMPIR` and `dpq_score` using `is.na()` on the adult cohort.
2. I confirmed that missingness was calculated before complete-case filtering.
3. I independently checked the analytic sample size and the mean and standard deviation values for age, `INDFMPIR`, and PHQ-9 used in the first Table 1.

<br>

## Preliminary figure, Table 1, missingness updates, interpretation and claim boundary (Morgan)

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

<br>

## Methods note, CSV checks and final render (Jade)

### Audit trail

No code was added in this part, so there are no AI prompt and Verified pairs to copy from the qmd.

### What AI helped with

Claude compared the teammate's starter methods note with the final analysis and helped check whether each claim in the note was supported by the code, the rendered output or a source.

### What I changed

I split the methods note into subsections (data and cohort, PHQ-9 total score, analytic sample, Table 1 and figure, software) and rewrote the PHQ-9 scoring rule as a table that matches `data/README.md`. Claude drafted this layout at my request, and I edited it before adding it to the note. I also revised the sentence that introduces the scoring guide reference.

### How I verified the result

1. I compared the numbers in the methods note with the re-rendered html: the analytic sample of 4,831 matches the cohort table, and the 53 adults with a refused or don't know answer match the counts table (23 and 51 answers).
2. I checked the PHQ-9 rule table in the methods note line by line against `data/README.md` and the scoring code in Setup 1.
3. I opened `table1.csv` and `missingness-summary.csv` and compared each number with the tables in the html.
4. I re-rendered the html after the final scoring code update and checked that the code shown in the html matches the qmd.
5. I searched for the scoring guide site linked in `data/README.md` to check who publishes it and whether it is a reliable source to reference.
