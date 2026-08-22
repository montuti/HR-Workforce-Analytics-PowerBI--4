# HR-Workforce-Analytics-PowerBI--4
Interactive HR Workforce Analytics Dashboard built in Power BI with 25+ DAX measures — attrition, compensation, performance, training ROI, and hiring trends across a modeled star schema with active/inactive date relationships and full Time Intelligence.
# HR Workforce Analytics — Power BI (PR4)

> An end-to-end HR analytics dashboard built in Power BI, analyzing workforce composition, attrition, compensation, performance, training, and recruitment using a dimensional Star Schema model and custom DAX measures.

**Institute:** Red & White Skill Education
**Subject:** Power BI
**Project:** Practical Report 4 (PR4)
**Dataset:** Employee / HR Dataset — All in One (Project Dataset)

---

## Table of Contents

- [Objectives](#objectives)
- [Data Model](#data-model)
- [Dashboard Pages](#dashboard-pages)
- [Key DAX Measures](#key-dax-measures)
- [Tools & Technologies](#tools--technologies)
- [Project Deliverables](#project-deliverables)
- [Validation Checklist](#validation-checklist)
- [Screenshots](#screenshots)
- [Video Walkthrough](#video-walkthrough)
- [Repository Structure](#repository-structure)
- [How to Use This Project](#how-to-use-this-project)

---

## Objectives

- Analyze total and active workforce across the organization.
- Understand employee attrition patterns and trends over time.
- Analyze salary and compensation distribution by department.
- Compare employee performance across teams and career levels.
- Analyze training investment and cost by department.
- Explore recruitment pipeline and hiring velocity.
- Demonstrate applied DAX concepts, including `CALCULATE`, `ALL`, `ALLEXCEPT`, `FILTER`, `RANKX`, and Time Intelligence functions.

---

## Data Model

The Power BI model follows a **Star Schema** design, separating descriptive dimensions from measurable facts for clean, performant DAX evaluation.

### Dimension Tables

| Table | Purpose |
|---|---|
| `DimDate` | Central date table for time intelligence (marked as Date Table) |
| `DimEmployee` | Employee attributes (name, gender, tenure, career level, etc.) |
| `DimDepartment` | Department names and hierarchy |
| `DimJobLevel` | Job/career level bands |
| `DimLocation` | Employee work location |

### Fact Tables

| Table | Purpose |
|---|---|
| `FactWorkforce` | Headcount and workforce composition records |
| `FactAttrition` | Termination and attrition events |
| `FactCompensation` | Salary and compensation records |
| `FactPerformance` | Performance ratings by review cycle |
| `FactRecruitment` | Recruitment pipeline and hiring data |
| `FactTraining` | Training programs, cost, and completion data |

### Measures Table

- `_Measures` — a dedicated, disconnected table used to organize all DAX measures cleanly, separate from data tables.

**Relationship notes:**
- `DateOfJoining` relationship to `DimDate` is **active** (drives hiring time intelligence).
- `DateOfTermination` relationship to `DimDate` is **inactive** by default, activated via `USERELATIONSHIP()` for attrition-specific time intelligence.
- `FactRecruitment` remains standalone where no `Employee ID` exists yet (pre-hire candidates).

---

## Dashboard Pages

### 1. Workforce Overview

The landing page, summarizing overall workforce health at a glance.

**KPI Cards:**
- Total Employees
- Active Employees
- Attrition Rate
- Average Salary
- High Performers %
- Avg Tenure (Yrs)
- Training Investment
- Female %

**Core Visuals:**
- Active Headcount by Department (bar chart)
- Workforce by Career Level Band (donut/bar chart)

**Slicers:** Year · Department · Career Level

---

### 2. Attrition Analysis

Focused on employee exits, hiring trends, and turnover patterns.

**Planned Visuals:**
- Attrition Rate (KPI)
- Terminated Count (KPI)
- Attrition Rate YTD (KPI)
- New Hires YoY % (KPI)
- Annual Hiring vs. Same Period Last Year (comparison chart)
- Year-to-Date New Hires by Month (line/column chart)
- Attrition Rate by Department (bar chart)

---

### 3. Compensation

Focused on salary distribution and training spend.

**Visuals:**
- Average Salary by Department (bar chart)
- Department Salary & Performance Ranking (ranked table/matrix)
- Above/Below Average Salary (variance indicator)
- Training Cost by Department (bar chart)

**Slicers:** Career Level · Salary Band

---

## Key DAX Measures

Organized by analytical theme:

**Headcount & Tenure**
- `Total_Headcount`
- `Active_Headcount`
- `Terminated_Count`
- `Avg_Tenure`
- `Distinct_Departments`

**Compensation**
- `Avg_Salary`
- `Total_Salary_Cost`
- `Dept_Avg_Salary_AEXCEPT`
- `Salary_Rank_Dept`

**Performance**
- `Avg_Performance_Rating`
- `High_Performers_Count`
- `High_Performer_%`
- `Senior_Headcount`

**Attrition & Diversity**
- `Attrition_Rate_%`
- `Attrition_Rate_YTD`
- `Gender_Diversity_Ratio`
- `Bench_Utilisation_%`

**Training**
- `Avg_Training_Cost`
- `Total_Training_Cost`
- `Training_Cost_Rank`

**Headcount Share**
- `Total_HC_All_Depts`
- `Headcount_%_of_Total`

**Recruitment / Time Intelligence**
- `YTD_New_Hires`
- `New_Hires_SPLY` (Same Period Last Year)
- `New_Hires_YoY_%`
- `Hires_Prior_3M`

---

## Tools & Technologies

- Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query (data cleaning & shaping)
- CSV data sources
- GitHub (version control & documentation)

---

## Project Deliverables

- [ ] Power BI `.pbix` file
- [ ] Dataset CSV files
- [ ] Dashboard screenshots
- [ ] Model View screenshot
- [ ] Measures documentation
- [ ] Recorded explanation video
- [ ] GitHub README

---

## Validation Checklist

Before final submission, verify the following:

- [ ] `Active Headcount + Terminated Count = Total Headcount`
- [ ] `DimDate` is marked as a Date Table
- [ ] `DateOfJoining` relationship is active
- [ ] `DateOfTermination` relationship is inactive (used only via `USERELATIONSHIP` for attrition time intelligence)
- [ ] Employee-related fact tables have correct, validated relationships
- [ ] `FactRecruitment` remains standalone where Employee ID is not available
- [ ] Percentage measures use percentage formatting
- [ ] Salary measures use currency formatting
- [ ] All three report pages are complete and consistently formatted (fonts, colors, alignment)

---

## Screenshots

> Add project screenshots to the `Screenshots` folder and update the paths below.

| Page | Preview |
|---|---|
| Workforce Overview | `Screenshots/workforce-overview.png` |
| Attrition Analysis | `Screenshots/attrition-analysis.png` |
| Compensation | `Screenshots/compensation.png` |
| Model View | `Screenshots/model-view.png` |

---
<img width="1895" height="918" alt="Screenshot 2026-08-19 134622" src="https://github.com/user-attachments/assets/84158d04-f250-4193-8fd9-f758b54dc882" />
<img width="1887" height="949" alt="Screenshot 2026-08-19 134647" src="https://github.com/user-attachments/assets/1b9737ea-03a8-484a-9052-fa3eeca43fb5" />
<img width="1346" height="730" alt="Screenshot 2026-08-22 160802" src="https://github.com/user-attachments/assets/252e39d7-28f3-444c-8e00-15776c9ec030" />
<img width="1289" height="724" alt="Screenshot 2026-08-22 160827" src="https://github.com/user-attachments/assets/9685a585-2462-457d-975b-cabf17ed72d0" />
<img width="1283" height="724" alt="Screenshot 2026-08-22 160843" src="https://github.com/user-attachments/assets/dbc48bcf-f97e-492a-bea6-d51777c14698" />

## Video Walkthrough

**Video Link:** `[Add Google Drive or YouTube Unlisted Link]`

---

## Repository Structure

```text
PR4_HR_Analytics/
│
├── PR4_HR_Analytics.pbix
├── Dataset/
│   ├── employee_data.csv
│   ├── training_and_development_data.csv
│   ├── employee_engagement_survey_data.csv
│   ├── performance_data.csv
│   └── recruitment_data.csv
│
├── Screenshots/
│   ├── workforce-overview.png
│   ├── attrition-analysis.png
│   ├── compensation.png
│   └── model-view.png
│
└── README.md
```

---

## How to Use This Project

1. Clone or download this repository.
2. Open `PR4_HR_Analytics.pbix` in Power BI Desktop.
3. If prompted, update the data source path to point to the `Dataset/` folder on your machine.
4. Refresh the data model (`Home → Refresh`).
5. Explore the three report pages using the slicers to filter by year, department, and career level.
