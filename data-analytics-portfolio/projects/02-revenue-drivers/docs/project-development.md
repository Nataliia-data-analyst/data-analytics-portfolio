# Project Development: From Coursework to an Analytical Dashboard

## Starting Point

The original assignment introduced revenue metrics and more advanced Tableau visualizations.

The portfolio version adds business questions, a consistent reporting timeline, coordinated filters, and documented interpretation limits.

## 1. Preserving the Reporting Timeline

**Problem:** Month names alone did not preserve the chronological order of a dataset spanning two calendar years.

**Change:** Monthly views were configured with a continuous month-level date that retains the year.

**Why it matters:** June 2022 and May 2023 must appear in their actual sequence. Month-over-month comparisons require adjacent calendar months.

**Result:** The dashboard displays June 2022–May 2023 in chronological order, supporting valid comparisons over time.

## 2. Making Total Monthly Revenue Visible

**Problem:** Separate product panels made individual product trends visible but made total monthly revenue harder to compare.

**Change:** Products were combined into stacked monthly bars, with color identifying each product.

**Why it matters:** Bar height shows total revenue, while the segments show how products contribute to it.

**Result:** Users can compare monthly totals and product composition in one view. Tooltips support precise comparisons of segments without a shared baseline.

## 3. Reading Paying Users and ARPPU Together

**Problem:** The initial arrangement did not provide a clear shared timeline for paying-customer count and ARPPU.

**Change:** Both metrics were displayed as separate line panels aligned to the same monthly axis.

**Why it matters:** Customer count and revenue per customer use different units. Separate panels preserve readable scales while allowing their trends to be compared.

**Result:** The dashboard reveals periods when customer count and ARPPU move together or in different directions.

## 4. Building a Payment Distribution View

**Problem:** Aggregated revenue totals did not show the distribution of individual payment amounts.

**Change:** The worksheet uses row-level revenue amounts, with Aggregate Measures disabled, and a box plot for each product.

**Why it matters:** A distribution requires individual observations rather than one total per group.

**Result:** The view shows payment amount variation across products. Repeated values explain why some boxes collapse into a line; this is not automatically a visualization error.

## 5. Calculating Market Share Within Each Month

**Problem:** Grouping payments by day of the month combined dates from different months and did not answer the revenue-share question.

**Change:** The view uses a month-and-year timeline and a Percent of Total calculation across Location within each month.

**Why it matters:** Each market's revenue must be divided by the total for the same month.

**Result:** The chart shows how the geographic revenue mix changes over time. Shares recalculate among the selected markets.

## 6. Coordinating Dashboard Filters

**Change:** Market, product, and payment-date filters were applied to the six dashboard worksheets.

**Why it matters:** Views must use a consistent selection when users compare revenue, customer metrics, and distributions.

**Design note:** Fixed numerical commentary is labeled as a full-period insight for all markets and products. It does not update with filters.

## Validation and Remaining Questions

Source-level checks reconcile monthly and product revenue totals to 1,332,835.

March 2023 provides a reference check: revenue of 162,260, 4,018 distinct paying users, and ARPPU of 40.38.

Remaining questions include currency, transaction grain, May reporting completeness, and the meaning of exact duplicate rows. These limits are documented in the methodology.

## Supporting Evidence

The [dashboard overview](../assets/dashboard-overview.png) shows the final layout.

Before-and-after screenshots can be added to illustrate individual changes. Only screenshots that document the described state should be included.
