# Tableau Calculated Fields

## First Payment Date

Earliest positive payment recorded for each customer across all products.

```tableau
{ FIXED [User Id] :
    MIN(
        IF [Revenue Amount] > 0
        THEN [Payment Date]
        END
    )
}
```

## New Paying Customer Revenue

All positive payments in the customer's first recorded payment month.

```tableau
IF [Revenue Amount] > 0
AND DATETRUNC('month', [Payment Date])
    = DATETRUNC('month', [First Payment Date])
THEN [Revenue Amount]
ELSE 0
END
```

## Cohort Month

```tableau
DATETRUNC('month', [First Payment Date])
```

## Months Since First Payment

```tableau
DATEDIFF(
    'month',
    [Cohort Month],
    DATETRUNC('month', [Payment Date])
)
```

Use this field as a discrete dimension on Columns.

## Revenue vs Cohort Month 0

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

Set Compute Using to Specific Dimensions:
- Checked: Months Since First Payment.
- Unchecked: Cohort Month.

Format as Percentage with one decimal place.

## Month-over-Month Revenue Change

Applied to the second SUM(Revenue Amount) measure:
- Quick Table Calculation: Percent Difference.
- Compute Using: Table (Across).
- Relative to: Previous.

Keep the revenue and percentage axes independent.

## Interpretation and Filter Behavior

See [Methodology and Limitations](methodology.md).
