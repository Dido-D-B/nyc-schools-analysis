# NYC School Analysis - Onboarding Week Project

🗓️ Project duration: 1 week

From Google Sheet analysis → Python data cleaning → SQL database population

## Objective

This onboarding project focused on understanding the **NYC public schools dataset** through different stages of the data workflow — from exploratory analysis to database integration.

The main goal was to:

* Explore and analyze data from various sources
* Clean and normalize data for consistency
* Load the prepared data into a PostgreSQL database
* Practice SQL querying, documentation, and version control in VS Code and GitHub

## Tools & Technologies

* **Google Sheets**: Initial data exploration and cleaning
* **Python** (Pandas, SQLAlchemy): Data wrangling, cleaning, and export to DB
* **PostgreSQL**: Database storage and querying
* **VS Code** + **GitHub**: Version control and project organization
* **Matplotlib** / **Seaborn**: Data visualization 
* **SQL**: Querying and aggregating cleaned data

## Project Structure 

````
NYC-SCHOOLS-ANALYSIS/
│
├── incident_analysis_google_sheets/                        # Initial analysis of incident reports in Google Sheets
│   ├── raw_data.csv
│   ├── cleaned_data_google_sheets.csv
│   └── README.md
│
├── school_directory_exploration_python/                    # Python-based data exploration and visualization
│   ├── notebook.ipynb
│   ├── visuals/
│   │   ├── avg_num_students_borough.png
│   │   ├── dist_school_size_borough.png
│   │   ├── num_schools_borough.png
│   │   └── start_grade_dist_borough.png
│   └── README.md
│
├── database_population/                                    # Data cleaning and database upload (PostgreSQL)
│   ├── data_cleaning.ipynb
│   ├── cleaned_sat_results.csv
│   └──  README.md
│
├── database_queries_sql/                                   # SQL queries and analysis examples
│   ├── queries.ipynb
│   └──  README.md
│
├── requirements.txt
└── README.md
````

## Data Cleaning Summary

The SAT results dataset was cleaned and prepared before being uploaded to the database.
Key steps included:

* **Normalization of column names**
  → lowercase, underscores, and consistent naming conventions
* **Removal of duplicate rows and columns**
  → handled identical SAT score columns and repeated school entries
* **Data type conversions**
  → converted object/string columns to numeric where appropriate
* **Missing data handling**
  → instead of dropping, imputed missing values (pct_students_tested and academic_tier_rating) using the mean
* **Validation checks**
  → ensured SAT scores fell within valid ranges (200–800)
  → confirmed consistency of percentage values and IDs

## Database Population

After cleaning, the data was uploaded into a PostgreSQL database (nyc_schools schema).

**Table name**: dido_sat_results

<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><code>dbn</code></td><td><code>TEXT</code></td><td>unique school identifier (primary key)</td></tr>
    <tr><td><code>school_name</code></td><td><code>TEXT</code></td><td>name of the school</td></tr>
    <tr><td><code>num_of_sat_test_takers</code></td><td><code>INTEGER</code></td><td>number of students taking SAT</td></tr>
    <tr><td><code>sat_critical_reading_avg_score</code></td><td><code>INTEGER</code></td><td>average reading score</td></tr>
    <tr><td><code>sat_math_avg_score</code></td><td><code>INTEGER</code></td><td>average math score</td></tr>
    <tr><td><code>sat_writing_avg_score</code></td><td><code>INTEGER</code></td><td>average writing score</td></tr>
    <tr><td><code>pct_students_tested</code></td><td><code>DOUBLE PRECISION</code></td><td>proportion of students tested (0–1)</td></tr>
    <tr><td><code>academic_tier_rating</code></td><td><code>DOUBLE PRECISION</code></td><td>school tier rating</td></tr>
    <tr><td><code>internal_school_id</code></td><td><code>BIGINT</code></td><td>internal identifier</td></tr>
  </tbody>
</table>

## Key Learnings

* Practiced a full data pipeline from raw data to database integration
* Gained experience with ETL workflows in Python and SQL
* Improved understanding of data cleaning best practices and when to impute vs. drop missing values
* Applied version control (Git) to manage notebook versions and documentation
 


