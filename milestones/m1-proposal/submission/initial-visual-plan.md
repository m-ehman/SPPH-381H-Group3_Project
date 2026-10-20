# Initial Visual Plan

## Planned figure

We plan to create a scatter plot showing the relationship between family income-to-poverty ratio (`INDFMPIR`) and total PHQ-9 depression score among adults in NHANES 2021–2023.

`INDFMPIR` will initially be treated as a continuous socioeconomic measure. NHANES calculates this variable as family income divided by the applicable poverty guideline. Values at or above 5.00 are top-coded as 5.00, which will be considered when interpreting the upper end of the distribution.

The PHQ-9 outcome will be calculated by summing the nine depression screener items (`DPQ010`–`DPQ090`), each scored from 0 to 3, producing a total score ranging from 0 to 27 for participants with complete responses.

Because both variables are numeric, the initial figure will retain their numeric form rather than immediately converting them into categories. A fitted trend line may be added to make the overall relationship easier to interpret.

## Audience purpose

The figure is intended to help the audience see whether depressive symptom severity tends to vary across levels of socioeconomic status and whether there appears to be an overall pattern between income-to-poverty ratio and PHQ-9 score.

## Risk of misinterpretation

An observed relationship between income-to-poverty ratio and PHQ-9 score should not be interpreted as evidence that lower income causes depression. NHANES data are observational and cross-sectional, so other factors may contribute to any association that is observed.

The top-coding of `INDFMPIR` at 5.00 also means that participants with higher income-to-poverty ratios cannot be distinguished from one another above that threshold, which may limit interpretation at the upper end of the income distribution.