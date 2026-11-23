# AI use notes

## Report draft

### What AI helped with
Copilot helped set up the NHANES survey design object, using WTMEC2YR (the 2-year MEC sample weight) as the weight and SDMVSTRA and SDMVPSU for the design. It also helped adapt our M2 Table 1 code to survey-weighted estimates using `svyby()`, `svyvar()` and `svytable()`. I updated the title, interpretation and limitations myself.

The income-band, Table 1 and figure code started from our M2 analysis. Their AI prompt and Verified pairs are in the M2 `ai-use-note.md`.

### AI audit trail
Survey design
- AI prompt: Use WTMEC2YR as the participant-level weight for the estimates rather than multiplying it into individual variables. Also account for SDMVSTRA (masked variance pseudo-stratum) and SDMVPSU (masked variance pseudo-PSU).
- Verified: I verified the code Copilot gave me by checking the NHANES documentation and the survey package documentation. The code correctly sets up the survey design using the appropriate weights and stratification variables.

Weighted Table 1
- AI prompt: Adapt our Table 1 code to the survey design: use svyby() for the weighted mean and SD of dpq_score by income_band, svytable() for each band's weighted share, and keep the unweighted N from count().
- Verified: the six band Ns match our M2 Table 1 and add to 4,831, the weighted shares add to 100%, and the figure's points match the weighted means.

### What I changed
- I updated the title to "Association between Income and Depression in NHANES Adults", following the M1 feedback.
- I replaced the unweighted M2 summaries with survey-weighted estimates. Table 1 keeps the unweighted N and now shows weighted percentages, means and SDs, and the figure plots the weighted means.
- I built the survey design on the merged file and then used `subset()` for adults and complete cases, instead of filtering the data first, so the design information stays intact.
- I revised the limitations following the M1 feedback, adding that self-reported answers can bring social desirability bias, recall bias and misclassification. I removed the unweighted limitation now that the weights are applied.

### How I verified the result
- I checked the survey design code against the NHANES documentation and the survey package documentation.
- The analytic sample is still 4,831 and the six band counts match our M2 Table 1, so applying the weights did not drop or add anyone.
- The weighted shares in Table 1 add to 100%.
- The weighted means are close to the unweighted M2 means (for example, 5.6 vs 5.7 for "Under 1"), as expected.
- The figure's points and n labels match Table 1.

## Dashboard and dashboard preview

### AI audit trail
Setup
- AI prompt: Adapt the setup code from report-draft.qmd for the dashboard. Keep the survey design (WTMEC2YR, SDMVSTRA, SDMVPSU), the age 18+ and complete-case filters, and the income bands. Load the data with a relative path and load only the packages this page uses.
- Verified: the analytic sample is n = 4,831, the same as the All adults row of Table 1 in report-draft.html. The six income band counts match the N column of that table. The weight and design variables are the same as in report-draft.qmd.

Control
- AI prompt: Add one editable control value for the income band, and stop with a clear error if the value is not one of the six band labels.
- Verified: changing the value to "5 or higher" updated the table, the figure title, and the interpretation. An invalid value stops the render with the error message.

Table
- AI prompt: Adapt the Table 1 code from report-draft.qmd for the dashboard: show only the selected band and All adults, with a caption on which columns are weighted.
- Verified: rows match Table 1 in report-draft.html, including after changing selected_band. The caption was checked against the code.

Figure
- AI prompt: Adapt the figure from report-draft.qmd for the dashboard: highlight the selected band in red, put it in the title, and add a caption with the exclusions and the descriptive limit.
- Verified: n labels and point heights match the figure in report-draft.html. Each caption statement was checked against the code.

### What AI helped with
- Adapting the setup, Table 1, and figure code from report-draft.qmd into a dashboard with one editable control (`selected_band`).
- Drafting the figure and table captions, the interpretation, and the limitation text, which I revised to match the report draft and the M1 feedback.
- Drafting the wording of dashboard-preview.md.

### What I changed

I wrote the dashboard question to include the control, the selected income band, so that the question matches what the audience can change on the dashboard. I used the report draft's interpretation sentence so the dashboard and the report make the same claim. Following the M1 feedback, I included misclassification in the self-report limitation. I described the overall mean as "all adults included in the analysis" so it is not read as all NHANES adults.

### How I verified the result

- I compared the table rows and the figure's n labels and point heights with report-draft.html, before and after changing selected_band.
- I checked each caption statement against the code: N is an unweighted count(), and the percentages, means, and SDs are survey-weighted.
- I checked the information in dashboard-preview.md against dashboard.qmd and the rendered dashboard.html.

## Project update

### AI audit trail

Project update structure  
- AI prompt: Help organize the M3 project update using the current report title, audience, research question, analytic sample, one stable finding, one choice needing review, and next steps.
- Verified: I checked each section against the current report draft before adding it.

Weighted finding  
- AI prompt: Help identify the main survey-weighted finding from the current M3 report without overstating the relationship or implying causation.
- Verified: I checked the weighted PHQ-9 values and the interpretation against the current rendered report. The lowest income group had the highest weighted mean PHQ-9 score and the highest income group had the lowest.

