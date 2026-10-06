# Methodology and limits

## Metric definitions

- Revenue: sum of the displayed `revenue_amount` aggregates. Confirm whether this represents cash collections, recognized revenue, refunds or another measure before making accounting claims.
- Product share: product revenue / total revenue over the same displayed period.
- Month-over-month growth: (current month revenue − previous month revenue) / previous month revenue. Undefined when the previous value is zero.
- Contribution to the May-to-June decline: (May market revenue − June market revenue) / (total May revenue − total June revenue). This is an additive decomposition, not causal attribution.
- Market share: market revenue / total revenue for the same month.

## Checks completed

All 12 sets of regional values reconcile to the displayed monthly totals. The sum of monthly totals equals the sum of product totals: 1,332,835. Percentages are calculated from unrounded chart values and displayed to one decimal place.

## Checks requiring the original dataset

Confirm date range and year; currency and conversions; transaction grain; duplicate records; null fields; refunds; nonpositive payments; missing months; and whether product / market mapping changes over time. Reconcile transcription to the workbook.

Unique paying customers require a documented positive-payment rule and a distinct user count over the selected period. Revenue divided by paying users is ARPPU (or revenue per paying customer), not ARPU across all users. Monthly counts must not be summed to obtain annual unique customers.

Payment revenue alone is not MRR: recurring subscription status and normalization rules are required. This case should remain separate from a subscription Revenue Metrics capstone until its source and definitions are confirmed.

Source transaction data has not been supplied with this package. No retention, churn, causal effect, customer segment revenue or product-level June contribution is claimed.
