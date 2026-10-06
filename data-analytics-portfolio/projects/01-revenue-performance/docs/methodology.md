# Methodology and Limitations

## Evidence and Scope

This case study uses the GoIT coursework dataset, visible Tableau aggregates, and manually transcribed chart summaries.

[View the source CSV →](../data/saas_revenue.csv)

The source contains 123,195 rows across four products and three markets. Recorded payment dates range from June 1, 2022 to May 30, 2023.

The corrected dashboard displays June 2022–May 2023 in chronological order. This period spans two calendar years.

Recorded date boundaries have been verified. Complete source coverage and full-month reporting still require confirmation.

Values are reported in revenue units because currency has not been verified.

## Metric Definitions

- **Revenue:** sum of `revenue_amount` within the reporting scope. Whether this represents cash collections, recognized revenue, or another measure requires confirmation.
- **Period revenue:** sum of revenue across June 2022–May 2023.
- **Product share:** product revenue divided by total revenue over the same period.
- **Month-over-month change:** (current month revenue − previous month revenue) / previous month revenue. Only consecutive year-month periods are compared. The percentage is undefined when the previous value is zero.
- **Change from the March peak:** (May 2023 revenue − March 2023 revenue) / March 2023 revenue. This is a two-month endpoint comparison, not a month-over-month change.
- **Regional revenue change:** market revenue in May 2023 minus market revenue in March 2023.
- **Market share:** market revenue divided by total revenue for the same month.

Regional changes provide an additive decomposition of the total change, not causal attribution.

## Calculations Used in the Findings

| Measure | Calculation | Result |
|---|---|---:|
| April month-over-month change | (151,080 − 162,260) / 162,260 | −6.9% |
| May month-over-month change | (136,945 − 151,080) / 151,080 | −9.4% |
| May change from March peak | (136,945 − 162,260) / 162,260 | −15.6% |
| Main App and Customer Success share | (405,645 + 398,655) / 1,332,835 | 60.3% |

Regional changes from March to May reconcile to the total decrease:

- APAC: **−16,025**
- EMEA: **+1,095**
- USA: **−10,385**
- Total: **−25,315**

## Checks Completed

### Timeline and Interpretation

- Adding the year revealed that June belonged to 2022 and May to 2023.
- The charts were rebuilt to preserve year-month chronology.
- The earlier May-to-June decline interpretation and associated contribution figures were withdrawn.

### Source Data and Reconciliation

- All source payment dates parsed successfully.
- No null values were found in the six source fields.
- All revenue amounts were positive.
- All 12 sets of regional summary values reconcile to the corresponding monthly totals.
- Source monthly, regional, and product totals reconcile to **1,332,835 revenue units** and agree with the chart summaries.
- Percentages are calculated before percentage rounding and reported to one decimal place.

These checks establish agreement between the supplied CSV and the reported aggregates. They do not independently establish that the source contains every expected payment.

### Duplicate Rows

The source contains **49 exact duplicate rows beyond their first occurrences**.

They were retained because no transaction identifier is available to distinguish accidental duplication from legitimate repeated payments.

## Remaining Validation Questions

- Completeness of each reporting month, particularly May 2023.
- Currency, conversion rules, and the accounting definition of revenue.
- Transaction grain and the meaning of repeated rows.
- Whether refunds are excluded, stored separately, or represented through another process.
- Missing records or reporting periods.
- Consistency of user identifiers and product / market mapping.
- Agreement between the supplied CSV and the exact data version used in the published workbook.

The latest recorded payment is May 30, 2023. The absence of May 31 does not by itself demonstrate missing data or confirm full-month coverage.

## Customer and Subscription Metrics

A paying customer is defined as a distinct user with at least one positive payment within the selected reporting scope.

Revenue divided by paying users is **ARPPU**, or revenue per paying customer. It is not ARPU across all users. Monthly unique-customer counts must not be summed to obtain unique customers across the full period.

Customer metrics are explored in the companion case study:

[Revenue Drivers & Paying Customer Analysis →](../../02-revenue-drivers/README.md)

Payment revenue alone does not establish **MRR**. Recurring subscription status and normalization rules are required.

This case remains separate from the subscription Revenue Metrics capstone, which requires its own source data and metric definitions.

## Interpretation Limits

The dashboard describes revenue patterns and supports investigation priorities.

It does not establish:

- Causes of revenue changes.
- Marketing attribution or campaign effectiveness.
- Profitability, CAC, ROAS, or LTV.
- Retention or churn.
- Customer-segment contributions.
- Product contributions to the March–May decrease within this case study.

Full-period product totals cannot explain monthly changes without a monthly product breakdown.

March–May comparisons remain provisional until reporting completeness is confirmed. The displayed period alone is insufficient to establish seasonality.
