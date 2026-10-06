# Revenue Performance Analysis

**Course:** GoIT Data Analytics  
**Module:** Tableau  
**Project type:** Coursework expanded into a portfolio case study  
**Analysis period:** June 2022–May 2023

## From Assignment to Business Analysis

The original assignment focused on three visualizations: monthly revenue, revenue by product, and monthly revenue by location.

I expanded it into a business case study with a reporting scenario, data validation, revised findings, and recommendations for further investigation.

The most important improvement came from checking the timeline. Adding the year revealed that the original month-only view had placed months from different years in calendar order. I corrected the chronology and withdrew the earlier interpretation of a May-to-June decline.

## A Timeline Check That Changed the Story

The corrected dashboard shows an overall upward revenue trend from June 2022 to a peak in March 2023, followed by two consecutive monthly declines.

It helps marketing, product, and regional teams identify changes in revenue and decide where deeper investigation is needed.

## Interactive Dashboard

[Explore the dashboard on Tableau Public →](https://public.tableau.com/authoring/1_RevenuePerformanceAnalysis/RevenuePerformanceAnalysis#1)

The dashboard shows monthly revenue across APAC, EMEA, and USA, total revenue by product, and the overall revenue trend.

![Corrected revenue dashboard](assets/development/03-corrected-dashboard.png)

## Business Brief

Imagine a software business with four products serving APAC, EMEA, and USA. Marketing and product managers need a shared overview of revenue to monitor performance and prioritize further analysis.

This is a proposed business application of an educational dataset, not a claim about a real company or client.

**Objective:** identify revenue trends, compare product contribution, and locate regional changes that require investigation.

## Who Would Use It?

| User | Purpose | Decision supported |
|---|---|---|
| Marketing manager | Monitor revenue changes by market | Decide which regional campaign, funnel, and tracking reports to investigate |
| Product manager | Compare product revenue contribution | Prioritize analysis of adoption and monetization |
| Regional sales / customer success lead | Review regional performance | Investigate billing, account activity, and renewals |
| Finance / leadership | Monitor revenue totals and changes | Request reconciliation and explanations of material movements |

The dashboard is relevant to businesses with comparable product and market dimensions. Revenue alone cannot establish campaign effectiveness or justify budget allocation.

## Data and Evidence

The case originates from GoIT coursework.

The findings presented here are based on the visible Tableau aggregates. The CSV files in `data/` are manually transcribed chart summaries, not the original transaction dataset.

The displayed monthly and product totals reconcile to **1,332,835 revenue units**.

The corrected charts display **June 2022–May 2023**. This is a reporting period spanning two calendar years, not a January–December annual total.

Currency has not been verified, so values are presented without a currency symbol.

Transaction grain, duplicates, refunds, missing records, and completeness of individual months still require verification against the source data. The dashboard does not establish recurring revenue, churn, profit, or marketing attribution.

## Key Findings

### 1. Revenue peaked in March 2023

Revenue increased from **44,085 in June 2022** to **162,260 in March 2023**, with a temporary decline in December.

The increase describes the displayed totals. Its causes and the completeness of the reporting periods require further investigation.

### 2. Revenue declined for two consecutive months after the peak

| Month | Revenue | Change from previous month |
|---|---:|---:|
| March 2023 | 162,260 | — |
| April 2023 | 151,080 | −6.9% |
| May 2023 | 136,945 | −9.4% |

By May, revenue was **25,315 lower than March**, a decrease of **15.6%**.

This creates a clear investigation question: which markets, products, and customer segments contributed to the decline?

### 3. Regional patterns help narrow the investigation

| Market | March 2023 | May 2023 | Change | Change % |
|---|---:|---:|---:|---:|
| APAC | 68,350 | 52,325 | −16,025 | −23.4% |
| EMEA | 33,425 | 34,520 | +1,095 | +3.3% |
| USA | 60,485 | 50,100 | −10,385 | −17.2% |
| **Total** | **162,260** | **136,945** | **−25,315** | **−15.6%** |

APAC had the largest absolute decrease, followed by USA. EMEA increased slightly between the two endpoints, partially offsetting those decreases.

These figures identify where revenue changed. They do not establish whether the causes were customer behavior, campaign performance, billing timing, or data completeness.

### 4. Two products contribute 60.3% of period revenue

| Product | Revenue | Share |
|---|---:|---:|
| Main App | 405,645 | 30.4% |
| Customer Success | 398,655 | 29.9% |
| Marketing Automation | 352,905 | 26.5% |
| Publishing | 175,630 | 13.2% |

Main App leads Customer Success by **6,990 revenue units**. Together, they contribute **60.3%** of revenue across the displayed period.

This ranking describes revenue contribution. It does not establish profitability or identify which product drove the April–May decline.

## Data Validation: Why the Year Matters

The original view used month names without showing the year. January–May 2023 appeared before June–December 2022.

This made **May 2023 and June 2022** appear to be consecutive months and led to an incorrect interpretation of a June revenue decline.

Adding `YEAR(Payment Date)` exposed the issue. I withdrew the earlier decline and regional contribution claims, then rebuilt the charts using month and year.

The corrected timeline changed the focus of the analysis to the actual consecutive declines in **April and May 2023**.

[See the screenshots, investigation, and improvements →](docs/project-development.md)

## What Each Chart Is For

| Chart | Question answered | How to use it | Limitation |
|---|---|---|---|
| Monthly Revenue Trend | When did revenue change? | Identify the March peak and subsequent declines | Does not explain causes |
| Total Revenue by Product | Which products contribute most? | Prioritize deeper product analysis | Period totals hide monthly changes and exclude costs |
| Monthly Revenue by Location | Which markets show changes? | Compare regional patterns over time | Location is not acquisition channel or campaign attribution |

## How Marketing Could Use the Dashboard

**Trigger:** May 2023 revenue is 15.6% below the March peak, following two consecutive monthly declines.

1. Confirm complete and comparable reporting periods with Analytics and Finance.
2. Investigate APAC and USA, which show decreases between March and May. Review EMEA as a comparison market.
3. Examine campaign spend, traffic, lead volume, conversion rates, and paying-customer counts over the same period.
4. Check whether the change reflects fewer paying customers, lower revenue per paying customer, or billing timing.
5. Select an action supported by the additional evidence and measure its outcome.

The dashboard supports investigation priorities. Decisions about campaign budgets require acquisition, attribution, and cost data.

## Recommendations

| Priority | Action | Owner | Evidence / success criterion |
|---|---|---|---|
| 1 | Verify source records and monthly completeness | Analytics + Finance | Comparable periods and reconciled totals |
| 2 | Decompose March–May changes by market, product, and customer segment | Analytics + Product | Segment changes reconcile to −25,315 without double counting |
| 3 | Compare paying-customer counts and revenue per paying customer | Analytics | Consistent population and metric definitions |
| 4 | Connect regional revenue with acquisition and spend | Marketing + Analytics | Validated joins and documented attribution rules |
| 5 | Monitor subsequent months | Product + Regional teams | Determine whether the decline continues, stabilizes, or reverses |

## Improvements Implemented

- Corrected the timeline to preserve month and year.
- Added the visible reporting period to the dashboard.
- Sorted products by revenue.
- Reduced line-chart labels to the first month, peak, and last month.
- Simplified technical field labels.
- Updated the narrative to match the corrected chronology.

## Further Improvements

- Verify and document the currency and source coverage.
- Add monthly product analysis to investigate the recent decline.
- Add filters with clearly visible scope.
- Make narrative annotations respond to filters, or label them as full-period findings.
- Add source access instructions and a reproducible workbook where sharing is permitted.

## Reproduction and Validation

The chart-summary CSV files reproduce the displayed aggregates, but do not reproduce the transaction-level Tableau workbook.

[See methodology and outstanding validation checks →](docs/methodology.md)

## Tools and Skills

Tableau · Revenue analysis · Date validation · Visual storytelling · Descriptive analysis · Business recommendations

**Status:** corrected dashboard and revised analytical findings. Source-level validation remains outstanding.
