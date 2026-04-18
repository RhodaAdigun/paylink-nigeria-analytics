# PayLink Nigeria — Customer Retention & Revenue Analysis

## Overview
PayLink Nigeria is a fictional Nigerian digital payment platform that allows users to send 
money, pay bills, and make purchases from online vendors. Despite strong user acquisition, 
the platform struggles with retention — many users register but become inactive shortly after.

This project analyzes 1,000 simulated user and transaction records to identify behavioral 
patterns behind customer churn, uncover high-value segments, and provide actionable 
recommendations to improve retention and grow revenue.


## Business Problem

> *"Although PayLink Nigeria continues to attract new users, many customers become inactive 
> after signing up. This leads to lower transaction activity and slower revenue growth."*

Without understanding why users disengage, the business cannot improve retention or 
sustainably grow revenue.


## Project Objectives
- Analyze customer transaction patterns to understand platform interaction
- Identify trends in user activity and retention over time
- Determine which customer segments generate the highest revenue
- Build an interactive Power BI dashboard showing key business metrics
- Provide data-driven recommendations to improve engagement and revenue


## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (Jupyter Notebook) | Synthetic dataset generation |
| MySQL | Data analysis and querying |
| Power BI | Interactive dashboard and visualization |
| Pandas, Faker | Data simulation libraries |


## Dataset

The dataset was synthetically generated using Python's `Faker` library and `random` module 
to simulate realistic Nigerian fintech user behavior.

**1,000 users | 9 columns | 5 years of registration data (2021–2026)**

| Column | Description |
|---|---|
| `User_ID` | Unique identifier (PLN-0001 to PLN-1000) |
| `Registration_Date` | Date user joined the platform |
| `Last_Active_Date` | Date of most recent transaction |
| `User_Location` | All 36 Nigerian states + FCT Abuja |
| `Customer_Status` | New, Active, At-Risk, or Churned |
| `Transaction_Type` | 13 real Nigerian fintech transaction categories |
| `Number_of_Transactions` | Total transactions performed |
| `Transaction_Amount` | Transaction value in Naira (₦) |
| `Revenue_Generated` | Platform fee (2% for ≤₦10K, 5% for >₦10K) |

**Behavioral logic applied per customer status:**

| Status | Transactions | Avg Amount | Days Since Active |
|---|---|---|---|
| Active | 30–50 | ₦100K–₦500K | 1–89 days |
| At-Risk | 10–29 | ₦30K–₦150K | 90–180 days |
| Churned | 1–8 | ₦500–₦30K | 181–900 days |
| New | 1–4 | ₦500–₦80K | 1–30 days |

---

## Key Findings

### Revenue
- Total platform revenue: **₦6,338,633**
- Active users (26.6% of base) generate **63.5% of all revenue**
- Active users average **₦15,125** vs churned users at **₦1,836** — an **8x gap**
- Top 10% of users contribute **34.2%** of total revenue

### Churn
- Churned users averaged only **4.43 transactions** vs active users at **39.80**
- Users who reach only **1–4 transactions represent 34.1%** of the entire platform
- Critical drop-off occurs after **transaction 4** — a 53% user fall between tx 4 and tx 5
- New users churn within **16 days** if not engaged early
- Churned users stayed an average of **720 days** before going inactive — churn is gradual

### Geography
- **Lagos** leads total revenue at **₦1,141,786**
- **Yobe, Kebbi, and Gombe** lead revenue per user (₦9,800–₦10,113) — hidden high-value markets
- **Anambra** appears in both top total revenue and top revenue-per-user tables — strongest expansion target

### Transactions
- **Bank Transfer** is the #1 revenue driver (₦826,104)
- **Savings Deposit** users transact most frequently and dominate among active users
- **Airtime Top-up** has the most users (120) but ranks 3rd in revenue — high frequency, low value
- Active users favor: Bank Transfer, Savings Deposit, Merchant Payment


<img width="869" height="486" alt="Screenshot 2026-04-18 154437" src="https://github.com/user-attachments/assets/4dc544cc-9e2e-41e7-8869-1a31080c85a2" />



## Recommendations

1. **Fix the 16-day onboarding window** — deploy a structured Day 1/3/7/14 engagement sequence
2. **Build a 5-transaction rescue program** — target users at exactly 4 transactions with a cashback incentive
3. **Push Savings Deposit to At-Risk users** — highest frequency product among active users
4. **Launch Anambra expansion campaign** — highest revenue per user outside Northern states
5. **Protect Bank Transfer and Savings** — these two products drive the majority of active user revenue
6. **Introduce transaction amount nudges** — large transaction amounts are the strongest predictor of retention
7. **Build a churn prediction flag** — monitor users with declining transaction frequency after day 90


## How to Run

**1. Generate the dataset:**
```bash
# Open and run all cells in:
create_dataset.ipynb
```

**2. Load into MySQL:**
```sql
-- Create database
CREATE DATABASE paylink_database;

-- Import CSV using MySQL Workbench Table Data Import Wizard
-- or use LOAD DATA INFILE
```

**3. Run SQL analysis:**
```bash
# Open and run:
SQL_analysis.ipynb
UserActivity_SQL_analysis.ipynb
```


This project uses a fully synthetic dataset. No real user data was used.  
Free to use for learning and portfolio purposes.
