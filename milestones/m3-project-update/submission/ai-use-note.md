# AI use notes

## Report draft

### What AI helped with
AI helped to use WTMEC2YR (2 year sample weight) in the analysis and NHANES survey design object for future analysis. 

### AI audit trail
AI use note: Use WTMEC2YR as the participant-level weight for the estimates rather than multiplying it into individual variables. Also account for SDMVSTRA (masked variance pseudo-stratum) and SDMVPSU (masked variance pseudo-PSU).
Verified: I verified the code Copilot gave me by checking the NHANES documentation and the survey package documentation. The code correctly sets up the survey design using the appropriate weights and stratification variables.

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