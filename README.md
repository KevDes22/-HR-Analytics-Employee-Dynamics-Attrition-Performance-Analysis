# -HR-Analytics-Employee-Dynamics-Attrition-Performance-Analysis

> **Tools Used:** Power BI · Data Modeling (Star Schema) · DAX · HRIS Data  
> **Domain:** Human Resources Analytics  
> **Dashboard Pages:** Employee Segmentation | Attrition & Performance  

---

## Table of Contents

1. [Introduction](#introduction)
2. [Problem Statement](#problem-statement)
3. [Methodology](#methodology)
4. [Results & Insights](#results--insights)
5. [Recommendations](#recommendations)
6. [Conclusion](#conclusion)

---

## Introduction

In today's competitive talent landscape, organizations can no longer afford to make people decisions based on intuition alone. Human capital is among the most strategic — and expensive — assets a company manages, and understanding the behavioral and operational patterns within a workforce is essential to sustaining growth and stability.

This project presents a comprehensive HR analytics solution built in **Power BI**, designed to help business leaders and HR professionals answer critical questions:

- Who makes up our workforce, and how is it distributed?
- Why are employees leaving, and which roles are most at risk?
- Are our training programs actually improving performance?
- Is compensation being distributed fairly across demographic groups?

The analysis spans two interactive dashboards:

| Dashboard | Focus |
|-----------|-------|
| **Employee Segmentation Analysis** | Demographics, compensation, geography, and gender distribution |
| **Employee Attrition Rate & Performance** | Turnover drivers, training impact, pay equity, and rating alignment |

---

## Problem Statement

The organization is operating with a **16.12% attrition rate** across a workforce of **1,470 employees (1.47K)**. While not immediately alarming, this rate signals structural challenges that — if unaddressed — will compound over time through rising recruitment costs, lost institutional knowledge, and declining team morale.

Three core problems are identified:

### 🔴 1. High Turnover in Frontline and Specialized Roles
Roles such as **Sales Representatives** and **Recruiters** are experiencing attrition rates approaching or exceeding **40%**. These are operationally critical positions, and their constant churn creates a revolving door that strains the organization's ability to build lasting client relationships or maintain internal hiring pipelines.

### 🟡 2. Inconsistent Return on Training Investment
Not all departments are deriving equal value from employee training programs. The **HR department** shows a **decline** in performance ratings following training cycles, while the **Technology department** exhibits a steady, positive trajectory. This disparity suggests that training content or delivery methods are misaligned with departmental needs in certain areas.

### 🟡 3. Performance Expectation Misalignment
A visible gap exists between **employee self-ratings** and **manager-assigned ratings**. Many employees rate their own performance at **4 or 5**, while managers frequently assign **3**. This disconnect can erode trust, reduce engagement, and undermine the credibility of performance review processes.

---

## Methodology

To ensure the analysis was both accurate and actionable, a structured four-stage process was followed:

### Stage 1 — Data Collection
Data was aggregated from HRIS systems, capturing multi-dimensional employee attributes across the following categories:

- **Demographics:** Age, Gender, Ethnicity, Location (State)
- **Compensation:** Average salary by job role and ethnicity
- **Performance:** Self-ratings vs. manager ratings; training frequency
- **Operational:** Distance from home (KM), Work-Life Balance scores, department affiliation

### Stage 2 — Data Cleaning & Transformation
Raw data was standardized and validated to ensure analytical integrity:

- **Age Grouping:** Employees were categorized into three cohorts — `Young Adult`, `Adult`, and `Aged Adult` — for segmentation analysis
- **Missing Value Handling:** Null and incomplete records were identified and treated appropriately to avoid skewing aggregated metrics
- **Categorical Normalization:** Inconsistent string labels across categorical fields were unified for accurate grouping and filtering

### Stage 3 — Data Modeling
A **Star Schema** was implemented as the underlying data architecture to enable efficient querying and granular slicing:

```
                    ┌──────────────────┐
                    │  PerformanceRating│  ← Fact Table
                    │  (Central Table)  │
                    └────────┬─────────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
   ┌──────┴──────┐   ┌───────┴──────┐   ┌──────┴──────┐
   │  Employee   │   │ EducationLevel│   │ RatingLevel │
   │  (Dimension)│   │  (Dimension)  │   │ (Dimension) │
   └─────────────┘   └──────────────┘   └─────────────┘
                             │
                    ┌────────┴────────┐
                    │  SatisfiedLevel  │
                    │  (Dimension)     │
                    └─────────────────┘
```

**Relationships:** All dimension tables connect to the Fact Table via **1-to-Many (1:N)** relationships, allowing for dynamic filtering across multiple analytical dimensions simultaneously.

### Stage 4 — Visualization & Dashboard Design
Two Power BI dashboards were developed with the following visual components:

| Visual Type | Purpose |
|-------------|---------|
| Horizontal Bar Chart | Average salary by job role |
| Clustered Bar Chart | Age group distribution; department headcount |
| Pie Chart | Gender distribution breakdown |
| Geospatial Map | Employee geographic concentration |
| Line Chart | Training impact on performance over time by department |
| Scatter Plot | Attrition rate vs. distance from home (by gender) |
| Ribbon Chart | Salary fairness across ethnic groups |
| Dot Plot | Self-rating vs. manager rating correlation |
| KPI Cards | Total employees; overall attrition rate |

---

## Results & Insights

### 📌 A. Employee Segmentation & Demographics

**Workforce Composition**

The workforce skews toward younger demographics. The **Young Adult** and **Adult** cohorts represent the largest age groups, while the **Aged Adult** segment is notably smaller. This distribution suggests the organization has a talent pipeline that is relatively early in career stages, which can be an asset for adaptability but also a risk factor for higher voluntary turnover due to career mobility at younger ages.

**Departmental Breakdown**

| Department | Employee Count |
|------------|---------------|
| Technology | Highest |
| Sales | Moderate |
| Human Resources | Lowest |

The **Technology department** anchors the organization's headcount, reflecting a tech-centric operational model.

**Geographic Distribution**

Employee concentration is highest in **California (CA)**, with secondary clusters in **New York (NY)** and **Illinois (IL)**. This coastal and urban bias has implications for compensation benchmarking, given the higher cost of living in these markets.

**Gender Distribution**

| Gender | Percentage |
|--------|-----------|
| Female | 45.92% |
| Male | 44.29% |
| Non-Binary | 8.44% |
| Prefer Not to Say | 8.44% |

Gender representation is near-parity between Female and Male employees, which is a positive indicator of inclusive hiring practices.

---

### 📌 B. Attrition Drivers

**Role Vulnerability**

The roles with the highest attrition rates are:

1. **Sales Representative** — ~40%+ attrition
2. **Recruiter** — ~40% attrition

These two roles share common characteristics: high-pressure targets, performance-based compensation structures, and significant external market competition for their skill sets. Their turnover significantly inflates the overall 16.12% organizational attrition figure.

**Commute Distance & Attrition**

The scatter plot analysis reveals a meaningful pattern: **attrition spikes when average employee commute distance exceeds 22–23 KM**, with the effect being more pronounced among **male employees**. Longer commutes correlate with reduced work-life quality and higher disengagement, making proximity to the office a hidden retention variable.

**Work-Life Balance**

The average Work-Life Balance score across all departments hovers around **3.40 out of 5**:

| Department | Avg. Work-Life Balance |
|------------|----------------------|
| Technology | 3.42 |
| Sales | 3.40 |
| Human Resources | 3.38 |

While the differences across departments are minor, the overall score is **mediocre**. A score below 3.5 in a workforce dominated by young adults — who increasingly prioritize flexibility — represents a latent retention risk.

---

### 📌 C. Performance & Compensation

**Training Efficacy by Department**

The line chart tracking training frequency against subsequent performance ratings surfaces a significant divergence:

- **Technology:** Performance ratings show a **positive, upward trend** as training intervals increase — indicating that training content is relevant and well-aligned with job demands.
- **HR Department:** Performance ratings **decline** following training cycles — a counterintuitive result suggesting either that training programs are poorly matched to HR-specific competencies, or that other confounding factors (e.g., job stress, role changes) are diminishing their effect.
- **Sales:** Performance trends remain relatively **flat**, indicating a neutral training impact.

**Self-Rating vs. Manager Rating Gap**

| Self-Rating (Employee) | Manager Rating | Gap |
|------------------------|---------------|-----|
| Predominantly 4–5 | Predominantly 3 | ~1–2 points |

This consistent overestimation in self-assessment is a well-documented organizational behavior challenge. Without structured calibration, this misalignment leads to dissatisfaction during review cycles and may be contributing to voluntary attrition in high-performing self-assessed employees who feel undervalued.

**Pay Equity Across Ethnicity**

The ribbon chart visualizing average salary across ethnic groups — segmented by gender — shows **fluctuations in compensation** across:

- White
- Black or African American
- American Indian
- Asian or Pacific Islander
- Mixed Origin
- Native
- Other

The variation in average salary across these groups suggests that pay equity has not been systematically enforced, and warrants a formal **pay-equity audit** to identify and remediate any unjustified disparities.

---

## Recommendations

Based on the findings above, the following strategic actions are recommended, prioritized by potential business impact:

### ✅ 1. Targeted Retention Programs for High-Risk Roles
**Priority: High | Timeline: 0–3 Months**

Implement structured retention initiatives for **Sales Representatives** and **Recruiters**:
- Conduct **Stay Interviews** to proactively surface dissatisfaction before it leads to resignation
- Introduce **retention bonuses** tied to 12-month tenure milestones
- Review compensation benchmarking against industry data for these specific roles

### ✅ 2. Hybrid Work & Commute Mitigation Policy
**Priority: High | Timeline: 1–3 Months**

For employees commuting more than **20 KM**, introduce flexible policies:
- Offer **hybrid work schedules** (2–3 days remote per week)
- Consider **commute subsidies** or pre-tax transportation benefits
- Use commute data during onboarding to flag high-risk hires early

### ✅ 3. Performance Calibration Workshops
**Priority: Medium | Timeline: 3–6 Months**

Bridge the self-rating vs. manager-rating gap through structured alignment:
- Launch **"Manager-Employee Alignment"** workshops before each review cycle
- Introduce shared **behavioral performance rubrics** so expectations are transparent and consistent
- Train managers on effective feedback delivery to reduce the perception of unfair ratings

### ✅ 4. HR Training Program Audit
**Priority: Medium | Timeline: 3–6 Months**

The current HR training curriculum is producing negative performance outcomes:
- Conduct a **root cause analysis** of training content relevance and delivery modality
- Benchmark HR training programs against external best practices
- Pilot revised training modules and track performance rating trends over two review cycles

### ✅ 5. Formal Pay Equity Audit
**Priority: Medium-High | Timeline: 3–6 Months**

Salary fluctuations across ethnic groups represent both a fairness concern and a legal risk:
- Engage HR and Finance leadership to conduct a **structured pay equity analysis** controlling for role, seniority, and performance
- Establish a **salary band framework** to standardize compensation within job levels
- Communicate findings and remediation steps transparently to build organizational trust

---

## Conclusion

This HR analytics project demonstrates how structured data analysis can surface non-obvious drivers of workforce instability and help organizations make proactive, evidence-based people decisions.

The organization's **16.12% attrition rate** is currently manageable but is trending toward systemic risk — particularly in Sales and Recruiting functions. The data points to a combination of **commute friction**, **unresolved performance expectation gaps**, and **training misalignment** as the primary contributors to turnover and engagement challenges.

The **Technology department** stands out as a model of positive training impact and stable performance, offering internal best practices that can potentially be adapted across other functions.

By acting on the five prioritized recommendations above, the organization can expect to:
- Reduce attrition in high-risk roles by addressing the root-cause retention levers
- Improve performance review satisfaction through better calibration
- Strengthen organizational trust through pay equity transparency
- Maximize ROI on training investment through curriculum realignment

---

## Dashboard Previews

### Page 1 — Employee Segmentation Analysis
![Employee Segmentation Dashboard](https://github.com/KevDes22/-HR-Analytics-Employee-Dynamics-Attrition-Performance-Analysis/blob/main/Screenshot%202026-03-06%20202119.png)

### Page 2 — Attrition Rate & Performance
![Attrition & Performance Dashboard](https://github.com/KevDes22/-HR-Analytics-Employee-Dynamics-Attrition-Performance-Analysis/blob/main/Screenshot%202026-03-06%20202136.png)
---



## About the Analyst

This project was developed as part of a data analytics portfolio, with a focus on translating raw HR data into strategic business intelligence. The analysis demonstrates proficiency in:

- **Power BI** dashboard development and DAX measures
- **Data modeling** using Star Schema architecture
- **HR domain knowledge** — attrition analysis, compensation equity, and performance management
- **Stakeholder-ready storytelling** — translating data into executive-level insights and actionable recommendations

---

*📁 Feel free to explore the `.pbix` file, raise issues, or connect on [LinkedIn](https://www.linkedin.com/in/destiny-kevin-0015861a4/) if you'd like to discuss the methodology or findings.*
