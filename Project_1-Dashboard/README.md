# 📊 Excel Salary Dashboard

## Introduction

This salary dashboard was built to help anyone in the data field explore job salaries based on their desired role, location, and employment type — making it easier to understand what fair compensation looks like in the current market.

The dataset used comes from Luke Barousse's Excel course and contains real-world data science job postings from 2023. Throughout this project I applied and practiced core Excel skills on a dataset of over 32,000 job listings.

### Dashboard File

My final dashboard: [1_Salary_Dashboard.xlsx](1_Salary_Dashboard.xlsx)

---

## Excel Skills Used

- **📉 Charts**
- **🧮 Formulas and Functions**
- **❎ Data Validation**

---

## Dataset

The dataset contains real job postings from 2023, with information on:

- **👨‍💼 Job titles** (Data Analyst, Data Engineer, Data Scientist, etc.)
- **💰 Salaries** (annual and hourly)
- **📍 Locations** (country-level)
- **🛠️ Required skills**
- **🏢 Job platforms** (LinkedIn, Indeed, ZipRecruiter, etc.)
- **⏱️ Schedule types** (Full-time, Part-time, Contractor, etc.)

---

## Dashboard Build

### 📉 Charts

#### 📊 Median Salary by Job Title — Bar Chart

- **Excel feature used:** Horizontal bar chart with formatted salary values
- **Design choice:** Jobs sorted by descending median salary for easy comparison
- **Insight:** Senior and Engineer roles consistently pay more than Analyst roles

#### 🗺️ Median Salary by Country — Map Chart

- **Excel feature used:** Excel's built-in map chart
- **Design choice:** Color-coded by salary range to highlight geographic differences
- **Insight:** Significant salary disparities exist globally, with the US leading in compensation

---

### 🧮 Formulas and Functions

#### 💰 Median Salary by Job Title

```excel
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

This array formula filters the dataset by job title, country, and schedule type simultaneously, then returns the median salary. It powers the background Jobs table which feeds the bar chart.

#### 🔢 Unique Job Schedule Types

```excel
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

This formula generates a clean list of unique schedule types by filtering out combined entries (e.g. "Full-time and Part-time") and empty values. The result is used as the data validation source for the Type dropdown.

#### 🏢 Job Count by Platform

```excel
=COUNTIFS(jobs[job_via],A2,jobs[job_title_short],title,jobs[job_country],country,jobs[job_schedule_type],type)
```

Counts job postings per platform filtered by the current dashboard selections — giving users a sense of where to look for their target role.

---

### ❎ Data Validation

The dashboard includes three dropdown filters — **Job Title**, **Country**, and **Type** — each powered by validated lists built from the dataset.

- User input is restricted to valid options only
- Prevents inconsistent or incorrect entries
- Updates all charts and metrics dynamically when selections change

---

## Conclusion

This project helped me put Excel's core features into practice on a real-world dataset. Building the dashboard from scratch — from raw job data to an interactive tool with dynamic charts, multi-criteria formulas, and validated dropdowns — gave me a solid understanding of how Excel can be used for data analysis and visualization.
