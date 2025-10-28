# 🩺 Vaccination Data Cleaning & MySQL Integration

## 📘 Overview

This project involves **data cleaning, transformation, and storage** of global vaccination datasets into a structured **MySQL database** for future analysis and visualization.
The datasets contain information about vaccine coverage, incidence rates, reported disease cases, vaccine introductions, and vaccination schedules from multiple sources.

---

## 🧩 Project Objectives

* Clean and preprocess multiple Excel datasets related to global vaccination statistics.
* Handle missing values, incorrect data types, and inconsistent entries.
* Structure the data into well-defined MySQL tables.
* Store the cleaned and processed data in a MySQL database named `vaccination_db`.
* Prepare the data for downstream analysis (e.g., visualization, dashboards, ML models).

---

## 🗂️ Datasets Used

| Dataset                            | Description                                                         |
| ---------------------------------- | ------------------------------------------------------------------- |
| **coverage-data.xlsx**             | Contains vaccine coverage information across countries and years.   |
| **incidence-rate-data.xlsx**       | Includes incidence rates of various vaccine-preventable diseases.   |
| **reported-cases-data.xlsx**       | Provides the number of reported cases for each disease and country. |
| **vaccine-introduction-data.xlsx** | Tracks the introduction of different vaccines in each country.      |
| **vaccine-schedule-data.xlsx**     | Contains vaccine schedules, doses, and target populations.          |

---

## 🧼 Data Cleaning Steps

### 🔹 1. Coverage Data

* Checked for missing and duplicate entries.
* Filled missing values with column means (for numeric columns) and mode (for categorical).
* Converted year into integer format.
* Converted `TARGET_NUMBER`, `DOSES`, and `COVERAGE` columns to integers.
* Trimmed whitespaces and standardized text data.
* Removed duplicates and remaining nulls.

### 🔹 2. Incidence Data

* Removed rows with missing values.
* Converted year and incidence rate to integer type.
* Replaced invalid denominators with default numeric values.
* Handled null and non-numeric entries safely.

### 🔹 3. Reported Cases Data

* Filled missing case values with mean.
* Converted `CASES` to integer.
* Cleaned and standardized disease names and country names.

### 🔹 4. Vaccine Introduction Data

* Removed null rows.
* Converted `YEAR` to integer type.
* Verified country and vaccine names.
* Ensured `INTRO` column contained valid 'Yes'/'No' entries.

### 🔹 5. Vaccine Schedule Data

* Filled missing categorical data using mode values.
* Converted all numerical columns to appropriate datatypes.
* Cleaned text fields like `AGEADMINISTERED`, `SOURCECOMMENT`, and `TARGETPOP`.
* Dropped any remaining null entries.

---

## 🗄️ Database Integration

### Database: `vaccination_db`

Created using MySQL with the following tables:

* **coverage**
* **incidence**
* **reported**
* **vaccine_int**
* **vaccine_sch**

Each dataset was iterated row by row and inserted into its respective table using Python’s `mysql.connector`.

### Example of Table Creation:

```python
cursor.execute("""
CREATE TABLE IF NOT EXISTS coverage (
    `GROUP` VARCHAR(255),
    CODE VARCHAR(255),
    NAME VARCHAR(255),
    YEAR INT,
    ANTIGEN VARCHAR(255),
    ANTIGEN_DESCRIPTION VARCHAR(255),
    COVERAGE_CATEGORY VARCHAR(255),
    COVERAGE_CATEGORY_DESCRIPTION VARCHAR(255),
    TARGET_NUMBER INT,
    DOSES INT,
    COVERAGE INT
);
""")
```

---

## 🛠️ Tech Stack

| Tool                                            | Purpose                    |
| ----------------------------------------------- | -------------------------- |
| **Python (Pandas, NumPy, Seaborn, Matplotlib)** | Data analysis and cleaning |
| **MySQL**                                       | Data storage               |
| **mysql.connector**                             | Python-MySQL integration   |
| **Jupyter Notebook / VSCode**                   | Development environment    |

---

## 📊 Exploratory Analysis (EDA)

* Used **Seaborn heatmaps** to visualize missing values.
* Generated summary statistics using `describe()`.
* Checked column data types, unique values, and duplicates.
* Ensured proper numeric conversions for analytical consistency.

---

## 🚀 Future Work

* Add SQL queries for analysis (e.g., coverage trends by region or disease).
* Build a **Streamlit dashboard** to visualize vaccination statistics.
* Integrate with APIs to update the database automatically.
* Use machine learning to predict vaccination coverage or outbreak likelihood.

---

## 👨‍💻 Author

**Sachin Hembram**
📧 Email: *sachincmf@gmail.com*
📍 Data Scientist | Machine Learning | Data Visualization
