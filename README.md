# 📊 Subscription Churn Analysis

A end-to-end data analysis project exploring customer churn patterns, cohort retention, and revenue impact for a subscription-based business.

---

## 🔍 Project Overview

This project analyzes **3,069 subscription customer records** to answer key business questions around churn, retention, and payment behavior. The full pipeline covers data cleaning in Python, exploratory data analysis, and an interactive Power BI dashboard.

### Key Findings
- **65.30% churn rate** — nearly 2 in 3 customers have cancelled
- **August 2023** was the peak churn month with 203 cancellations
- **2023 cohort** churned fastest — 446 customers cancelled within their first month
- **95.67% of subscriptions were paid** — payment is not the driver of churn

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Python (Pandas, Matplotlib) | Data cleaning & EDA |
| Jupyter Notebook | Analysis environment |
| Power BI Desktop | Dashboard & visualization |
| Claude (Anthropic) | Analysis guidance & documentation |

---

## 📓 Notebook Summary

The Jupyter notebook covers:

1. **Loading data** — raw CSV files into Pandas DataFrames
2. **Null inspection** — identifying 1,065 missing `canceled_date` values (active customers)
3. **Date conversion** — converting string columns to `datetime64`
4. **Feature engineering** — creating derived columns:
   - `subscription_duration_days`
   - `is_churned`
   - `status` (Active / Cancelled)
   - `cohort_month`
5. **EDA** — visualizing churn distribution, payment status, duration histogram, and monthly churn trend
6. **Export** — saving cleaned data as CSV for Power BI

---

## 📊 Dashboard

The Power BI dashboard includes:

- **KPI Cards** — Total Customers, Active %, Churn %, Revenue Collected
- **Bar Chart** — Churn % by Quarter and Year
- **Line Chart** — Monthly Churn Trend
- **Matrix Heatmap** — Cohort Retention (cohort month × months to churn)
- **Donut Chart** — Paid vs Unpaid Subscriptions
- **Scatter Plot** — Subscription Duration vs Cost by Churn Status
- **Slicer** — Filter by Cohort Month



---

## 📄 Documentation

| File | Description |
|------|-------------|
| `stakeholder_briefing.md` | Original project brief and business questions |
| `subscription_cohort_reference.pdf` | Full reference guide — cleaning steps, DAX measures, visual setup |
| `subscription_churn_findings.pdf` | Executive summary of key findings and recommendations |

---

## 🚀 How to Run

1. Clone the repository
2. Open `notebook/Subscription.ipynb` in Jupyter
3. Place the raw CSV files in the same directory or update the file paths
4. Run all cells — `cleaned_subscriptions.csv` will be generated
5. Open `dashboard/Subscription Analysis.pbix` in Power BI Desktop
6. Update the data source path to point to your local `cleaned_subscriptions.csv`

---

## 📬 Contact

Feel free to connect or reach out if you have any feedback on this project!
