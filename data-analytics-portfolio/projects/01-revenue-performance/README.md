# Revenue Performance Analysis

**Course:** GoIT Data Analytics  
**Module:** Tableau  
**Project type:** Coursework expanded into a portfolio case study

## From Assignment to Business Analysis

The original assignment focused on three visualizations:
monthly revenue, revenue by product, and monthly revenue by location.

I extended the assignment with a business scenario, a regional
decomposition of the May-to-June revenue decline, and recommendations
for further investigation.

The dashboard helps marketing, product, and regional teams identify
when revenue changes and where to investigate first.

### One revenue drop. Three markets. A clearer place to start.

An educational Tableau case study exploring revenue across months, products and geographic markets. The dashboard flags an unusually weak June; a regional comparison shows where the observed decline is concentrated.

## Interactive Dashboard

[Explore the dashboard on Tableau Public →](https://public.tableau.com/views/1_RevenuePerformanceAnalysis/RevenuePerformanceAnalysis)

The dashboard shows total monthly revenue, revenue by product,
and monthly revenue across APAC, EMEA, and USA.

![Original Tableau dashboard](assets/dashboard-original.png)

## Investigating the June Revenue Decline

Where should the team investigate first?

Revenue fell from **136,945 in May to 44,085 in June**,
a **67.8% month-over-month decline**.

![June Revenue Decline](assets/june-revenue-decline.png)

APAC and EMEA accounted for **85.6% of the total decrease**.
USA also declined, but less sharply.

[Explore the June Revenue Decline dashboard →](https://public.tableau.com/authoring/1_RevenuePerformanceAnalysis/JuneRevenueDecline#1)

**Recommended next step:** validate data completeness, then
investigate billing activity and paying-customer trends in
APAC and EMEA. The comparison identifies where the decline
occurred; its causes require further analysis.

## Business brief

Imagine a software business with four products serving APAC, EMEA and USA. Marketing and product managers need a shared overview of revenue and a way to prioritize investigations when performance changes. This is a proposed application of the coursework dataset, not a claim about a real company or client.

**Objective:** identify revenue patterns, product contribution and the markets contributing most to the May-to-June decline.

## Who would use it?

| User | Purpose | Decision supported |
|---|---|---|
| Marketing manager | Spot changes by market and establish investigation priorities | Decide which regional campaign and tracking reports to examine first |
| Product manager | Compare product revenue contribution | Prioritize product-level analysis, then check adoption and monetization |
| Regional sales / customer success lead | Review regional performance changes | Check billing, account activity and renewal records |
| Finance / leadership | Monitor revenue totals and volatility | Request reconciliation and an explanation of material changes |

Useful for a software business with comparable product and market dimensions. Revenue alone cannot establish campaign effectiveness or justify budget allocation.

## Data and evidence

The case originates from course homework. Current evidence consists of a Tableau dashboard screenshot and its visible aggregates. The two CSVs in `data/` are manually transcribed chart summaries, not the original transaction dataset. Regional values reconcile to monthly totals; monthly totals reconcile to the four product totals: **1,332,835**.

The source fields described in the course context are `user_id`, `payment_date`, `location`, `software_name`, `is_enterprise_customer`, and `revenue_amount`. Their types, transaction grain, uniqueness, coverage and business meaning still require verification against the source file.

Currency and year are not established by these screenshots. Numbers below therefore use revenue units, without a dollar symbol. The data does not establish recurring revenue, churn, profit, acquisition channel or marketing attribution.

## The story: look beyond the headline

### 1. The annual total hides a sharp interruption

Revenue across the displayed January–December period totals **1.33M**. March is the highest month at **162,260**. June is the lowest at **44,085**: a **67.8% decline from May**, when revenue was 136,945.

The practical question is not simply “Which month was weakest?” It is “Where should the team look first to explain the change?”

### 2. The decline is concentrated in two markets

| Market | May | June | Change | Change % | Share of total decline |
|---|---:|---:|---:|---:|---:|
| APAC | 52,325 | 3,475 | −48,850 | −93.4% | 52.6% |
| EMEA | 34,520 | 3,850 | −30,670 | −88.8% | 33.0% |
| USA | 50,100 | 36,760 | −13,340 | −26.6% | 14.4% |
| Total | 136,945 | 44,085 | −92,860 | −67.8% | 100.0% |

APAC and EMEA account for **85.6% of the observed decrease**. USA also declines, but less sharply. Its share rises from **36.6% in May to 83.4% in June** because the other markets fall faster—not because USA grows.

This is a descriptive decomposition, not proof of a causal explanation. Campaign changes, missing data, delayed billing and customer losses remain hypotheses to test.

### 3. Revenue rises after June, but the March peak is not regained

Revenue increases each month from June through November, reaching **122,865** in November. That remains **24.3% below March**. December then declines to **107,320**, down **12.7% from November**.

“Recovery through November, followed by a December decline” is more accurate than “continuous recovery in the second half.” A single year does not establish seasonality.

### 4. Product revenue is spread across three substantial contributors

| Product | Revenue | Share |
|---|---:|---:|
| Main App | 405,645 | 30.4% |
| Customer Success | 398,655 | 29.9% |
| Marketing Automation | 352,905 | 26.5% |
| Publishing | 175,630 | 13.2% |

Main App leads Customer Success by only **6,990**. Together they contribute **60.3%**. The ranking indicates contribution, not profitability, growth potential or marketing efficiency. These annual product totals cannot identify which product drove June’s decline.

## What each chart is for

| Chart | Question answered | How to use it | Limitation |
|---|---|---|---|
| Monthly Revenue | When did performance change? | Detect June, compare May and June, monitor subsequent months | Cannot explain the cause |
| Revenue by Product | Which products contribute most? | Set priorities for deeper product analysis | Annual ranking hides monthly changes and excludes costs |
| Monthly Revenue by Location | Where is the change concentrated? | Compare APAC, EMEA and USA around the anomaly | Location is not acquisition channel or campaign attribution |

## How marketing could act on the dashboard

**Trigger:** June revenue is down 67.8% from May.

1. Confirm completeness, comparable reporting periods, market mapping, currency treatment and billing timing with the data / finance team.
2. Investigate APAC and EMEA first: together they contribute 85.6% of the decrease. USA remains in scope.
3. Compare regional campaign spend, paid traffic, lead volume, conversion rates and paying-customer counts for May and June.
4. Join revenue with acquisition and cost data using validated identifiers and attribution rules. Check whether lower revenue reflects fewer customers, lower revenue per paying customer, or timing effects.
5. Choose an action based on the evidence: repair missing data; resolve billing issues; investigate funnel friction; or test campaign changes. Measure the outcome against a baseline, using an experiment where practical.

The current dashboard establishes where and when to investigate. It does not support ROAS, CAC, LTV or a recommendation to move spend toward the highest-revenue product.

## Recommendations

| Priority | Action | Owner | Evidence / success criterion |
|---|---|---|---|
| 1 | Validate the June data and reconcile to source payment records | Analytics + Finance | Full period coverage and reconciled totals |
| 2 | Decompose May-to-June changes by market, product and customer segment | Analytics + Product | Segment changes reconcile to −92,860 without double counting |
| 3 | Compare paying customers and revenue per paying customer by month | Analytics | Verified positive-payment population and consistent denominator |
| 4 | Connect regional revenue to acquisition and spend | Marketing + Analytics | Validated joins and documented attribution / cost coverage |
| 5 | Monitor the December decline | Regional teams | Month comparison checked for coverage and explained by segments |

## Tableau improvement plan

The screenshot shows the existing homework dashboard. The following improvements are proposed and have not yet been implemented:

- Lead with the monthly trend and KPI cards for total revenue, peak month and lowest month.
- Place a business question above each chart and a concise evidence-based insight below it.
- Use horizontal product bars sorted by revenue and a consistent market color palette.
- Replace crowded market labels with tooltips; optionally use three market lines for time comparison.
- Add a May-to-June change chart by market.
- Add product, location and customer-segment filters; make KPI scope and date range visible.
- Keep static full-period findings clearly labeled, or update them dynamically when filters change.

## Reproduction and validation

The CSV summaries reproduce the findings above, but not the transaction-level Tableau workbook. See [Methodology](docs/methodology.md) for formulas and outstanding checks.

To complete publication: attach the verified source or its access instructions, confirm publication permission, document year and currency, add the Tableau workbook and the published view URL, and replace the screenshot after implementing dashboard improvements.

## Tools and skills

Tableau · Revenue analysis · Visual storytelling · Descriptive decomposition · Business recommendations

**Status:** initial documented case study. Tableau workbook, live dashboard URL and transaction-level validation are pending.
