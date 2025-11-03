# School Incident Analysis - Google Sheets

This analysis explores reported school incidents in New York City between **school years 2013–2014 and 2015–2016**, using basic spreadsheet formulas and Pivot Tables.

The goal was to get familiar with the dataset structure and perform initial descriptive analysis directly in Google Sheets.

📄 [View the Google Sheet](https://docs.google.com/spreadsheets/d/1zbQY23ITLgMxgfDk0eIK354g8wK13n6wOKhqZ1ZwDK0/edit?gid=1495382759#gid=1495382759)

## Objectives

- Explore the raw CSV dataset using Google Sheets.
- Practice formulas, conditional logic, and pivot tables.
- Generate simple insights about NYC school incidents.


## Overview

- **How many total rows are there?** 6,310 → Counted all rows in column A (excluding the header). 
- **How many unique schools are listed?** 1,891 → Counted unique values in the `DBN` column. 
- **What is the most frequent incident type?** Non-Criminal Incidents (`NoCrim`) → Created a Pivot Table summing all incident types. 
- **What % of incidents occurred in the Bronx?** 28.24% → Added a calculated column summing all incidents per entry, created a Pivot Table by borough, and calculated percentage of total. 


💡 **Insights**:

- The Bronx and Brooklyn together account for 58% of all reported incidents, while Staten Island has the fewest reported incidents.
- Overall, incident frequency decreased between school years 2013–14 and 2015–16, with all categories showing a decline except non-criminal incidents, which increased slightly.

🧹 **Anomalies**:

- Missing data in several columns (`DBN`, `Register`, and `Building Name`).
- Some rows report 0 incidents or N/A across all incident types. likely data entry errors or “no incident” reports.

## Key Learnings

- Reinforced spreadsheet analysis skills (COUNT, UNIQUE, SUM, Pivot Tables).  
- Identified common data quality issues.  
- Laid the groundwork for the Python-based cleaning and SQL analysis in later steps.