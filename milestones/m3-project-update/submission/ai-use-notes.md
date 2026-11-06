# AI use notes

## What AI helped with
AI helped to use WTMEC2YR (2 year sample weight) in the analysis and NHANES survey design object for future analysis. 

## AI aduit trail
AI use note: Use WTMEC2YR as the participant-level weight for the estimates rather than multiplying it into individual variables. Also account for SDMVSTRA (masked variance pseudo-stratum) and SDMVPSU (masked variance pseudo-PSU).
Verified: I verified the code Copilot gave me by checking the NHANES documentation and the survey package documentation. The code correctly sets up the survey design using the appropriate weights and stratification variables.