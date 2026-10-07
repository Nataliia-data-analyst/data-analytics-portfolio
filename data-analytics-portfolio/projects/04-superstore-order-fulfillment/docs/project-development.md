# Project Development

## From Assignment to Business Analysis

The assignment requested shipment timing by shipping mode, an order distribution and a state map.

The portfolio case adds a business question: where should operations teams investigate differences in time to shipment?

## 1. Clarifying What the Dates Measure

The assignment described delivery time, but the source provides Order Date and Ship Date.

The metric was named Days to Shipment to match the available evidence. This avoids presenting dispatch timing as customer delivery performance.

## 2. Giving Each Order Equal Weight

The source contains multiple product lines per order. Averaging durations directly across rows would give larger orders more weight.

An INCLUDE calculation determines duration by Order ID. Average aggregation then gives each order equal weight. Order counts use COUNTD(Order ID).

This aligns both charts with the order-level business question.

## 3. Defining the Geographic Scope

The supplied file includes US and Canadian records.

All three worksheets were filtered to United States. The original file was preserved unchanged.

This keeps the order distribution, shipping-mode chart and state map within the same geographic scope.

## 4. Moving from Scratchpad to a Workbook

The initial chart was built in the data-source Scratchpad, where worksheet creation and naming were unavailable.

The source was published and used to create a visualization workbook. The three worksheets and dashboard were then assembled there.

## 5. Improving Interpretation

Distinct count of Order ID was displayed as Number of Orders.

Shipment intervals were formatted to one decimal place. The dashboard combines a distribution, shipping-mode averages and a geographic view, with shared filters.

The methodology explains calendar-day calculations, order-level aggregation and the limits of the available dates.

## Final Dashboard

![Superstore Order Fulfillment Analysis](../assets/dashboard-overview.png)

[Explore the interactive dashboard](https://public.tableau.com/views/4_SuperstoreOrderFulfillmentAnalysis/OrderFulfillmentOverview)

## Outcome

The case provides a documented overview of time to shipment and supports further operational investigation.

Promised shipment dates and customer delivery records would be needed to assess lateness and delivery performance.
