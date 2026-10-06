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

## Key Findings

With all games, age groups, and device languages selected:

- Monthly active players increased from 47 in March to 150 in December 2022, peaking at 155 in November.
- Battle Pass participation peaked at 76.9% in April and reached 50.0% in December.
- Despite the lower participation rate, Battle Pass player counts increased from 40 in April to 75 in December.
- Average monthly playtime per active player peaked at 78 hours 35 minutes in June and ended at 53 hours 2 minutes in December.

These are descriptive findings from recorded activity, not evidence of acquisition, retention, purchases, or causal effects.

## The Story Behind the Dashboard

### A growing audience does not guarantee broader feature participation

The active-player base expanded across the recorded period. However, Battle Pass participation did not keep pace with that expansion.

In April, 40 of 52 active players participated in Battle Pass activities. By December, participation had grown to 75 players, but the overall active audience had reached 150. The participation rate therefore fell from 76.9% to 50.0%.

The feature reached more players in absolute terms while representing a smaller share of the audience. This makes both the player count and participation rate necessary for interpretation.

### Playtime adds another dimension to engagement

Average monthly playtime peaked in June at 78:35 per active player. December recorded 53:02, alongside a larger active audience than June.

Audience size and average playtime describe different aspects of engagement. Their movements should be investigated by game and player segment before proposing an explanation.

Monthly averages do not show whether the same players changed their behavior. Cohort analysis would be needed to distinguish changes within players from changes in audience composition.

### The heatmap identifies questions, not target audiences

Quarterly playtime varies across age groups, but the heatmap should be read alongside the number of players behind each cell.

A high average in a small group may reflect only a few players. Q1 contains March only, so its cumulative playtime is not directly comparable with three-month quarters.

The view helps identify segments for further analysis; it does not establish that age causes engagement differences or justify targeting decisions on its own.

## Business Applications and Recommendations

### 1. Monitor participation counts alongside percentages

Battle Pass participation fell from 76.9% in April to 50.0% in December, while the number of participating players increased from 40 to 75.

A lower participation rate does not necessarily mean fewer participants. Product teams should track both measures to distinguish changes in audience size from changes in feature engagement.

**Next step:** compare participation by game and player cohort. Confirm which games offer Battle Pass activities before interpreting differences.

### 2. Investigate playtime changes within comparable groups

Average monthly playtime per player peaked at 78:35 in June and reached 53:02 in December.

This comparison describes the monthly player population; it does not establish that individual players became less engaged.

**Next step:** compare returning and newly active players, then examine activity types and game-level patterns. Cohort analysis is needed to assess changes among the same players.

### 3. Use the age heatmap to guide further analysis

The heatmap highlights differences in average playtime across age groups and quarters.

**Next step:** review the number of players behind each cell before prioritizing a segment. Small groups can produce unstable averages. Q1 contains March only and should not be treated as a full quarter.

### 4. Connect engagement patterns to additional evidence

Product and game operations teams can use the dashboard to identify segments and periods worth investigating.

Marketing teams can use these observations to frame audience research and campaign hypotheses. Budget decisions require acquisition costs, campaign attribution and conversion data.

Battle Pass activity indicates participation, not a purchase. The dashboard does not measure revenue, retention or campaign effectiveness.

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
