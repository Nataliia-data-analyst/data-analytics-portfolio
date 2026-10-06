# Methodology and Data Validation

## Data Source and Scope

The analysis uses `saas_revenue.csv`, the GoIT coursework dataset also used in the first portfolio project.

- Rows: 123,195
- Distinct users: 8,463
- Products: 4
- Markets: APAC, EMEA, USA
- Recorded payment dates: June 1, 2022–May 30, 2023
- Total revenue: 1,332,835 revenue units

Currency and the accounting meaning of `revenue_amount` have not been confirmed.

## Tableau Metric Definitions

The formulas below use the field names displayed in Tableau.

### Total Revenue

```tableau
SUM([Revenue Amount])
```

Revenue is summed within the selected dates, products, and markets.

### Paid Users Count

```tableau
COUNTD(
    IF [Revenue Amount] > 0 THEN [User Id] END
)
```

A paying user is a distinct user with at least one positive payment in the selected scope.

A user paying for multiple products is counted once in the overall total, but may appear in several product-level counts. These counts are not additive.

### Average Revenue per Paying User — ARPPU

```tableau
IF [Paid Users Count] > 0 THEN
    [Total Revenue] / [Paid Users Count]
END
```

Revenue and paying-user count must use the same reporting scope. Full-period ARPPU is calculated from full-period revenue and distinct paying users, not by averaging monthly ARPPU.

## Monthly Timeline

Monthly charts use a continuous month-level date that preserves both month and year.

Month names alone are insufficient: the dataset spans two calendar years, and sorting January–December would distort its chronology.

## Monthly Revenue Share by Market

The view uses a Percent of Total table calculation on revenue.

Under Specific Dimensions, only `Location` is checked. The calculation runs across markets separately within each month.

Market filters change the denominator: when only APAC is selected, APAC represents 100% of the selected revenue.

## Payment Amount Distribution

The box plot uses individual row-level payment amounts, with Aggregate Measures disabled on that worksheet.

Products define the comparison groups. Boxes show the interquartile range; whiskers use Tableau's 1.5 × IQR setting.

Repeated payment amounts can cause quartiles to coincide and boxes to collapse into a line. Points beyond the whiskers are statistical outliers, not automatically invalid payments.

## Source Checks Completed

- All payment dates parsed successfully.
- No null values were found in the six source fields.
- All revenue amounts were positive.
- Monthly and product revenue totals both reconcile to 1,332,835.
- March 2023 reconciles to revenue of 162,260, 4,018 paying users, and ARPPU of 40.38.
- May 2023 reconciles to revenue of 136,945, 3,623 paying users, and ARPPU of 37.80.

## Unresolved Data Questions

The source contains 49 exact duplicate rows beyond the first occurrences. They were retained because no transaction identifier is available to distinguish duplicate records from legitimate repeated payments.

The latest payment date is May 30, 2023. The absence of May 31 does not establish missing data, but full-month coverage requires confirmation.

Transaction grain, user-ID consistency, currency, refunds, and product / market definitions require additional source documentation.

## Analytical Limits

The dataset supports descriptive revenue and paying-customer analysis. It does not independently establish recurring revenue, churn, retention, profitability, marketing attribution, or causal effects.
