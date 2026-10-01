# NYC Motor Vehicle Collisions, 2020

An analysis of crash patterns, road safety, contributing factors, injuries, and fatalities across New York City.

## Executive Summary

### Situation

New York City experiences motor vehicle collisions that affect road safety, public health, and urban mobility. This project analyzes NYC's 2020 motor vehicle collision records to understand where, when, and why crashes occur and the extent of their impact on road users. The analysis covers **74,881 crash records across 32 fields**, spanning January to August 2020, with a focus on borough-level patterns, temporal trends, contributing factors, injuries, and fatalities.

### Complication

The analysis reveals substantial differences in crash distribution and outcomes across boroughs, alongside data quality challenges. Brooklyn and Queens account for a combined 61% of crashes, 65% of injuries, and 62% of fatalities in the cleaned borough-level dataset. Crash volumes also declined by approximately 71% between January and April, coinciding with the COVID-19 lockdown period. However, missing borough information, unspecified contributing factors, and incomplete location fields limit the extent to which these patterns can be interpreted. Additionally, the unusual circumstances of 2020 make it difficult to generalize the findings to typical traffic conditions.

### Question

Where and when were motor vehicle collisions most concentrated across New York City's boroughs, what contributing factors were most frequently reported, and how did these collisions affect road users? Furthermore, what do these patterns reveal about potential road safety priorities?

### Answer

The analysis identifies clear geographical and temporal patterns in NYC's 2020 motor vehicle collisions. Brooklyn and Queens recorded the highest crash volumes, while collisions were most concentrated between 3 PM and 6 PM, accounting for approximately 20% of recorded crashes. Driver inattention or distraction was among the most frequently specified contributing factors across boroughs, alongside failure to yield and following too closely. Crash volumes declined sharply from January to April, consistent with changes in travel activity during COVID-19 lockdowns.

These findings provide a basis for understanding the distribution and circumstances of collisions across the city. Further investigation into high-risk roads, intersections, and fatality-related factors can help identify areas for more targeted road safety analysis and resource planning.

## Project Overview

### Objective

This project examines New York City's 2020 motor vehicle collision records to identify patterns in crash frequency, location, timing, contributing factors, injuries, and fatalities. The objective is to generate data-driven insights that can support road safety assessments, inform resource allocation, and improve understanding of traffic collision patterns.

### Dataset

The dataset contains **74,881 collision records across 32 fields**, covering January to August 2020.

| Category   | Fields                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------- |
| When       | Crash date, crash time, month, hour of collision, time period                               |
| Where      | Borough, ZIP code, latitude, longitude, location, on-street, cross-street, off-street names |
| Impact     | Persons injured and killed, including pedestrians, cyclists, and motorists                  |
| Causes     | Contributing factors and vehicle types for up to five vehicles                              |
| Identifier | Collision ID                                                                                |

## Data Quality and Cleaning

Borough was the most significant data quality issue in the original dataset, with a considerable number of records missing borough information.

| Dataset        | Borough populated | Missing |
| -------------- | ----------------: | ------: |
| Original       |    49,140 (65.6%) |  25,741 |
| After cleaning |    70,316 (93.9%) |   4,565 |

Missing borough values were recovered using available location information, increasing borough coverage from 65.6% to 93.9%. Approximately 82% of the original missing borough values were recovered, while the remaining 4,565 records (6.1%) were excluded from borough-level analysis.

Other fields also contain missing values. Secondary contributing factors and vehicle types are generally populated only when multiple vehicles are involved. For example, contributing factor 2 is present in approximately 79% of records, while factor 5 is present in fewer than 1%. ZIP code and cross-street information are also incomplete, with approximately 66% and 48% coverage, respectively.

## Analysis Approach

The project examines collision patterns across several dimensions:

- **Borough analysis:** Distribution of crashes, injuries, and fatalities across the five boroughs.
- **Monthly trends:** Changes in crash volumes over time for each borough.
- **Hourly trends:** Distribution of collisions across different hours and periods of the day.
- **Contributing factors:** Frequently reported factors associated with collisions in each borough.
- **Road user impact:** Injuries and fatalities involving pedestrians, cyclists, and motorists.
- **Hotspot analysis:** Identification of crash concentrations along roads and at intersections (planned).

The analysis combines descriptive statistics, grouped comparisons, temporal trends, and geographical analysis to identify patterns in collision frequency and severity.

## Key Findings

### 1. Collision Distribution by Borough

The cleaned dataset contains 70,316 crashes with assigned boroughs. Brooklyn and Queens recorded the highest collision volumes, together accounting for 61.4% of borough-assigned crashes.

