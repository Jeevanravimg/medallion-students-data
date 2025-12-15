# Student Medallion Architecture – Databricks Lakehouse

This project implements a **Medallion Architecture (Bronze, Silver, Gold)** using **Databricks**, **Apache Spark**, **Delta Lake**, and **Unity Catalog** to process and analyze student-related data.  
Synthetic data is generated using **Faker**, ingested as raw CSV files, transformed into clean analytical tables, and finally aggregated for reporting and dashboards.

---

## 🏗️ Architecture Overview

- **Bronze Layer** – Raw data ingestion from CSV files
- **Silver Layer** – Cleaned, standardized, and deduplicated data
- **Gold Layer** – Aggregated and analytics-ready datasets
- **Jobs & Orchestration** – Automated execution of pipelines

---

## 📂 Unity Catalog Setup

### Schema Creation
A dedicated schema was created in Unity Catalog to organize all project tables:

### Volume Creation
A volume was created within the schema to store raw CSV data files.

### Data Storage Path
All raw CSV files are stored at:


---

## 🧪 Data Generation

- **Library Used:** Faker (Python)
- **Purpose:** Generate realistic synthetic student data
- **Special Cases Included:**
  - Null values
  - Duplicate records  
  (to simulate real-world data quality issues and enable cleaning exercises)

### Generated CSV Files
Four interlinked CSV files representing a student management system:

- `students.csv`
- `courses.csv`
- `enrollments.csv`
- `results.csv`

---

## 🥉 Bronze Layer – Raw Data Ingestion

### Key Activities
- Loaded raw CSV files for:
  - **Students**
  - **Courses**
  - **Enrollments**
  - **Results**
- Ingested data into Spark DataFrames with:
  - Schema inference
  - Header recognition
- Persisted data as **Delta tables** using overwrite mode

### Bronze Tables Created
- `bronze_students`
- `bronze_courses`
- `bronze_enrollments`
- `bronze_results`

### Validation
- Verified schema and data using Spark `display()` and schema printouts
- Ensured repeatable and reliable ingestion

---

## 🥈 Silver Layer – Data Cleaning & Standardization

### Key Activities
- Read Bronze layer Delta tables
- Cleaned and standardized data:
  - Casted columns to appropriate data types
  - Removed records with missing critical fields
  - Dropped duplicate rows
- Applied schema evolution where required

### Silver Tables Created
- `silver_students`
- `silver_courses`
- `silver_enrollments`
- `silver_results`

### Validation
- Displayed each Silver table to verify data quality and structure

---

## 🥇 Gold Layer – Aggregation & Analytics

### Student Performance Aggregation
- Total courses enrolled
- Total marks
- Performance metrics per student

### Course Performance Aggregation
- Total students per course
- Average, maximum, and minimum marks

### Department Performance Aggregation
- Department-wise student count
- Marks statistics by department

### Enrollment Statistics
- Enrollment counts by:
  - Course
  - Enrollment status

### Gold Outputs
- Analytics-ready Delta tables
- Dashboards created for visualization and insights

---

## ⏱️ Jobs & Orchestration

- Databricks Jobs created to:
  - Automate Bronze → Silver → Gold execution
  - Ensure correct dependency order
- Enables repeatable, production-style data pipelines

---

## 🛠️ Technologies Used

- Databricks
- Apache Spark
- Delta Lake
- Unity Catalog
- Python
- Faker
- GitHub (version control)

---

## 📌 Key Learnings

- End-to-end Medallion Architecture implementation
- Working with Unity Catalog schemas and volumes
- Real-world data quality handling (nulls & duplicates)
- Building analytics-ready datasets
- Orchestrating pipelines using Databricks Jobs

---

## 📎 Repository Structure 

medallion-students-data/
│
├── POC_Jeevan/
│ ├── Bronze_Layer.ipynb
│ ├── Silver_Layer.ipynb
│ ├── Gold_Layer.ipynb
│ └── Data_generation.ipynb
│
├── README.md


---

## 👤 Author

**Jeevan M G**  
Databricks | Data Engineering | Lakehouse Architecture
