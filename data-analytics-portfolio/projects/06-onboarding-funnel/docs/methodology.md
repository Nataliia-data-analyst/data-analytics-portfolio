# Methodology and Limitations

## Source and Initial Checks

[View the source CSV](../data/onboarding_funnel_product.csv)

The supplied educational dataset contains 25,018 event records and 8,460 distinct users.

Initial checks found:
- No missing values in the three source fields.
- No exact duplicate rows.
- No repeated user–event pairs.

These checks do not establish tracking completeness or correct event order.

## Registration Date

```tableau
{ FIXED [User Id] :
    MIN(
        IF [Event] = 'registration'
        THEN [Event Timestamp]
        END
    )
}
```

This date is associated with every event belonging to the user.

Monthly charts use the month and year of Registration Date, so later trial and payment events remain assigned to the user's registration group.

The workbook may display this field as RegistrationDate.

## KPI Calculations

### Registered Users

```tableau
COUNTD(
    IF [Event] = 'registration'
    THEN [User Id]
    END
)
```

### Trial Users

```tableau
COUNTD(
    IF [Event] = 'trial-start'
    THEN [User Id]
    END
)
```

### Paying Users

```tableau
COUNTD(
    IF [Event] = 'first-payment'
    THEN [User Id]
    END
)
```

### Registration to Trial CR

```tableau
IF [Registered Users] > 0
THEN [Trial Users] / [Registered Users]
END
```

### Registration to Payment CR

```tableau
IF [Registered Users] > 0
THEN [Paying Users] / [Registered Users]
END
```

Event filters are not applied to KPI sheets because removing registration records would remove the conversion denominator.

## Monthly Registrations and Trial Conversion

Columns: continuous month and year of Registration Date.

Rows:
- Registered Users, displayed as bars.
- Registration to Trial CR, displayed as a line on a separate percentage axis.

The axes are not synchronized because their units differ.

Trial conversion represents recorded trial starts among each month's registered users, without a fixed post-registration conversion window.

## Funnel Construction

### Step Order

```tableau
CASE [Event]
WHEN 'registration' THEN 1
WHEN 'email-verification' THEN 2
WHEN 'profile-completion' THEN 3
WHEN 'setup-completion' THEN 4
WHEN 'trial-start' THEN 5
WHEN 'first-payment' THEN 6
END
```

Event is sorted ascending by MIN(Step Order).

### Step Users

```tableau
COUNTD([User Id])
```

### Funnel Start

```tableau
-[Step Users] / 2
```

Rows: Event.  
Columns: Funnel Start.  
Marks: Gantt Bar.  
Size: Step Users.

Each bar is centered on zero. Negative axis positions are a layout device, not negative user counts.

### Step Conversion from Registration

```tableau
IF WINDOW_SUM([Registered Users]) > 0
THEN
    [Step Users] / WINDOW_SUM([Registered Users])
END
```

Compute Using: Specific Dimensions, with Event checked.

The registration row supplies the denominator. Removing it through a filter makes the calculation undefined.

Labels show unique-user counts and percentages relative to registration.

This is an event-reach funnel. It does not enforce completion of preceding steps or chronological event order.

## Selected Step Parameter

Name: Selected Step.  
Data type: String.  
Allowable values: List.

Values:
- registration
- email-verification
- profile-completion
- setup-completion
- trial-start
- first-payment

Default selection: first-payment.

## Elapsed Days to Selected Step

```tableau
IF [Event] = [Selected Step]
AND NOT ISNULL([Registration Date])
AND [Event Timestamp] >= [Registration Date]
THEN
    DATEDIFF(
        'second',
        [Registration Date],
        [Event Timestamp]
    ) / 86400.0
END
```

Use RegistrationDate instead if that is the workbook field name.

Non-selected events and timestamps before registration return NULL, not zero.

The chart uses AVG(Elapsed Days to Selected Step), grouped by registration month.

Because the source has one record per user–event pair, each qualifying user contributes once to the selected milestone's mean.

Future datasets with repeated events would require an explicit first-occurrence rule.

## Parameter Action

- Source sheet: Onboarding Funnel.
- Run on: Select.
- Target parameter: Selected Step.
- Source field: Event.
- Aggregation: None.
- Clearing selection: Keep current value.

Selecting a funnel bar updates the parameter, the time chart and its dynamic title.

This action changes the selected milestone; it does not filter the dashboard to users represented by the selected bar.

## Reference Values

For the full dataset:

| Step | Users | Conversion from registration |
|---|---:|---:|
| Registration | 8,460 | 100.00% |
| Email verification | 6,267 | 74.08% |
| Profile completion | 4,660 | 55.08% |
| Setup completion | 3,106 | 36.71% |
| Trial start | 1,948 | 23.03% |
| First payment | 577 | 6.82% |

The May registration group contains only 10 users.

## Interpretation Limits

- Missing events do not establish permanent abandonment or churn.
- Event sequence and tracking completeness require further validation.
- Conversion comparisons do not use a consistent elapsed-time window.
- Average time includes only users who reached the selected milestone.
- Different milestones represent different user groups.
- The mean can be influenced by long delays; median and percentiles would add context.
- Differences across registration months do not establish causes or experiment effects.
- Channel, device, product-version and acquisition-cost data are unavailable in this source.
