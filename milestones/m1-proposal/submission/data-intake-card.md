# Data Intake Card

- **Dataset:** NHANES 2021-2023 Depression Screener (DPQ_L) and Demographics (DEMO_L)
- **Source and steward:** CDC/National Center for Health Statistics, National Health and Nutrition Examination Survey
- **Access:** Public-use XPT files downloaded from CDC and stored under `data/raw/`; the two files can be linked by participant ID `SEQN`; codebooks at <https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/DPQ_L.htm> and <https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/DEMO_L.htm>; checked 2026-10-15
- **Terms:** Public-use NHANES files under the NCHS Data User Agreement; cite CDC/NCHS documentation
- **Geography and time:** United States; August 2021 to August 2023
- **Format and level:** XPT (SAS Transport); row-level public-use records
- **Unit of analysis:** One participant aged 18 or older in the depression screener file
- **Key variables:** `DPQ010` to `DPQ090`, the nine PHQ-9 items scored 0-3 (7, 9, and `.` are missing codes), summed into a PHQ-9 total of 0-27; `INDFMPIR`, family income to poverty ratio (top-coded at 5); `RIDAGEYR`, age in years (top-coded at 80)
- **Privacy/security:** Use only aggregate outputs, avoid small-cell claims, and do not upload row-level records to external AI tools
- **Stewardship:** Report the self-harm item (`DPQ090`) only in aggregate, and describe income differences without blaming lower-income adults
- **Indigenous Data Sovereignty relevance:** No Indigenous community, service, territory, or identifier is part of the proposed comparison. We will reassess CARE/OCAP relevance if the project scope changes.
- **Known limitations:** The PHQ-9 is a screening tool, not a diagnosis; `INDFMPIR` is missing for some participants; the survey is cross-sectional, so it cannot show cause; unweighted results describe the sample only, not the U.S. population
- **KT framing:** The data can point to a pattern between income and depressive symptoms that is worth discussing, while making clear it is not evidence of cause
- **Citation:** CDC/NCHS, National Health and Nutrition Examination Survey 2021-2023, DPQ_L and DEMO_L, <https://wwwn.cdc.gov/nchs/nhanes/>, accessed 2026-10-15

AI could add the PHQ-9 answer codes 7 (Refused) and 9 (Don't know) into the total as if they were scores, even though they mean no answer. It could also treat an `INDFMPIR` value of 5 as exactly 5, even though it means 5 or higher. We checked both against the CDC codebooks. We will leave 7 and 9 out of the score but report how many there are, and describe 5 as "5 or higher" in any summary.