Wording  
- AI prompt: Help revise the project update so the wording is clear and academic but still sounds natural and similar to my writing style.
- Verified: I reviewed the wording and made changes before adding it to `project-update.md`.

### What AI helped with

- Organizing the required sections of `project-update.md`.
- Identifying the main weighted finding from the current report.
- Drafting and revising some of the wording so the update was clear without making a causal claim.

### What I changed

I updated the draft using the current report title, audience, analytic sample, and weighted findings instead of the earlier unweighted results. I also adjusted parts of the wording after comparing the draft with the current report.

### How I verified the result

- I checked the title, audience, research question, and analytic sample against the current report draft.
- I compared the stable finding with the weighted values shown in the rendered report.
- I checked that the wording described an association rather than implying that income causes differences in depression scores.


## Reproducibility note

### AI audit trail

Reproducibility note structure  
- AI prompt: Help draft a reproducibility note using the report's file paths, package requirements, Codespace setup, and the survey-weighted analysis.
- Verified: I checked the file path and package information against the current report code.

Codespace error  
- AI prompt: Help interpret the Codespace render error and identify what should be documented in the reproducibility note.
- Verified: I ran the render myself. The first render failed because the `survey` package was not installed in the course Codespace.

Reproducibility test  
- AI prompt: Help determine the next step for checking whether the rest of the report reproduces after the missing package error.
- Verified: After manually installing `survey`, I reran `report-draft.qmd` and confirmed that it rendered successfully.

Final wording  
- AI prompt: Help revise the reproducibility note so it clearly separates what we successfully tested from the unresolved `survey` package dependency.
- Verified: I revised the note based on the actual results of the Codespace test.

### What AI helped with

- Drafting the structure and wording of `reproducibility-note.md`.
- Identifying the missing `survey` package as the reason the first render failed.
- Helping organize the results of the reproducibility check so the note clearly distinguishes between what was successfully tested and what still depends on the project setup.

### What I changed

I changed the note after running the reproducibility check myself. Instead of only saying that we planned to test the report, I updated it to explain that the report initially failed because `survey` was missing and then rendered successfully after the package was manually installed. I also kept the unresolved package dependency separate from the parts of the report that were successfully tested.

### How I verified the result

- I confirmed that the report reads the analysis file from `data/nhanes_merged.csv` using the project root instead of a personal file path.
- I checked the packages loaded in the report, including `survey`.
- I rendered `report-draft.qmd` in the course Codespace and confirmed that the first render failed because `survey` was not installed.
- After manually installing `survey`, I reran the report and confirmed that it rendered successfully and regenerated the report output.

## Feedback request and final check

### AI audit trail

Report draft edits
- AI prompt: Revise the interpretation so it gives the Table 1 numbers and describes the gap at the same strength as our M2 interpretation, with no causal or national claim. Restore the M2 figure caption for the weighted results and add a limitation on adults excluded for missing data.
- Verified: each number in the interpretation matches Table 1 in the re-rendered report (5.6, 2.9, a gap of 2.7, weighted SD 4.7). The report and dashboard make the same association claim.

Reproducibility note, project update and feedback request
- AI prompt: Update the reproducibility note and project update now that `survey` is in the Codespace setup, and draft a feedback request with one specific question each on correctness, interpretation, visual clarity, reproducibility and audience fit.
- Verified: the render commands, data path and package list match the repository (`data/README.md` and `.devcontainer/install-packages.sh`). The stable finding numbers match Table 1 and the M2 `table1.csv`. Each feedback question points to something in the report or dashboard.

### What AI helped with

- Claude reviewed the M3 brief and the M3 files and flagged the interpretation wording ("substantial" and "clear downward trend"), the missing figure caption and missingness limitation, and the out-of-date reproducibility note and next steps.
- AI drafted or suggested the revised interpretation, the figure caption, the missingness limitation, a corrected weight explanation, a sentence on the PHQ-9 scoring rule and analytic sample, the title header, an in-text citation and a grammar fix in `report-draft.qmd`. No analysis code changed. The only code chunk changes are the figure caption option and relabelling an AI comment to "AI prompt:" to match this note.
- AI drafted a first pass of the language updates to `reproducibility-note.md` and `project-update.md`, and drafted `feedback-request.md`.

### What I changed

- I edited Claude's suggested wording throughout for plain language, clarity, and length before adding it to our files.
- I added the date the instructor confirmed `survey` to the reproducibility note, and had the reproducibility question in the feedback request say that we added a package.

### How I verified the result

- I opened a new Codespace after the `survey` setup change and rendered `report-draft.qmd` and `dashboard.qmd` without installing anything by hand.
- I checked the numbers in the revised interpretation and the project update against Table 1 in the re-rendered report and the M2 `table1.csv`.
- I ran `band_summary` and `overall_sd` in R and confirmed the weighted means behind the interpretation: 5.62 for "Under 1" and 2.92 for "5 or higher" (a gap of about 2.7), an overall SD of 4.67, and a lower mean in each higher band.
- I compared the dashboard table for "Under 1" (731, 13.4, 5.6 (5.7)) with Table 1 in the report.
- I checked that the report and dashboard make the same association claim and do not make a causal claim.