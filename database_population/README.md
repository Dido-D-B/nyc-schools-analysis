# Data Cleaning & Database Population — NYC Schools Project

This folder contains the **Python-based data cleaning process** for the NYC SAT Results dataset and the steps used to **populate the PostgreSQL database** with the cleaned data.

## Objective
Prepare the NYC SAT Results dataset for structured storage in a relational database by:

1. Cleaning and validating the raw data.
2. Handling duplicates, data types, and missing values.
3. Designing a clean table schema.
4. Uploading the final dataset to PostgreSQL using SQLAlchemy.


## Files Overview

`data_cleaning.ipynb`: Jupyter notebook containing all data assessment, cleaning, validation, and export steps. 
`cleaned_sat_results.csv`: Final cleaned dataset ready for database upload.

## Data Cleaning Summary

### **Data Assessment**

The dataset was first explored to understand structure and quality:

- Inspected shape, column names, and data types.
- Checked for missing values and duplicates.
- Assessed value consistency and potential anomalies.

### **Cleaning Steps**

- **Column Normalization** : Renamed columns to lowercase and snake_case for consistency.
- **Duplicate Handling**: Removed duplicate rows and identical columns. 
- **Data Type Conversion**: Converted numeric columns from string → integer/float. 
- **Missing Values**: Imputed missing `pct_students_tested` and `academic_tier_rating` values using the **mean** instead of dropping them. 
- **Value Validation**: Removed invalid SAT scores outside the valid range (200–800). 
- **Outlier Review**: Checked `num_of_sat_test_takers` distribution to ensure plausible values. 

## Rationale for Imputation

Originally, missing rows were dropped, but this risked losing valid SAT data. Following feedback, missing values were imputed using the **mean** of their respective columns, ensuring the dataset remained complete while maintaining statistical balance.

## Database Population

### **Schema Design**

```
| Column | Type | Description |
|:--|:--|:--|
| `dbn` | TEXT | unique school identifier (primary key) |
| `school_name` | TEXT | name of the school |
| `num_of_sat_test_takers` | INTEGER | number of students taking SAT |
| `sat_critical_reading_avg_score` | INTEGER | average reading score |
| `sat_math_avg_score` | INTEGER | average math score |
| `sat_writing_avg_score` | INTEGER | average writing score |
| `pct_students_tested` | DOUBLE PRECISION | proportion of students tested (0–1) |
| `academic_tier_rating` | DOUBLE PRECISION | school tier rating |
| `internal_school_id` | BIGINT | internal identifier |
```

### **Exporting to PostgreSQL**

Connection created using `SQLAlchemy` with a PostgreSQL engine:

```python
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine("postgresql+psycopg2://<username>:<password>@<host>/<database>")

new_df.to_sql(
    name='dido_sat_results',
    con=engine,
    schema='nyc_schools',
    if_exists='replace',
    index=False
)
```

### PostgreSQL Database

* **Host**: ep-falling-glitter-a5m0j5gk-pooler.us-east-2.aws.neon.tech
* **Port**: 5432
* **Database Name**: neondb
* **User**: neondb_owner