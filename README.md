# video-streaming-churn-analysis.
# Video Streaming Subscription & Churn Analysis (Excel Dashboard)

An end-to-end Excel analysis of **3,069 subscriptions** from a video streaming service. The project cleans the raw data, builds calculated columns and KPIs with formulas, summarises the results in pivot tables, and presents them in an interactive-style dashboard that shows **when customers cancel, how much revenue they generate, and how the user base grows**.

![Final Dashboard](images/Final_Dashboard.png)

---

## Business Questions

1. How many customers did we gain, and how many cancelled?
2. **When** do customers cancel (first week, first month, first quarter, ...)?
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

- **Churn happens early.** About 80% of cancellations (1,593 of 2,004) occur within the first quarter, and about a third happen within the first month. Onboarding and early engagement are the biggest retention opportunity.
- **Very few cancellations are payment failures.** Only 123 cancelled subscriptions were never paid, so churn is mostly voluntary rather than a billing problem.
- **Customer acquisition is growing.** New sign-ups rose from about 190-230 per month in late 2022 to 270-300+ per month in 2023, peaking at 306 in July 2023.
- **Q1 2023 was the strongest revenue quarter** at €95,550. (Q3 2022 and Q3 2023 are partial periods, so their lower totals do not indicate a decline.)

---

## Dataset

Raw data with 3,069 rows, one per subscription:

| Column | Description |
|---|---|
| `customer_id` | Customer identifier |
| `created_date` | Subscription start date (Sep 2022 - Sep 2023) |
| `canceled_date` | Cancellation date (blank = still active) |
| `subscription_cost` | Monthly price (€39 for all rows) |
| `subscription_interval` | Billing interval (monthly for all rows) |
| `was_subscription_paid` | Whether the subscription was ever paid (Yes/No) |

---

## Methodology

**1. Data preparation**
- Renamed and reformatted headers for readability.
- Checked for duplicates. No fully duplicated rows exist. 185 customer IDs appear more than once with different dates, which are re-subscriptions and were kept as separate subscriptions.

**2. Calculated columns** (Excel formulas)

| Column | Logic |
|---|---|
| Paid flag (1/0) | `IF` converts Yes/No to a number so it can be averaged |
| Days Duration | `DATEDIF` between start and cancellation date |
| Accounts longer than 6 months | `IFS` + `EDATE` flags subscriptions that reached 6 months, including active ones |
| Cancellation Time | `IFS` buckets: under a week, month, quarter, half year, year, or Active |
| Estimated Subscription Value | Months subscribed x €39, set to €0 if never paid |

**3. KPI block** built with `COUNT`, `COUNTIFS`, `SUMIF`, `AVERAGEIF`, `SUMPRODUCT`, `MIN`/`MAX`.

**4. Pivot tables** for cancellation timing by payment status, paid revenue by join quarter, and new customers per month.

**5. Dashboard** with three charts (cancellations and payment status, earned revenue per quarter, new users per month) and KPI cards.

---

## Tools & Skills Demonstrated

- **Microsoft Excel:** pivot tables, pivot charts, dashboard design
- **Formulas:** `IFS`, `DATEDIF`, `EDATE`, `COUNTIFS`, `SUMIF`, `AVERAGEIF`, `SUMPRODUCT`
- **Data cleaning & validation**
- **Churn / cohort analysis and KPI design**
- **Data visualisation and business storytelling**

---

## Repository Structure

```
├── README.md
├── video-Stream-Project2.xlsx   # Workbook: data, formulas, KPIs, pivots, dashboard
└── images/
    └── Final_Dashboard.png      # Dashboard screenshot
```

**Workbook sheets**

| Sheet | Contents |
|---|---|
| `Dashboard` | Final dashboard |
| `Sheet1` | Pivot tables feeding the charts |
| `Subscription Cohort Analysis Da` | Cleaned data, calculated columns, KPI block |
| `Read me` | Log of cleaning steps and reasoning |

---

## Assumptions & Limitations

- **Revenue is estimated, not actual.** It is calculated as full months subscribed x €39, so subscriptions cancelled within the first month count as €0.
- **Reference date.** Active-account calculations use 1 Nov 2023, while the data ends on 8 Sep 2023.
- **"Customers" are subscriptions.** There are 3,069 subscriptions from 2,877 unique customer IDs.
- **Single price point.** All subscriptions are €39/month, so there is no plan-level comparison.
- Q3 2022 and Q3 2023 cover partial quarters.

---

## Possible Next Steps

- Retention curve by monthly sign-up cohort
- Compare churn by plan or price (needs more data)
- Add Power BI or Tableau version
- Forecast revenue using observed churn rates

---

## Author

**Soroush**
- Upwork: `<your profile link>`
- LinkedIn: `<your profile link>`
- Email: `<your email>`

*Open to freelance data analysis and Excel dashboard projects.*
