# Methodology and Limitations

## Source and Scope

The analysis uses the Orders worksheet from Tableau Sample Superstore.

[Download the source dataset](../data/sample-superstore.xls)

All three worksheets are filtered to United States. The original source file remains unchanged.

## Data Grain

Each row represents an order line. One order can contain several product lines.

Order counts use distinct Order IDs. Average days to shipment gives each order equal weight.

Source checks confirmed that dates, shipping mode, state and segment are consistent within each Order ID.

## Calculated Fields

### Days to Shipment

Calendar days from order placement to shipment:

```tableau
DATEDIFF('day', [Order Date], [Ship Date])
```

### Order Days to Shipment

One duration per order within the dimensions of the view:

```tableau
{ INCLUDE [Order ID] : MIN([Days to Shipment]) }
```

This field uses Average aggregation in the shipping-mode chart and state map.

### Number of Orders

```tableau
COUNTD([Order ID])
```

The distribution chart groups distinct orders by Days to Shipment.

## Filters

Order Date, Segment and Ship Mode apply to all three worksheets.

Order Date filters by placement date. An included order may ship after the selected date range.

## Validation

Source checks found no negative order-to-shipment intervals.

Dashboard validation should confirm that:

- Distribution counts sum to the distinct US order count under the same filters.
- Shipping-mode averages match an independent order-level calculation.
- Every dashboard filter updates all three views.
- State comparisons include the number of orders behind each average.

## Interpretation Limits

- Ship Date records shipment, not customer delivery.
- Durations include weekends and holidays.
- Zero days means shipment on the same calendar date, not immediate shipment or same-day delivery.
- No promised shipment dates are available, so longer intervals cannot automatically be classified as late.
- State averages may reflect shipping-mode mix and small order counts.
- The data is an educational sample, not verified operating results of a real retailer.
