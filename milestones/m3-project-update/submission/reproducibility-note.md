# Reproducibility note

The report is designed to run from the course GitHub Codespace. It identifies the project root using Git and reads the analysis file from `data/nhanes_merged.csv`, so no personal or absolute file paths need to be changed.

The report uses `tidyverse`, `knitr`, `haven`, `dplyr`, and `survey`. The `survey` package is used in M3 to apply the NHANES survey weights and account for the survey design.

We tested the report in the course Codespace. The first render failed because `survey` is not included in the default Codespace environment. After manually installing `survey`, `report-draft.qmd` rendered successfully and regenerated the report output. Approval has been requested to add `survey` to the project dependency setup so that a fresh Codespace can run the report without requiring a manual package installation.