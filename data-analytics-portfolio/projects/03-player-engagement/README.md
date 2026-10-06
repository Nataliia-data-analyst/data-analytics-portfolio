# Player Engagement & Battle Pass Participation

Exploring player activity, time spent in games, and participation in Battle Pass activities.

**Course:** GoIT Data Analytics  
**Module:** Tableau — Calculated Fields  
**Project type:** Coursework expanded into a portfolio case study

## Business Question

How do monthly active-player counts, Battle Pass participation, and playtime vary over time and across player age groups?

## Project Overview

This educational case study examines recorded activity across three mobile games.

The analysis will combine three views:

- Monthly distinct active players and the percentage participating in Battle Pass activities.
- Average monthly playtime per active player, with duration labels formatted as HH:MM.
- Average playtime per active player by five-year age group and calendar quarter.

Game, activity-date, age-group, and device-language filters will support exploration of player segments.

## Intended Users

| User | Analytical purpose |
|---|---|
| Product manager | Monitor engagement patterns and identify segments for further investigation |
| Game designer | Compare playtime and participation in Battle Pass activities |
| CRM / lifecycle marketer | Identify segments for engagement hypotheses and campaign experiments |

## Data Source

The project uses the GoIT coursework file `games_activity_combined (2.0).csv`.

[View the source CSV →](data/games_activity.csv)

The supplied CSV contains 44,012 rows and seven fields: user ID, activity date, game activity name, total seconds, device language, older-device indicator, and age.

Game names and activity types are combined in `game_activity_name`. A separate game dimension will be derived for filtering.

## Interpretation Boundaries

Recorded activity does not establish purchases, Battle Pass ownership, revenue, or campaign effectiveness.

Battle Pass participation means recorded positive time in an activity whose name contains “Battle pass”.

Players without recorded activity are not represented in active-player counts.

## Tools

Tableau · Calculated fields · Distinct user counts · Duration formatting · Heatmaps · Interactive dashboards

## Status

In development: source data supplied; metric validation and dashboard review are next.