| Borough       |    Crashes |    Share |  Killed |    Injured |
| ------------- | ---------: | -------: | ------: | ---------: |
| Brooklyn      |     22,716 |    32.3% |      38 |      8,527 |
| Queens        |     20,482 |    29.1% |      43 |      7,355 |
| Bronx         |     13,309 |    18.9% |      24 |      5,011 |
| Manhattan     |     11,229 |    16.0% |      17 |      3,497 |
| Staten Island |      2,580 |     3.7% |       8 |      108\* |
| **Total**     | **70,316** | **100%** | **130** | **24,498** |

_Staten Island's injury count requires verification._

Brooklyn recorded the highest number of crashes, injuries, and fatalities combined in absolute terms for crashes and injuries, while Queens recorded the highest number of fatalities. These figures describe the distribution of recorded collisions and casualties, not individual road users' risk of being involved in a crash.

### 2. Temporal Patterns

Collision frequency varied considerably throughout the period under review.

- **Peak hours:** Crashes were most frequent between 3 PM and 6 PM, accounting for approximately 20% of collisions.
- **Lowest activity:** Collision volumes were lowest between 2 AM and 4 AM.
- **Monthly trend:** Crash volumes declined by approximately 71% between January and April, coinciding with COVID-19 lockdowns and changes in travel activity.

![patterns](/images/borough_crashes_analysis.png)

These patterns highlight the importance of considering time of day and wider circumstances when examining collision frequency. The midnight spike observed in every borough may also be affected by missing or default crash-time entries.

### 3. Contributing Factors

Driver inattention or distraction was among the most frequently specified contributing factors across boroughs, alongside failure to yield and following too closely.

| Borough       | Top reported factor | Share | Other notable factor           |
| ------------- | ------------------- | ----: | ------------------------------ |
| Brooklyn      | Unspecified         |   29% | Distraction (25%)              |
| Queens        | Distraction         |   28% | Backing unsafely               |
| Bronx         | Unspecified         |   33% | Distraction (20%)              |
| Manhattan     | Distraction         |   28% | Improper passing or lane usage |
| Staten Island | Distraction         |   34% | Backing unsafely               |

Unspecified contributing factors account for a substantial proportion of records, particularly in Brooklyn and the Bronx. As these factors are recorded at the scene and are not necessarily confirmed causes, the results should be interpreted as reported contributing factors rather than definitive explanations for collisions.

### 4. Injuries and Fatalities

Across the cleaned borough-level dataset, 24,498 injuries and 130 fatalities were recorded.

Brooklyn and Queens together accounted for approximately 65% of recorded injuries and 62% of fatalities. The number of recorded fatalities varied from 8 in Staten Island to 43 in Queens.

Fatality counts are relatively small at the borough level, meaning that even a few additional cases can noticeably affect comparisons. Further analysis of fatalities by road user type and contributing factor is planned.

## Limitations

- **Partial-year coverage:** The dataset covers January to August 2020 and does not represent the full calendar year.
- **COVID-19 impact:** Lockdowns and changes in travel patterns during 2020 may have influenced collision frequency and distribution, limiting comparisons with other years.
- **Missing borough information:** Approximately 6.1% of records still lack an assigned borough and are excluded from borough-level analysis.
- **Incomplete location data:** ZIP codes, cross streets, and other location fields contain missing values, which may affect geographical analysis.
- **Unspecified contributing factors:** A substantial share of crashes have unspecified factors, limiting conclusions about the most common reported causes.
- **Reported rather than confirmed causes:** Contributing factors reflect information recorded in collision reports and should not be treated as independently verified causes.
- **Potential time-recording issues:** The higher number of collisions recorded at midnight may partly reflect missing or default time values.
- **Small fatality counts:** Borough-level fatality totals are relatively small and should be interpreted cautiously.
- **Unverified injury data:** Staten Island's recorded injury count requires validation before drawing comparisons.

## Conclusion

The analysis of NYC's January to August 2020 motor vehicle collision records identifies substantial differences in collision distribution across boroughs, clear temporal patterns, and frequently reported contributing factors. Brooklyn and Queens account for the majority of recorded collisions and associated casualties in the cleaned borough-level dataset, while afternoon hours show the highest collision frequency.

Although the findings provide useful insight into the city's collision patterns, incomplete data, unspecified contributing factors, and the exceptional circumstances of 2020 place important limits on interpretation. Further validation and hotspot analysis will help extend the project by examining where collisions are concentrated and how their severity varies across locations.

## Tools and Technologies

- **Python:** Data analysis and cleaning
- **Pandas / NumPy:** Data manipulation and statistical calculations
- **Matplotlib / Seaborn:** Data visualization
- **Jupyter Notebook:** Exploratory data analysis and documentation

## Project Status

**In progress** — Borough-level and temporal analyses have been completed. Hotspot analysis, further data validation, and additional investigation of fatality-related factors remain planned.
