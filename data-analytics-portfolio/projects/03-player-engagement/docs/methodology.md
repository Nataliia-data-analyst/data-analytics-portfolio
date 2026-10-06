# Methodology and Limitations

## Data and Scope

The analysis uses the GoIT coursework dataset stored in `data/games_activity.csv`.

The dashboard displays activity from March to December 2022. The source includes user identifiers, activity dates, activity names, recorded playtime in seconds, age and device language.

An activity record is not necessarily a session. Session counts and session duration are therefore not reported.

## Metric Definitions

### Monthly Players

Distinct users with an activity record in the selected month:

COUNTD([User Id])

This measures recorded monthly participation. It does not identify newly acquired or retained players.

### Battle Pass Players

Distinct users with positive recorded playtime in an activity whose name contains “battle pass”:

COUNTD(
    IF CONTAINS(LOWER([Game Activity Name]), "battle pass")
       AND [Total Seconds] > 0
    THEN [User Id]
    END
)

Each qualifying user is counted once within the selected period.

### Battle Pass Participation Rate

Battle Pass players divided by total players within the same month and filter scope.

The denominator includes all recorded players in the selected games, including games without Battle Pass activities. The rate therefore describes participation across the selected audience, rather than adoption among eligible players.

Battle Pass activity does not establish a purchase or paid subscription.

### Average Playtime per Player

SUM([Total Seconds]) / COUNTD([User Id])

For each month, total recorded playtime is divided by the number of distinct players in that month.

For each heatmap cell, the calculation uses total recorded playtime and distinct players within the corresponding age group and quarter.

Quarterly values are not averages of monthly averages. A player active in several months is counted once within the quarter.

### Duration Labels

Average playtime is displayed as hours and minutes in HH:MM format.

Whole minutes are calculated by truncating fractional minutes. The minute component always contains two digits.

These labels represent duration, not time of day. Values can exceed 24 hours.

### Age Groups

Players are grouped into five-year intervals using:

FLOOR([Age] / 5) * 5

For example, ages 20–24 belong to the same group.

### Game

The game name is extracted from the text before the colon in `game_activity_name`.

TRIM(SPLIT([Game Activity Name], ":", 1))

## Dashboard Filters

Activity date, age group, game and device language filters apply to all three dashboard worksheets.

Metrics are recalculated within the selected scope. Written full-period findings refer to all games, age groups and device languages unless stated otherwise.

## Validation Performed

- Source-based monthly calculations were checked against the reported player counts, Battle Pass participation and average playtime.
- Monthly dates preserve both month and year.
- Battle Pass participation requires positive recorded playtime.
- Duration labels use two-digit minutes.
- The heatmap calculates playtime per distinct player within each age group and quarter.

Selected reference values for the full audience:

| Month | Players | Battle Pass players | Participation | Average playtime |
|---|---:|---:|---:|---:|
| April 2022 | 52 | 40 | 76.9% | 74:34 |
| June 2022 | 81 | 59 | 72.8% | 78:35 |
| December 2022 | 150 | 75 | 50.0% | 53:02 |

## Interpretation Limits

- Q1 contains March only. Its playtime totals are not directly comparable with complete quarters.
- Blank heatmap cells indicate no recorded observations, rather than zero playtime.
- Small player groups can produce unstable averages. Review distinct-player counts before interpreting age-group differences.
- A growing monthly player count does not establish acquisition or retention.
- Changes in average playtime may reflect changes in audience composition rather than changes among the same players.
- Differences by age, game or language do not establish causal effects.
- Reporting completeness and the meaning of individual activity records require confirmation.
- Recorded playtime does not measure revenue, profitability, campaign effectiveness or player satisfaction.

Cohort analysis, feature eligibility, purchase records and acquisition data would be needed to answer those additional questions.
