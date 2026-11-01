# Video Streaming Subscription & Churn Analysis (Excel Dashboard)

> **Project note:** This is a personal **learning project**. The dataset is a practice dataset from an online learning platform for data analysts, used here to build my Excel skills. I do not claim ownership of the raw data.> **Dataset source:** [Streaming Video Subscriptions – Maven Analytics](https://mavenanalytics.io/data-playground/streaming-video-subscriptions). The original dataset is provided by Maven Analytics and is listed as **Public Domain** on its official page. All data preparation, modifications, calculations, and analysis presented in this project were independently completed by me.

An end-to-end Excel analysis of **3,069 subscriptions** from a video streaming service. I cleaned the data, **built five calculated columns and a 15-KPI block from scratch using formulas**, summarised the results in pivot tables, and presented everything in a dashboard showing **when customers cancel, how much revenue they generate, and how the user base grows**.


## What Was Provided vs. What I Built

The original dataset contained only **6 columns (A to F)**. Everything else in the workbook was created by me.

**Colour code in the workbook:**

| Header colour | Meaning |
|---|---|
| **Dark blue** | **Original** columns that came with the dataset |
| **Brown** | **Columns I created myself** with Excel formulas |

### Original columns (dark blue headers)

| Column | Description |
|---|---|
| `customer_id` | Customer identifier (can repeat if a customer re-subscribed) |
| `created_date` | Subscription start date (Sep 2022 - Sep 2023) |
| `canceled_date` | Cancellation date (blank = still active) |
| `subscription_cost` | Monthly price (€39 for all rows) |
| `subscription_interval` | Billing interval (monthly for all rows) |
| `was_subscription_paid` | Whether the subscription was ever paid (Yes/No) |

### Columns I created (brown headers)

| Column | What it does | Main functions |
|---|---|---|
| `was_subscription_paid 1&0` | Converts Yes/No into 1/0 so the paying rate can be averaged | `IF` |
| `Accounts longer than 6 months` | Flags accounts that reached 6 months, including active ones | `IFS`, `AND`, `ISBLANK`, `EDATE` |
| `Days Duration` | Days between sign-up and cancellation (blank for active accounts) | `IF`, `ISBLANK`, `DATEDIF` |
| `Cancellation Time` | Buckets each customer: week, month, quarter, half year, year, or Active | `IFS` |
| `Estimated Subscription Value` | Whole months used x €39, set to €0 if never paid | `IFS`, `DATEDIF` |

I also built the **KPI block** (15 KPIs) next to the data using `COUNT`, `COUNTIFS`, `SUMIF`, `AVERAGEIF`, `SUMPRODUCT`, `MIN` and `MAX`.

> **The full reasoning and the exact formula for every column and KPI are documented in the `Read me` sheet inside the workbook.**

---

## Business Questions

1. How many customers did we gain, and how many cancelled?
2. **When** do customers cancel (first week, month, quarter, ...)?
3. How many cancellations never paid at all?
4. How long does the average subscriber stay?
5. How much revenue has been earned, and how much is still active?
6. How is new-customer growth trending month to month?

---

## Key Findings

| Metric | Result |
|---|---|
| Total subscriptions analysed | **3,069** |
| Cancellations | **2,004** (about 65% of all subscriptions) |
| Still active | 1,065 |
| Subscriptions that were paid | 2,936 (about 95.7%) |
| Unpaid cancellations | **123** (6.1% of cancellations) |
| Accounts lasting 6+ months | **472** (about 25% of eligible accounts) |
| Average time before cancelling | **58 days** |
| Longest time before cancelling | 348 days |
| Total estimated revenue | **€321,945** |
| Active customers' estimated value | €202,839 |
| Revenue already lost to cancellations | €119,106 |

**Insights**

- **Churn happens early.** About 80% of cancellations (1,593 of 2,004) occur within the first quarter, and about a third within the first month. Onboarding and early engagement are the biggest retention opportunity.
- **Few cancellations are payment failures.** Only 123 cancelled subscriptions were never paid, so churn is mostly voluntary rather than a billing problem.
- **Acquisition is growing.** New sign-ups rose from about 190-230 per month in late 2022 to 270-300+ in 2023, peaking at 306 in July 2023.
- **Q1 2023 was the strongest revenue quarter** at €95,550. (Q3 2022 and Q3 2023 are partial quarters, so their lower totals are not a decline.)

---

## Methodology

1. **Data preparation:** renamed and tidied headers; checked for duplicates. There are no fully duplicated rows. 185 customer IDs appear more than once with different dates, which are re-subscriptions, so they were kept as separate subscriptions.
2. **Calculated columns:** five formula-driven columns (brown headers, see above).
3. **Consideration date:** the dataset has no "today" for active accounts, so I set a fixed **consideration date of 1 November 2023**. All active-account calculations (6-month status and estimated value) are measured up to this date, keeping results consistent and reproducible. The data itself ends on 8 September 2023, so this was a deliberate choice and can be changed in one cell to re-run the analysis.
4. **KPI block:** 15 KPIs built with formulas.
5. **Pivot tables:** cancellation timing by payment status, paid revenue by join quarter, and new customers per month.
6. **Dashboard:** three charts (cancellations and payment status, earned revenue per quarter, new users per month) plus KPI cards.

---

## Tools & Skills Demonstrated

- **Microsoft Excel:** pivot tables, pivot charts, dashboard design
- **Formulas:** `IF`, `IFS`, `DATEDIF`, `EDATE`, `COUNTIFS`, `SUMIF`, `AVERAGEIF`, `SUMPRODUCT`
- **Data cleaning and validation**
- **Churn analysis and KPI design**
- **Data visualisation and business storytelling**

---

## Repository Structure

```
README.md
video-Stream-Project2.xlsx    (data, formulas, KPIs, pivots, dashboard)
images/
    Final_Dashboard.png       (dashboard screenshot)
```

| Workbook sheet | Contents |
|---|---|
| `Dashboard` | Final dashboard |
| `Sheet1` | Pivot tables feeding the charts |
| `Subscription Cohort Analysis Da` | Data, calculated columns, KPI block |
| `Read me` | Reasoning and formulas for every step |

---

## Assumptions & Limitations

- **Learning project:** built on a practice dataset, so findings illustrate the method and are not real business advice.
- **Revenue is estimated, not actual:** it uses whole months subscribed x €39, so a subscription cancelled within its first month counts as €0.
- **Consideration date:** active-account calculations use 1 Nov 2023, while the data ends on 8 Sep 2023.
- **"Customers" are subscriptions:** 3,069 subscriptions from 2,877 unique customer IDs.
- **Single price point:** all subscriptions are €39/month, so no plan-level comparison is possible.

---

## Possible Next Steps

- Retention curve by monthly sign-up cohort
- Power BI or Tableau version of the dashboard
- Revenue forecast based on observed churn rates

---

## Author

**Soroush**

- Upwork:https://www.upwork.com/freelancers/~0124871fd1f5602bed
- LinkedIn:(https://www.linkedin.com/in/soroush-ahmadifar/)
- Email:soroushinkavosh@gmail.com

*Open to freelance data analysis and Excel dashboard projects.*
