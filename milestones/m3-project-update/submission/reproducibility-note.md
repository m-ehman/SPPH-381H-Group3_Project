# Reproducibility note

The report is designed to run from the course GitHub Codespace. It identifies the project root using Git and reads the analysis file from `data/nhanes_merged.csv`, so no personal or absolute file paths need to be changed.

The report uses `tidyverse`, `knitr`, `haven`, `dplyr`, and `survey`. The `survey` package is used in M3 to apply the NHANES survey weights and account for the survey design.

For the final reproducibility check, we will open a fresh Codespace and render `report-draft.qmd`. We will confirm that the report runs without manual path or data changes and that the tables and figure are regenerated from the code.