Expected folders are 'data/', 'report/', 'dashboard/', and 'milestones/'. The cached public-use-derived CSV will be committed once under 'data/' and treated as read-only. R source files will load tidyverse and knitr explicitly and use paths relative to the project root.

Another student should be able to open the course Codespace, start at the repository root, and run quarto render on the named source. Generated tables, figures, and HTML files will be regenerated from code rather than edited by hand. Any added dependency will be recorded before use.

Feasibility check: the CSV loaded successfully in the course environment with 105,626 rows and 18 columns. R is the project language; a Python version is not needed for the proposed questions.