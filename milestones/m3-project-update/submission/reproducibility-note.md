# Reproducibility note

The report is designed to run from the course GitHub Codespace. It identifies the project root using Git and reads the analysis file from `data/nhanes_merged.csv`, so no personal or absolute file paths need to be changed. The dashboard reads the same file with a path relative to the project root. This file is committed to the repository. It is built from the raw CDC files in `data/raw/` by the setup chunk in `milestones/m2-preliminary-analysis/submission/preliminary-analysis.qmd`, as described in `data/README.md`.

To rerun the work, open a new Codespace on `main` and run these commands from the project root:

```
quarto render milestones/m3-project-update/submission/report-draft.qmd
quarto render dashboard/dashboard.qmd
```

The report uses `tidyverse`, `knitr`, `haven`, `dplyr`, and `survey`. The `survey` package is used in M3 to apply the NHANES survey weights and account for the survey design.

We tested the report in the course Codespace. The first render failed because `survey` is not included in the default Codespace environment. After manually installing `survey`, `report-draft.qmd` rendered successfully and regenerated the report output. On 17 November 2026, the instructor confirmed we could use `survey`, and we added it to the package list in `.devcontainer/install-packages.sh` so a new Codespace installs it during setup. On 22 November 2026, we opened a new Codespace after this change and rendered both files without installing anything by hand. A Codespace created before 17 November 2026 must be deleted and recreated to pick up the change.