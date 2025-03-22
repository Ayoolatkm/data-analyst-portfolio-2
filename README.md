# Data Analyst Portfolio

Welcome to my Data Analyst portfolio! This repository showcases my skills, projects, and expertise in data analysis, SQL, Python, Power BI, and Tableau. I am passionate about extracting insights from data and providing actionable solutions.

## 📌 About Me
- **Name:** Ayoola Alonge
- **Location:** UK
- **Background:** MSc in Sustainable Planning and Environmental Management
- **Current Role:** Community Support Worker at Cornwall Partnership NHS Foundation Trust
- **Transitioning Into:** Data Analyst / Data Architect

## 🛠 Tools & Skills
- **Programming & Data Manipulation:** SQL, Python (Pandas, NumPy, Matplotlib, Seaborn)
- **Data Visualization:** Power BI, Tableau, Excel
- **Version Control:** GitHub

## 📊 Featured Projects
### 1️⃣ NHS Patient Wait Time Analysis
- **Goal:** Analyze patient wait times and identify bottlenecks in NHS services
- **Skills Used:** SQL, Python (Pandas & Matplotlib), Power BI, Tableau
- **Key Insights:**
  - **Average Patient Wait Time Across Hospitals:** Identify hospitals with the longest and shortest average wait times.
  - **Percentage of Patients Waiting Over 4 Hours:** Define the proportion of patients experiencing long delays, broken down by hospital and department.
  - **Peak Wait Time Hours & Days:** Identify trends in patient wait times based on time of day and day of the week.
  - **Wait Time Distribution by Age Group & Severity:** Compare how wait times differ across patient demographics.
  - **Improvement Recommendations:** Identify bottlenecks and suggest data-backed solutions.
- **Files:**
  - `datasets/nhs_wait_times.csv`
  - `sql/nhs_wait_times_analysis.sql`
  - `python/nhs_wait_times_analysis.ipynb`
  - `visuals/nhs_wait_times_dashboard.pbix`
  - `visuals/nhs_wait_times_dashboard.png`

#### SQL Queries for NHS Patient Wait Time Analysis
<details>
<summary>View SQL Queries</summary>

```sql
SELECT patient_id, appointment_date, arrival_time, seen_time, 
       TIMESTAMPDIFF(MINUTE, arrival_time, seen_time) AS wait_time_minutes
FROM nhs_wait_times
WHERE appointment_date BETWEEN '2024-01-01' AND '2024-12-31';
```

```sql
SELECT hospital_name, AVG(TIMESTAMPDIFF(MINUTE, arrival_time, seen_time)) AS avg_wait_time
FROM nhs_wait_times
GROUP BY hospital_name
ORDER BY avg_wait_time DESC;
```

```sql
SELECT patient_id, hospital_name, arrival_time, seen_time, 
       TIMESTAMPDIFF(MINUTE, arrival_time, seen_time) AS wait_time_minutes
FROM nhs_wait_times
WHERE TIMESTAMPDIFF(MINUTE, arrival_time, seen_time) > 240;
```

```sql
SELECT HOUR(arrival_time) AS hour_of_day, 
       AVG(TIMESTAMPDIFF(MINUTE, arrival_time, seen_time)) AS avg_wait_time
FROM nhs_wait_times
GROUP BY hour_of_day
ORDER BY avg_wait_time DESC;
```

```sql
SELECT CASE 
         WHEN age < 18 THEN 'Under 18'
         WHEN age BETWEEN 18 AND 40 THEN '18-40'
         WHEN age BETWEEN 41 AND 65 THEN '41-65'
         ELSE '65+' END AS age_group, 
       AVG(TIMESTAMPDIFF(MINUTE, arrival_time, seen_time)) AS avg_wait_time
FROM nhs_wait_times
GROUP BY age_group
ORDER BY avg_wait_time DESC;
```
</details>

### 2️⃣ Data Cleaning with SQL
- **Goal:** Clean and normalize messy datasets using SQL techniques
- **Files:** `sql/data_cleaning_project.sql`

### 3️⃣ Python Exploratory Data Analysis (EDA)
- **Goal:** Perform EDA on a dataset to uncover trends and insights
- **Files:** `python/eda_project.ipynb`

## 📂 Repository Structure
```
📁 data-analyst-portfolio
│-- 📄 README.md
│-- 📁 datasets
│   │-- nhs_wait_times.csv
│-- 📁 sql
│   │-- nhs_wait_times_analysis.sql
│   │-- data_cleaning_project.sql
│-- 📁 python
│   │-- nhs_wait_times_analysis.ipynb
│   │-- eda_project.ipynb
│-- 📁 visuals
│   │-- nhs_wait_times_dashboard.pbix
│   │-- nhs_wait_times_dashboard.png
│-- 📁 notebooks
│   │-- exploratory_data_analysis.ipynb
```

## 🚀 How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/Ayoolatkm/data-analyst-portfolio-2.git
   ```
2. Navigate to the project folder and explore the SQL, Python, and visualization files.
3. Open the Jupyter notebooks or Power BI files to analyze the data.

## 📬 Contact
- **GitHub:** [https://github.com/Ayoolatkm](https://github.com/Ayoolatkm)
- **Email:** ayoolaalonge@gmail.com

![GitHub last commit](https://img.shields.io/github/last-commit/Ayoolatkm/data-analyst-portfolio-2)

---
This portfolio will be continuously updated with new projects and improvements. Stay tuned! 🚀
