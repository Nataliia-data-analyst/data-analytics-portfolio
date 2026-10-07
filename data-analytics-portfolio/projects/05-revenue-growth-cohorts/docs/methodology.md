# Methodology and Limitations

## Source and Scope

[View the source CSV](../data/saas_revenue.csv)

[Tableau calculated fields and table calculation settings →](docs/tableau-calculations.md)

The analysis groups customers by `user_id` across all products.

First payment means the earliest positive payment recorded in the supplied dataset. Earlier customer history is unavailable.

Revenue is reported in unspecified currency units.

## First Payment Date

```tableau
{ FIXED [User Id] :
    MIN(
        IF [Revenue Amount] > 0
        THEN [Payment Date]
        END
    )
}
```

The FIXED expression establishes each customer's first qualifying payment date across the source.

Location and date filters remain ordinary dimension filters. They are not added to context, so they do not redefine the first payment date.

Data-source, extract or context filters that remove earlier records could change this result.

## New Paying Customer Revenue

```tableau
IF [Revenue Amount] > 0
AND DATETRUNC('month', [Payment Date])
    = DATETRUNC('month', [First Payment Date])
THEN [Revenue Amount]
ELSE 0
END
```

The chart sums all positive payments made in a customer's first recorded payment month, not only the first transaction.

The assignment calls this metric New MRR. This case uses New Paying Customer Revenue because recurring subscriptions and monthly normalization have not been established.

## Monthly Revenue and Growth

Total Revenue is SUM([Revenue Amount]).

The second axis uses Percent Difference from Previous, computed across consecutive calendar months:

(Current month revenue − Previous month revenue) / Previous month revenue.

The first displayed month has no comparison value. A zero previous-month value makes percentage growth undefined.

The source view contains consecutive months. If filters create gaps, comparisons must be checked before interpreting them as month-over-month changes.

## Cohort Definitions

### Cohort Month

```tableau
DATETRUNC('month', [First Payment Date])
```

### Months Since First Payment

```tableau
DATEDIFF(
    'month',
    [Cohort Month],
    DATETRUNC('month', [Payment Date])
)
```

Month 0 is the first recorded payment month. Month 1 is the next calendar month.

Cohort Month forms the rows. Months Since First Payment is a discrete dimension forming the columns.

## Cohort Revenue Ratio

Labels show SUM([Revenue Amount]).

Color shows each cell's revenue divided by the same cohort's month-zero revenue:

```tableau
IF WINDOW_SUM(
    SUM(
        IF [Months Since First Payment] = 0
        THEN [Revenue Amount]
        END
    )
) > 0
THEN
    SUM([Revenue Amount])
    /
    WINDOW_SUM(
        SUM(
            IF [Months Since First Payment] = 0
            THEN [Revenue Amount]
            END
        )
    )
END
```

Specific Dimensions addresses Months Since First Payment only. Cohort Month remains unchecked, creating a separate calculation for each cohort row.

Month-zero cells equal 100%. Ratios above 100% mean recorded revenue exceeds the cohort's initial-month revenue.

This is a revenue ratio, not customer retention or subscription net revenue retention.

## Dashboard Filter Behavior

- Location filters all three views and the payments included in their revenue totals. Cohort membership remains based on the first payment across the source.
- Payment Date filters the two monthly charts. The first visible month loses its previous-month comparison.
- First Payment Month filters cohort rows while preserving each selected cohort's observed history and month-zero baseline.

A payment-date filter is not applied to the cohort table because it could remove month-zero records.

## Reference Checks

For the full period and all locations:

- June 2022 total revenue: 44,085.
- June 2022 first-payment-month revenue: 44,085.
- March 2023 total revenue: 162,260.
- June 2022 cohort, month 0: 44,085 and 100%.
- June 2022 cohort, month 1: 46,015, approximately 104.4% of month 0.

These are selected reference checks, not a complete reconciliation of every cohort cell.

## Interpretation Limits

The first observed cohort may include customers who paid before the dataset began. Its size cannot establish an acquisition peak.

Recent cohorts have shorter observation windows. Compare cohorts at the same age rather than by full-period totals.

Blank cells may represent periods outside the observation window or no recorded payments. They do not establish churn.

Month-zero revenue reflects different first-payment dates within the month. A later full month can exceed this baseline without proving improved retention.

Currency, payment-record grain, reporting completeness and subscription status require confirmation.

The dashboard does not establish acquisition channel, campaign effectiveness, profitability, CAC, LTV or causes of revenue changes.
