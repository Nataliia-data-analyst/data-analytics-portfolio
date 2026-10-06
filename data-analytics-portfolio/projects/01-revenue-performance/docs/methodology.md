# Methodology and Limitations

## Evidence and Scope

This case study uses visible Tableau aggregates and manually transcribed chart summaries.

The corrected dashboard displays June 2022–May 2023. Year labels establish the chronology shown in the charts; complete source coverage and full-month reporting still require transaction-level verification.

Values are reported in revenue units because the currency has not been verified.

## Metric Definitions

- **Revenue:** sum of the displayed `revenue_amount` aggregates. Whether this represents cash collections, recognized revenue, or another measure requires confirmation.
- **Period revenue:** sum of monthly revenue across the displayed June 2022–May 2023 period.
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

- Adding the year revealed that June belonged to 2022 and May to 2023.
- The charts were rebuilt to preserve year-month chronology.
- The earlier May-to-June decline interpretation and associated contribution figures were withdrawn.
- All 12 sets of transcribed regional values reconcile to the displayed monthly totals.
- Monthly totals reconcile to the four product totals: **1,332,835**.
- Percentages use the displayed integer aggregates before percentage rounding and are reported to one decimal place.

These checks establish consistency among the displayed aggregates. They do not establish transaction-level accuracy or completeness.

## Checks Requiring the Original Dataset

- Exact date coverage and completeness of each month.
- Currency, conversion rules, and revenue definition.
- Transaction grain and duplicate records.
- Null fields, refunds, and nonpositive payments.
- Missing records or reporting periods.
- Changes in product and market mapping.
- Reconciliation of transcribed summaries to source records and workbook exports.

## Customer and Subscription Metrics

Unique paying customers require a documented payment eligibility rule and a distinct user count over the selected period.

Revenue divided by paying users is **ARPPU**, or revenue per paying customer. It is not ARPU across all users. Monthly unique-customer counts must not be summed to obtain unique customers across the full period.

Payment revenue alone does not establish **MRR**. Recurring subscription status and normalization rules are required.

This case remains separate from the subscription Revenue Metrics capstone until the relevant source data and metric definitions are confirmed.

## Interpretation Limits

The dashboard describes revenue patterns and supports investigation priorities.

It does not establish:

- Causes of revenue changes.
- Marketing attribution or campaign effectiveness.
- Profitability, CAC, ROAS, or LTV.
- Retention or churn.
- Customer-segment contributions.
- Product contributions to the March–May decrease.

Product totals describe the full reporting period and cannot explain monthly changes without a monthly product breakdown.

March–May comparisons remain provisional until reporting completeness is confirmed. The displayed period alone is insufficient to establish seasonality.
