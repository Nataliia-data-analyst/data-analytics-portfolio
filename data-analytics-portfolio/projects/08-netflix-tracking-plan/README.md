# Netflix Onboarding & Early Engagement Tracking Plan

Designing a measurement framework for registration, membership setup, profile onboarding and early viewing behavior.

**Course:** GoIT Data Analytics  
**Project type:** Coursework expanded into a portfolio case study  
**Tools:** Google Sheets  
**Research context:** Netflix Poland, English-language web interface, 8 October 2026

[Explore the tracking plan →](https://docs.google.com/spreadsheets/d/13avxyeE0wFl63EAd3As_6D8-Y2jwjMuVUbqDfyFQIgc/edit?usp=sharing)

## Business Question

Where do new accounts drop off before payment and membership activation, and how do new viewing profiles progress toward their first viewing experience and repeated use?

## Project Overview

This project defines 19 proposed events and 10 metrics for measuring the early customer journey.

The tracking plan documents event triggers, properties, data types, expected values, proposed implementation owners, identity rules and measurement windows.

It is an independent educational proposal. No analytics tracking was implemented, and Netflix’s internal instrumentation was not verified.

## Research Scope

Two separate journeys were inspected:

- **New-account signup:** email-link account creation, plan selection and payment-method screens. No new payment was submitted or membership activated.
- **Existing Premium account:** selection of an existing Kids profile, creation of a new non-Kids test profile, introductory tour, search, content details and the player screen.

These observations do not represent one continuous registration-to-playback journey. A visible player screen alone does not confirm successful playback.

Smart TV is included as a proposed schema extension. Its user journey and event triggers require separate validation.

## Tracking Framework

| Area | Proposed events |
|---|---|
| Registration & membership setup | Account Created, Plan Selection Viewed, Plan Selected, Plan Confirmed, Payment Methods Viewed |
| Profile onboarding & content discovery | Profile Created, Onboarding Step Viewed, Onboarding Tour Completed, Profile Selected, Search Results Viewed, Content Details Viewed |
| Payment & subscription | Payment Method Selected, Payment Attempted, Payment Succeeded, Payment Failed, Membership Activated |
| Playback & engagement | Playback Requested, Playback Started, Watch Time Recorded |

## Identity and Data Quality

- `account_id` connects registration, payment and membership activity.
- `profile_id` distinguishes viewing profiles within an account.
- `anonymous_id` supports anonymous browser activity without assuming cross-device continuity.
- `event_id` supports deduplication and remains unchanged on delivery retries.
- Event timestamps use UTC.
- Incremental watch-time values exclude pauses and buffering.
- Trailer and preview activity is excluded from first-view and viewing-habit metrics.

## Metrics

The plan defines:

1. Registration-to-payment conversion within 7 days.
2. Registration-to-activation conversion within 7 days.
3. Payment attempt success rate within 24 hours.
4. Profile tour completion rate within 24 hours.
5. New profile first-view conversion within 7 days.
6. Median time to first view within 7 days.
7. Early viewing habit rate within 7 days.
8. Playback start rate within 60 seconds.
9. Average watch time per new profile within 7 days.
10. Median introductory tour duration within 24 hours.

Each metric specifies its entity, required events, denominator or calculation population, units and observation window.

The proposed early habit threshold is at least 10 minutes of movie or episode viewing on each of three distinct days within seven days. This hypothesis requires validation.

## Key Measurement Decisions

**Separate accounts from profiles.** Creating a profile within an existing membership is different from acquiring a new paying account.

**Separate intent from outcomes.** Selecting a plan, requesting payment and clicking Play do not confirm membership activation, successful payment or playback.

**Use complete observation windows.** Recent accounts and profiles are excluded until the relevant measurement window has elapsed.

**Define time metrics precisely.** Tour duration measures elapsed time between events. Watch time measures active playback.

## Business Applications

Once implemented and validated, this framework could help product teams identify membership setup drop-offs, evaluate profile onboarding, investigate playback friction and compare early engagement cohorts.

## Privacy and Limitations

Proposed analytics payloads exclude email addresses, phone numbers, profile names, payment credentials and raw search text.

The walkthrough covers a limited Poland web experience. Other regions, devices and account states may differ. Payment outcomes are proposed events that were not observed.

No conversion, retention or revenue results are reported.

## Project Status

Tracking plan and metric definitions completed and reviewed for consistency. Instrumentation, event QA and analysis of collected data remain future work.
