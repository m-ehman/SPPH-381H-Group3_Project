# Reproducibility Plan

## Repository folders

We use the folders that came with the course template: 

- `data/raw/`: the two CDC files, `DEMO_L.xpt` and `DPQ_L.xpt`, kept exactly as downloaded.
- `milestones/`: each milestone's files will be placed in its own `submission/` folder. 
- `report/`: the final report, `report.qmd`, and its rendered `report.html`.
- `dashboard/`: the dashboard-style KT product.

## Data access plan

The data come from two public-use files in the CDC NHANES August 2021–August 2023 release. We downloaded them on 2026-10-15 and committed them to `data/raw/`. Both files are small (under 3 MB each) and contain no direct identifiers. No one edits them by hand.

Anyone who needs a fresh copy can download each file from the link on its CDC codebook page:

- Demographics (`DEMO_L`): <https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/DEMO_L.htm>
- Depression screener (`DPQ_L`): <https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/DPQ_L.htm>

Data cleaning and variable derivation will be performed in the relevant `.qmd` files.

## Packages and dependencies

We use R in the course Codespace, which already includes every package we need.

- `tidyverse` for data handling and figures
- `haven` to read the XPT files. It comes with the tidyverse, but `library(tidyverse)` does not load it, so we will call `library(haven)` separately.
- `knitr` for tables

If we add a package later, we will note it in the repository README before anyone relies on it.

## How another student can rerun the work

The template's `_quarto.yml` sets `execute-dir: project`, so every `.qmd` runs from the repository root. Paths such as `data/raw/DPQ_L.xpt` therefore work wherever the `.qmd` sits.

To rerun a milestone, open the repository in a Codespace and render its `.qmd` from the root. The render rebuilds the tables, figures, and HTML from the raw files, so nothing needs editing by hand.

## Feasibility check

On 2026-10-25, Morgan read both files into R in the course Codespace. `DEMO_L` had 11,933 rows and `DPQ_L` had 6,337 rows, which match the counts in the CDC codebooks. The project uses R only.