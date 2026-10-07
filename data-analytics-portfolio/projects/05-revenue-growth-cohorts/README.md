# Revenue Growth & Cohort Analysis

Exploring revenue growth through new paying customers and payment cohorts.

**Course:** GoIT Data Analytics
**Module:** Tableau — LOD Expressions and Table Calculations
**Project type:** Coursework expanded into a portfolio case study

## Business Question

How does revenue change over time, how much comes from newly paying customers, and how does each payment cohort develop after its first payment?

## Project Overview

This project extends the earlier revenue analysis with three views:

- Revenue from new paying customers in their first payment month.
- Monthly total revenue and month-over-month percentage change.
- Cohort revenue by months since the first recorded payment.

The dashboard will include location and date filters.

## Data and Scope

[View the source CSV →](data/saas_revenue.csv)

The supplied dataset contains 123,195 rows with customer identifiers, payment dates, locations, products, enterprise-customer flags and revenue amounts.

Cohorts will be defined at customer level using `user_id`, across all products. First payment means the first qualifying payment recorded in the supplied dataset.

Source validation and filter behavior will be documented before interpreting the results.

## Metric Naming

The assignment calls first-payment-month revenue “New MRR.”

This case uses **New Paying Customer Revenue** because the available payment data does not by itself establish recurring subscriptions or monthly normalization.

A customer's first recorded payment may not be their first-ever payment if earlier history is unavailable.

## Cohort Analysis

Customers are grouped by their first recorded payment month.

Each cell shows the cohort's revenue at a given number of months after that first month. Color represents revenue relative to the same cohort's month-zero revenue.

This ratio describes cohort revenue development. It is not customer retention or subscription net revenue retention.

## Business Applications

Product and finance teams can use the dashboard to distinguish revenue from newly paying customers from subsequent cohort revenue.

Marketing teams can investigate acquisition cohorts further when campaign attribution and acquisition costs become available.

## Analytical Priorities

- Preserve consecutive year-month chronology.
- Define customer identity and first-payment scope.
- Document how filters affect LOD expressions.
- Calculate monthly changes using the preceding calendar month.
- Keep cohort month-zero comparisons consistent.
- Distinguish incomplete observation periods from zero revenue.

## Tools and Skills

Tableau · LOD Expressions · Table Calculations · Cohort Analysis · Revenue Analysis

## Project Status

Project structure created. Source validation, dashboard development and findings are pending.
