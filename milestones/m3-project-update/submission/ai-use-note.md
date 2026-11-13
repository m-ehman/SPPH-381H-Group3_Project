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