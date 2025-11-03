# SQL Query Exploration — NYC Schools Project

This folder contains the notebook used to **query and analyze** the NYC Schools database. The goal was to practice **SQL analysis within Python** using PostgreSQL connections.

## Objective

Run SQL queries directly from Python using `pandas` and `SQLAlchemy` to:

- Explore and validate database content.
- Answer analytical questions about school distribution and student demographics.
- Practice combining SQL logic with Python visualization and insights.

## Files Overview

`queries.ipynb`: Jupyter notebook containing SQL-based analytical queries with outputs and insights.
`README.md`: Documentation summarizing the purpose and methods used for this analysis.

## Example Tasks

### School Distribution

**Question:** How many schools are there in each borough?  
**Approach:**  Queried the `high_school_directory` table and grouped results by `borough`.

```sql
SELECT borough, COUNT(DISTINCT dbn)
FROM nyc_schools.high_school_directory
GROUP BY borough;