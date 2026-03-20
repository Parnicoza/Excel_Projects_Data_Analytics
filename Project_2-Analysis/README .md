# 📊 Excel Salary Analysis

## Introduction

Exploring job postings as someone interested in the data field, I wanted to go beyond just looking at salaries — I wanted to understand what drives them. This project uses Excel to analyze the relationship between skills and pay, regional salary differences, and which skills are most in demand across data roles.

The dataset comes from Luke Barousse's Excel course and contains real-world data science job postings from 2023.

### Questions Analyzed

1. **Do more skills get you better pay?**
2. **What's the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What's the pay for the top 10 skills?**

### Excel Skills Used

- **🔍 Power Query**
- **💪 Power Pivot**
- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**

### Dataset

Real-world job postings from 2023, including:

- **👨‍💼 Job titles**
- **💰 Salaries**
- **📍 Locations**
- **🛠️ Skills**

---

## 1️⃣ Do more skills get you better pay?

### 🔍 Skill: Power Query (ETL)

I used Power Query to extract and transform the raw data, producing two clean tables:

- `data_jobs_all` — job listings with title, country, salary, and schedule type
- `data_job_skills` — skills associated with each job ID

Both tables were cleaned (column types adjusted, unnecessary columns removed, whitespace trimmed) and loaded into the workbook as the foundation for all analysis.

### 📊 Analysis

#### 💡 Insights

- There is a clear positive correlation between the number of skills requested and median salary. Senior Data Engineer roles average ~8 skills per job and a median salary of $147,500, while Business Analyst roles average fewer skills and lower pay.
- Roles requiring more specialized skill sets consistently command higher market value.

#### 🤔 So What

Acquiring multiple relevant skills — especially technical ones — is directly tied to salary growth, particularly for anyone targeting senior or engineering roles.

---

## 2️⃣ What's the salary for data jobs in different regions?

### 🧮 Skills: PivotTables & DAX

I built a PivotTable using the Data Model created in Power Pivot, then added DAX measures to calculate median salaries for US vs. non-US roles separately.

**Median Salary (all):**
```
Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
```

**Median Salary (US only):**
```
=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States"
)
```

### 📊 Analysis

#### 💡 Insights

- Senior Data Engineer and Data Scientist roles lead in median salary both in the US and internationally.
- US salaries are notably higher in technical roles — Senior Data Engineers earn $150,000 in the US vs. $147,500 globally.
- Cloud Engineer and Software Engineer roles show the largest gap between US and non-US compensation.

#### 🤔 So What

For salary negotiations or relocation decisions, understanding regional differences is crucial — especially in high-demand technical roles where US-based positions carry a significant premium.

---

## 3️⃣ What are the top skills of data professionals?

### 💪 Skill: Power Pivot

I created a Data Model by linking `data_jobs_all` and `data_job_skills` through the `job_id` column. This relationship, built in Power Pivot, allows cross-table analysis without needing lookup formulas.

### 📊 Analysis

#### 💡 Insights

- SQL and Python are the most frequently requested skills across data roles, confirming their foundational importance.
- Cloud skills (AWS, Azure) appear consistently across job types, reflecting the industry's continued shift toward cloud infrastructure.
- For Data Engineer roles specifically, tools like Kafka, Hadoop, and NoSQL are prominent alongside core languages.

#### 🤔 So What

For anyone entering or growing in the data field, SQL and Python are non-negotiable starting points. Cloud platform knowledge is increasingly expected even outside engineering roles.

---

## 4️⃣ What's the pay for the top 10 skills?

### 📈 Skill: Advanced Charts (Combo PivotChart)

I built a combo PivotChart plotting both median salary and skill likelihood (%) on the same chart:

- **Primary axis:** Median Salary (Clustered Column)
- **Secondary axis:** Skill Likelihood (Line with diamond markers)

### 📊 Analysis

#### 💡 Insights

- Python leads with a median salary of $98,500 and a skill likelihood of ~29% — high demand and high pay.
- SQL has the highest likelihood (~52%) confirming it as the most common skill, with a median salary of $92,500.
- Oracle commands a $95,000 median salary despite lower likelihood (~6.5%), suggesting it's a niche but well-compensated skill.
- Presentation tools like PowerPoint and Word show the lowest salaries and likelihood among the top 10.

#### 🤔 So What

Focusing on Python and SQL gives the best combination of demand and pay. Niche skills like Oracle can also be worth pursuing for those targeting specific high-paying industries.

---

## Conclusion

This project gave me a clearer picture of how skills, location, and job type influence salary in the data field. Using Power Query, Power Pivot, DAX, and advanced charting in Excel, I was able to move from raw job data to meaningful insights — all without writing a single line of code outside of DAX. The analysis confirms that technical skills like Python, SQL, and cloud platforms are the most valuable investments for anyone looking to grow their career and earning potential in data.
