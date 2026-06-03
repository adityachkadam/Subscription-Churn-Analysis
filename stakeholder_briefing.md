# Stakeholder Briefing — Subscription Cohort Analysis

**From:** Head of Revenue & Customer Success  
**To:** Data Analyst  
**Date:** June 2, 2026  
**Re:** Subscription Churn & Cohort Performance Analysis  

---

## Background

We have been experiencing subscriber losses over recent quarters and currently lack a clear, data-driven picture of *why* customers are leaving and *when* they tend to churn. We have transactional subscription data for **3,069 customers** and need it turned into actionable insights.

---

## Problem Statement

> **We need to understand our subscription churn patterns, identify revenue leakage, and evaluate cohort-level retention so that we can make informed decisions to reduce churn and improve payment collection.**

---

## Key Business Questions

### 1. Churn Analysis
- What is the **overall churn rate** across all customers?
- Among the ~1,065 customers with no `canceled_date` (presumably still active), how does churn vary?
- How does churn differ across **subscription intervals** (e.g., monthly vs. annual)?

### 2. Revenue Impact
- How much **revenue was collected vs. lost** due to unpaid or canceled subscriptions?
- What is the relationship between `was_subscription_paid` and churn behavior?
- Are non-paying customers more likely to cancel early?

### 3. Cohort Retention Analysis
- Using `created_date`, group customers into **monthly cohorts**.
- For each cohort, how long do customers stay subscribed before canceling?
- Are **newer cohorts churning faster** than older ones?

### 4. Payment Behavior
- What proportion of subscriptions were **not paid**?
- Does non-payment correlate with early cancellation?
- Are certain subscription intervals more prone to payment failure?

---

## Recommended Workflow

### Step 1 — Data Cleaning (Jupyter Notebook)
- Convert `created_date` and `canceled_date` from `object` to proper `datetime` format
- Handle nulls in `canceled_date` — treat as **still active** customers
- Engineer the following derived columns:
  - `is_churned` → Boolean flag (True if `canceled_date` is not null)
  - `subscription_duration_days` → Days between `created_date` and `canceled_date`
  - `cohort_month` → Month extracted from `created_date` (for grouping)
  - `months_to_churn` → Duration expressed in months (for cohort table)

### Step 2 — Export Cleaned Data
- Save cleaned dataframe as `cleaned_subscriptions.csv`
- This file will serve as the single source of truth for Power BI

### Step 3 — Power BI Dashboard
Load `cleaned_subscriptions.csv` into Power BI and build the following visuals:

| Visual | Description |
|--------|-------------|
| KPI Cards | Total customers, active %, churned %, revenue collected |
| Bar Chart | Churn rate by Cohort Month |
| Line Chart | Churned Count by Cancelled Date(Month) |
| Cohort Heatmap | Retention rate by cohort month |
| Pie/Donut Chart | Paid vs. unpaid subscriptions |
| Scatter Plot | Subscription duration vs. cost, colored by churn status |

---

## Deliverables Expected

1. **Jupyter Notebook** — Well-commented, covering data cleaning and brief EDA
2. **`cleaned_subscriptions.csv`** — Cleaned and enriched dataset
3. **Power BI Dashboard** — Minimum 4 visuals with filters/slicers
4. **Summary Section** (at the end of the notebook or a separate doc) — Key findings in plain language

---

## Notes & Assumptions

- Customers with a `null` value in `canceled_date` are to be treated as **currently active**.
- All revenue figures should use `subscription_cost` as the basis.
- `was_subscription_paid` should be treated as a categorical variable — verify its unique values before analysis.
- Data dictionary (`df1`) should be referenced throughout to ensure correct interpretation of fields.

---

*Any questions or blockers? Flag them early so we can align before final delivery.*
