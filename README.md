# CodeAlpha_hr_analytics_dashboard
Data-driven HR Analytics Dashboard built with Power BI &amp; DAX to uncover workforce attrition patterns and provide strategic retention recommendations.
# 📊 HR Analytics Dashboard

## 📌 Project Overview
This repository contains a comprehensive, production-grade **2-Page Power BI Dashboard** designed for workforce analytics and talent management. It analyzes employee retention, attrition drivers, salary distribution, overtime impact, and organizational demographics.

This project goes beyond simple visual metrics to build a **data-driven business narrative (Storytelling)** that links employee turnover trends (**Attrition Rate: 16.12%**), job roles, and work-life balance factors to recommend strategic actions for executive leadership and HR managers.

---

## 🛠️ Tech Stack & Key Skills
* **BI Platform:** Power BI Desktop
* **Data Transformation:** Power Query (ETL, Data Cleaning, Custom Binning for Age Groups)
* **Data Modeling & Calculations:** DAX (Data Analysis Expressions) for custom KPI measures
* **Features Used:** Synced Slicers, Custom Page Navigation, Custom Color Palette (`#582C58` Theme), Native KPI Cards, Interactive Cross-Filtering.
* **Analysis Concepts:** HR Analytics, Employee Churn Analysis, Retention Strategy, Compensation & Workload Profiling.

---

## 📖 The Business Narrative (Storytelling & Insights)

### 👥 Chapter 1: HR Overview (Workforce Baseline & Attrition Dynamics)
* **Performance Baseline:** Analyzed an organization of **1,470 total employees**, maintaining **1,233 active staff** with an average age of **36.92 years** and an average tenure of **7.01 years**.
* **Attrition Baseline:** Logged a total of **237 employee departures**, resulting in an overall **Attrition Rate of 16.12%**.
* **Age Group & Overtime Exposure (Primary Turnover Driver):**
  * The **25–34 age group** experiences the highest absolute count of resignations.
  * *The OverTime Link:* Across almost every age bracket, employees required to work **OverTime** exhibit a significantly higher rate of leaving compared to non-overtime staff, pointing directly to burnout and work-life balance tension.
* **Travel Frequency & Education Field Distribution:**
  * The vast majority of departing staff hold degrees in **Life Sciences (37.55%)** and **Medical (26.58%)**.
  * Employees categorized under **Travel_Rarely** account for 65.82% of attrition count, though frequent travelers (**Travel_Frequently**) show higher relative risk.

![Dashboard Page 1](hr1.jpeg)

### 💼 Chapter 2: Employee Insights (Compensation & Job Role Risk)
* **Job Role Attrition & Compensation Disparity:**
  * **Sales Representatives** experience the most critical turnover rate (**39.76%**), driven by entry-level compensation baseline and high target stress.
  * **Laboratory Technicians** and **Human Resources** staff also display elevated attrition rates (~20-25%).
  * *The Executive Contrast:* Executive and leadership roles (**Managers**, **Research Directors**) show minimal attrition (<5%) due to high average monthly income ($15K–$20K) and career stability.
* **Tenure Vulnerability (The Onboarding Gap):**
  * The line analysis of **Attrition Count by YearsAtCompany** reveals a massive spike in departures during the **first 1–3 years** (peaking at Year 1). Once an employee passes the 3-year mark, attrition probability drops sharply.
  * *Strategic Action:* HR must overhaul the 30-60-90 day onboarding and mentorship program to support early-stage employee retention.

![Dashboard Page 2](hr2.jpeg)

---

## 💻 Technical Implementation, DAX & Data Engineering

To ensure high performance and precise dynamic aggregations, custom **DAX measures** and **Power Query transformations** were built.

### 📐 Key DAX Measures & Calculated Columns

#### 1. Attrition Rate Measure
Calculates the exact percentage of employees who have left the company relative to the total headcount:
```dax
Attrition Rate = 
DIVIDE(
    [Attrition Count], 
    [Total Employees], 
    0
)
```
#### 2. Active Employees Count
Dynamically computes the remaining workforce currently active in the organization:
```dax
Active Employees = 
CALCULATE(
    COUNT('HR_Data'[EmployeeNumber]), 
    'HR_Data'[Attrition] = "No"
)
```
#### 3. Average Monthly Income
Used to evaluate compensation baselines across different job roles and department hierarchies:
```dax
Avg Monthly Income = AVERAGE('HR_Data'[MonthlyIncome])
```
#### 4. Average Job Satisfaction Score
Evaluates the organizational satisfaction metric on a 1–4 standardized scale:
```dax
Avg Job Satisfaction = AVERAGE('HR_Data'[JobSatisfaction])
```
## 📦 Data Grouping & Transformation (Power Query)

  Age Demographic Binning: Transformed continuous age data into structured age brackets (Under 25, 25-34, 35-44, 45-54, 55+) to isolate generational turnover trends.

  Conditional Formatting & Page Navigation: Configured interactive page navigation buttons with active (Selected) and passive state color transitions to deliver an intuitive user experience.

## 💡 Strategic Recommendations for Executive Leadership

  Overtime Workload Redistribution: Re-evaluate staffing levels for teams with high overtime requirements to mitigate burnout-induced resignations.

  Sales Rep Retention Plan: Redesign commission structures and entry-level career progression maps for Sales Representatives to combat the 39.76% attrition spike.

  Early-Tenure Mentorship: Implement structured check-ins during the first 12 months of employment to flatten the high 1st-year departure spike.
