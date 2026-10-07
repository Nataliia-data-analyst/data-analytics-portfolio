# Onboarding Funnel & Conversion Analysis

Analyzing progression from registration to first payment, conversion by registration month, and time to reach onboarding milestones.

**Course:** GoIT Data Analytics  
**Module:** Tableau — Advanced Chart Settings  
**Project type:** Coursework expanded into a portfolio case study

## Business Question

Which onboarding steps should the product team investigate, how does trial conversion vary by registration month, and how long do users who reach each step take to get there?

## Project Overview

The dashboard includes:

- Registered, trial and paying-user KPI cards.
- Registration-to-trial and registration-to-payment conversion in KPI tooltips.
- Monthly registrations and trial conversion, grouped by registration month.
- A six-step funnel with unique-user counts and conversion relative to registration.
- Average elapsed days from registration to a selected step.
- A parameter action that updates the time chart when a funnel step is selected.

## Data and Scope

[View the source CSV →](data/onboarding_funnel_product.csv)

The supplied educational CSV contains 25,018 event records for 8,460 unique users.

Fields: `user_id`, `event`, `event_timestamp`.

The six recorded event types are registration, email verification, profile completion, setup completion, trial start and first payment.

Initial checks found no missing values, exact duplicate rows or repeated user–event pairs.

Monthly views group events by each user's registration month, rather than the month when a later event occurred.

## Interactive Dashboard

[Explore the dashboard on Tableau Public →](https://public.tableau.com/app/profile/nataliia.fofanova/viz/6_OnboardingFunnelConversionAnalysis/OnboardingFunnelConversionOverview)

Select a funnel bar to change the milestone shown in the time chart, or use the Selected Step parameter.

## Metric Definitions

- Registered Users: distinct users with a registration event.
- Trial Users: distinct users with a trial-start event.
- Paying Users: distinct users with a first-payment event.
- Registration-to-step conversion: users with the specified event divided by registered users in the selected scope.
- Average time to selected step: mean elapsed days among users with that event and a timestamp at or after registration.

Funnel percentages use registration as the denominator, not the preceding step.

Recorded event counts do not by themselves confirm that every user completed all preceding steps in order.

## Key Findings

### 23.03% of registered users have a recorded trial start

The dataset includes 8,460 registered users and 1,948 users with a trial-start event.

### 6.82% of registered users have a recorded first payment

A first-payment event is recorded for 577 users.

These figures describe recorded progression. They do not establish the reasons why other users did not reach those milestones.

### Trial conversion varies across registration months

Observed trial conversion is approximately 25.6% in January, 22.6% in February, 19.4% in March, 21.7% in April and 20.0% in May.

The May group contains only 10 registrations and should not be treated as a stable benchmark.

## Business Applications and Next Steps

- Investigate onboarding friction using event-order checks, error logs and user research.
- Compare conversion within a consistent time window after registration.
- Add channel, device or product-version data to investigate differences between groups.
- Examine median and percentile time to milestones alongside the mean.
- Use validated findings to propose experiments; the dashboard does not establish causal effects.

## Limitations

Users who did not reach a milestone are excluded from its average-time calculation.

Different milestones therefore represent different groups of users.

Monthly comparisons use recorded outcomes without a fixed conversion window. Follow-up completeness requires confirmation.

Missing milestone events do not establish permanent abandonment or churn.

## Tools and Skills

Tableau · LOD Expressions · COUNTD · Conversion Analysis · Gantt Funnel · Parameters · Parameter Actions

## Project Status

Dashboard published. Initial source checks completed. Supporting data, screenshot and detailed methodology are being added.
