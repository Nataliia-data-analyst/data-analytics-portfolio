# Revenue Drivers & Paying Customer Analysis

Understanding how products, markets, and paying customers shape revenue.

**Course:** GoIT Data Analytics  
**Module:** Tableau  
**Project type:** Coursework expanded into a portfolio case study

## Business question

How does revenue change over time, and how do paying-customer counts, revenue per paying customer, products, and markets help explain those changes?

## Project overview

This educational case study expands a Tableau assignment into an interactive analysis of revenue and paying customers across four products and three markets.

The dashboard combines monthly revenue, distinct paying-customer counts, average revenue per paying user (ARPPU), product–market comparisons, regional revenue shares, and payment amount distributions.

Market, product, and date filters allow users to explore each view within the same selected scope.

## Interactive Dashboard

[Explore the dashboard on Tableau Public →](https://public.tableau.com/authoring/2_RevenueDriversandPayingCustomerAnalysis/RevenueDriversPayingCustomerAnalysis#1)

Use the market, product, and payment-date filters to explore revenue and paying-customer metrics. Revenue shares are calculated within the selected markets.


## Key Findings

Across June 2022–May 2023, total revenue reached 1,332,835 revenue units, with 8,463 distinct paying users.

- Monthly paying users increased from 753 in June 2022 to 3,623 in May 2023.
- Over the same interval, ARPPU decreased from 58.55 to 37.80.
- Revenue peaked at 162,260 in March 2023, then fell to 136,945 in May: a 15.6% decrease.
- USA generated 48.3% of full-period revenue, APAC 33.7%, and EMEA 18.0%.
- Marketing Automation in USA was the largest product–market combination at 297,390, followed by Customer Success in APAC at 292,860.

These findings describe the full dataset period with all products and markets included. Currency has not been confirmed.

## The Story Behind the Dashboard

### A larger paying audience, with less revenue per customer

The two customer metrics move in different directions. By May 2023, the monthly paying audience was substantially larger than in June 2022, while revenue per paying customer was lower.

Together, these trends show why customer count alone is insufficient to assess revenue performance. A larger audience can support higher total revenue even as average customer spending declines.

The dashboard reveals this pattern; it does not establish whether pricing, payment frequency, or changes in the customer and product mix caused it.

### The March peak gives way to a two-month decline

Between March and May 2023, revenue decreased by 15.6%. Monthly paying users fell from 4,018 to 3,623, while ARPPU declined from 40.38 to 37.80.

Both components of revenue weakened. The next analytical step is to examine these changes by product and market, then distinguish customer activity from payment timing and reporting coverage.

### Different markets have different product leaders

USA contributed the largest share of revenue across the full period. However, the strongest product–market combinations reveal a more specific picture: Marketing Automation led in USA, while Customer Success was especially strong in APAC.

This makes product–market analysis useful for choosing where to investigate customer needs and monetization. Revenue contribution alone does not establish profitability or justify reallocating marketing budgets.

## Business Application

This dashboard could support a software business operating across multiple products and geographic markets. The business scenario is illustrative; this is an educational dataset, not a real client engagement.

| User | Question | Decision supported |
|---|---|---|
| Product manager | Is revenue changing alongside paying-customer count or ARPPU? | Prioritize product and customer-segment investigations |
| Marketing manager | How do revenue patterns differ across markets and products? | Select segments for deeper funnel and acquisition analysis |
| Regional lead | Which products contribute most to each market? | Focus reviews of customer activity and payment patterns |
| Finance / analytics team | Are changes consistent with payment records and reporting coverage? | Reconcile totals and validate comparisons |

## Recommendations

### 1. Investigate the March-to-May revenue decline

Break down the change by product and market. For each segment, compare revenue, distinct paying users, and ARPPU over consistent reporting periods.

Check May reporting completeness before interpreting the decline: the latest recorded payment is May 30, 2023, which does not by itself confirm whether the month is complete.

### 2. Explain the lower revenue per paying customer

Examine payment frequency, payment amounts, and product mix. Where additional data is available, review pricing changes, discounts, and customer segments.

A decline in ARPPU does not by itself demonstrate customer dissatisfaction or churn.

### 3. Connect revenue patterns to marketing evidence

Compare product–market revenue trends with acquisition spend, traffic, conversion rates, and customer acquisition sources.

Validate join keys and attribution rules before calculating marketing efficiency or recommending budget changes.

### 4. Monitor customer count and ARPPU together

Use both metrics alongside total revenue. When revenue changes, check whether the movement comes from customer count, revenue per customer, or both.

## Interpretation Limits

- Revenue is reported in units because currency has not been confirmed.
- Paying users are distinct within the selected period. Monthly counts must not be added to calculate full-period unique users.
- ARPPU measures revenue per paying user, not revenue per all users.
- Regional shares are recalculated among the selected markets.
- Revenue data alone does not establish MRR, retention, churn, profitability, or advertising effectiveness.
- Findings describe observed patterns; causal explanations require additional evidence.

## Methodology

See [Methodology and Data Validation](docs/methodology.md) for metric definitions, validation results, and unresolved data questions.

## Tools

Tableau · Calculated fields · Table calculations · Interactive dashboards · Data validation
