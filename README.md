# NYC Motor Vehicle Collisions, 2020

An analysis of crash patterns, road safety, contributing factors, injuries, and fatalities across New York City.

## Executive Summary

### Situation

New York City experiences motor vehicle collisions that affect road safety, public health, and urban mobility. This project analyzes NYC's 2020 motor vehicle collision records to understand where, when, and why crashes occur and the extent of their impact on road users. The analysis covers **74,881 crash records across 32 fields**, spanning January to August 2020, with a focus on borough-level patterns, road-level hotspots, temporal trends, contributing factors, injuries, and fatalities.

### Complication

The analysis reveals substantial differences in crash distribution and outcomes across boroughs, alongside data quality challenges. Brooklyn and Queens account for a combined 61% of crashes, 65% of injuries, and 62% of fatalities in the cleaned borough-level dataset. Crash volumes also declined by approximately 71% between January and April, coinciding with the COVID-19 lockdown period. At the road level, crashes are concentrated on a small number of highways: the ten most crash-prone roads account for roughly 9% of all records, and eight of them are expressways, parkways, or drives. However, missing borough information, unspecified contributing factors, and incomplete location fields limit the extent to which these patterns can be interpreted. Additionally, the unusual circumstances of 2020 make it difficult to generalize the findings to typical traffic conditions.

### Question

Where and when were motor vehicle collisions most concentrated across New York City's boroughs and roads, what contributing factors were most frequently reported, and how did these collisions affect road users? Furthermore, what do these patterns reveal about potential road safety priorities?

### Answer

The analysis identifies clear geographical and temporal patterns in NYC's 2020 motor vehicle collisions. Brooklyn and Queens recorded the highest crash volumes, while collisions were most concentrated between 3 PM and 6 PM, accounting for approximately 20% of recorded crashes. Driver inattention or distraction was among the most frequently specified contributing factors across boroughs, alongside failure to yield and following too closely. Crash volumes declined sharply from January to April, consistent with changes in travel activity during COVID-19 lockdowns.

At the road level, the **Belt Parkway** is the clear hotspot with 1,245 crashes, about 1.7 times the next highest road (Long Island Expressway, 745). The Grand Central Parkway and Cross Island Parkway recorded the most fatalities among the top ten roads despite lower crash counts. Distraction and following too closely dominate the reported factors on the highest-crash highways.

These findings provide a basis for understanding the distribution and circumstances of collisions across the city. They point to highway corridors in Brooklyn and Queens, and to the weekday afternoon peak, as natural starting points for targeted road safety analysis and resource planning.

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
- **Monthly trends:** Changes in crash volumes over time for each borough and for the highest-crash roads.
- **Hourly trends:** Distribution of collisions across different hours and periods of the day.
- **Contributing factors:** Frequently reported factors associated with collisions in each borough and on the highest-crash roads.
- **Road user impact:** Injuries and fatalities involving pedestrians, cyclists, and motorists.
- **Hotspot analysis:** Identification of crash concentrations along roads, ranked by crashes, injuries, and fatalities, with monthly, hourly, and contributing-factor breakdowns for the top ten roads.

The analysis combines descriptive statistics, grouped comparisons, temporal trends, and geographical analysis to identify patterns in collision frequency and severity.

## Key Findings

### 1. Collision Distribution by Borough

The cleaned dataset contains 70,316 crashes with assigned boroughs. Brooklyn and Queens recorded the highest collision volumes, together accounting for 61.4% of borough-assigned crashes.

| Borough       |    Crashes |    Share |  Killed |    Injured | Injured per 100 crashes |
| ------------- | ---------: | -------: | ------: | ---------: | ----------------------: |
| Brooklyn      |     22,716 |    32.3% |      38 |      8,527 |                    37.5 |
| Queens        |     20,482 |    29.1% |      43 |      7,355 |                    35.9 |
| Bronx         |     13,309 |    18.9% |      24 |      5,011 |                    37.6 |
| Manhattan     |     11,229 |    16.0% |      17 |      3,497 |                    31.1 |
| Staten Island |      2,580 |     3.7% |       8 |      108\* |                   4.2\* |
| **Total**     | **70,316** | **100%** | **130** | **24,498** |                    34.8 |

_\*Staten Island's injury count requires verification. Its injury rate (about 4 per 100 crashes) is roughly one-ninth of every other borough, which suggests a data or aggregation issue rather than a real difference._

Brooklyn recorded the most crashes and injuries, while Queens recorded the most fatalities. These figures describe the distribution of recorded collisions and casualties, not individual road users' risk of being involved in a crash, as they are not adjusted for population, traffic volume, or road length.

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

### 5. Crash Hotspots by Road

Ranking records by the street on which the crash occurred shows that collisions are heavily concentrated on a few major roads. The ten most crash-prone roads recorded **6,787 crashes, about 9% of all 74,881 records**, along with 18 deaths and 3,245 injuries.

| Rank | Road                       | Crashes | Killed | Injured | Injured per 100 crashes |
| ---: | -------------------------- | ------: | -----: | ------: | ----------------------: |
|    1 | Belt Parkway               |   1,245 |      1 |     692 |                    55.6 |
|    2 | Long Island Expressway     |     745 |      0 |     284 |                    38.1 |
|    3 | Brooklyn Queens Expressway |     740 |      3 |     332 |                    44.9 |
|    4 | FDR Drive                  |     729 |      1 |     323 |                    44.3 |
|    5 | Major Deegan Expressway    |     591 |      2 |     338 |                    57.2 |
|    6 | Broadway                   |     584 |      1 |     251 |                    43.0 |
|    7 | Grand Central Parkway      |     581 |      5 |     342 |                    58.9 |
|    8 | Atlantic Avenue            |     534 |      0 |     214 |                    40.1 |
|    9 | Cross Bronx Expressway     |     526 |      1 |     250 |                    47.5 |
|   10 | Cross Island Parkway       |     512 |      4 |     219 |                    42.8 |

![hotspot summary](/images/top_streets_accidents.png)

Key observations:

- **The Belt Parkway stands apart.** With 1,245 crashes it recorded about 1.7 times as many as the next road and nearly 700 injuries, more than any other road in the top ten.
- **Highways dominate.** Eight of the ten roads are expressways, parkways, or drives. Only Broadway and Atlantic Avenue are surface streets.
- **Volume and severity do not line up.** The Grand Central Parkway had the most fatalities (5) and the highest injury rate (58.9 per 100 crashes) despite ranking seventh by crashes. The Cross Island Parkway (4 deaths) and the Brooklyn Queens Expressway (3 deaths) follow. The Long Island Expressway ranks second by crashes but had no recorded fatalities and the lowest injury rate (38.1).
- **Fatalities are few.** The 18 deaths across the top ten roads are roughly 14% of the 130 recorded at borough level (indicative only, since the two counts rest on different record subsets). Per-road comparisons of 0 to 5 deaths should be read cautiously.

#### Monthly Pattern on Hotspot Roads

Combined crashes on the top ten roads fell from 1,255 in January to 438 in April, a decline of about 65%, slightly smaller than the citywide drop. Most roads bottomed out in April and recovered only partially by August.

- **Belt Parkway** peaked in February (225), fell to 74 in April, and recovered to 161 by July, remaining the highest-crash road in every month except April.
- **FDR Drive** was the most resilient road, falling only about 37% (128 to 81) and overtaking the Belt Parkway in April.
- **Brooklyn Queens Expressway** had the largest rebound in August (94), up from 44 in April.

#### Hourly Pattern on Hotspot Roads

![street patterns](/images/street_crashes_analysis.png)

- **Afternoon peak.** Most roads peak between 2 PM and 6 PM. The Belt Parkway recorded 362 crashes between 3 PM and 7 PM, about 29% of all its crashes, with a peak of 98 at 3 PM.
- **Morning commuter peaks.** The Long Island Expressway (42 and 43 crashes at 6 and 7 AM) and the FDR Drive (38 at 7 AM) show a distinct morning peak, and the Grand Central Parkway rises from 5 AM.
- **Midnight spike.** Several roads, notably the Belt Parkway (62 at midnight, 65 at 11 PM), show elevated counts around midnight, which may partly reflect default time entries (see Limitations).
- **Quietest period.** Counts are lowest between 2 AM and 4 AM on most roads.

#### Contributing Factors on Hotspot Roads

Contributing factors below refer to the first vehicle in each crash.

| Road                       | Top factor                       | Second factor                    | Third factor                  |
| -------------------------- | -------------------------------- | -------------------------------- | ----------------------------- |
| Belt Parkway               | Distraction (360, 29%)           | Following too closely (206, 17%) | Unspecified (190, 15%)        |
| Long Island Expressway     | Following too closely (234, 31%) | Distraction (217, 29%)           | Unsafe lane changing (59, 8%) |
| Brooklyn Queens Expressway | Distraction (209, 28%)           | Following too closely (193, 26%) | Unspecified (84, 11%)         |

Distraction and following too closely together account for well over half of the reported first-vehicle factors on the long expressways, which is consistent with high-speed, high-volume stop-and-go conditions. Unsafe lane changing and unsafe speed also appear among the leading factors on these roads. These are reported factors rather than confirmed causes.

## Limitations

- **Partial-year coverage:** The dataset covers January to August 2020 and does not represent the full calendar year.
- **COVID-19 impact:** Lockdowns and changes in travel patterns during 2020 may have influenced collision frequency and distribution, limiting comparisons with other years.
- **Missing borough information:** Approximately 6.1% of records still lack an assigned borough and are excluded from borough-level analysis.
- **Incomplete location data:** ZIP codes, cross streets, and other location fields contain missing values, which may affect geographical analysis.
- **Street-level ranking is not exposure-adjusted:** Roads are ranked by raw crash counts. Long, high-traffic highways naturally record more crashes than short or low-traffic streets, so the rankings show where crashes were recorded, not which roads are the most dangerous per mile or per vehicle.
- **Street name recording:** Hotspot counts depend on the on-street field. Crashes with missing street names, and crashes recorded at intersections under different street names or spellings, may be undercounted or split across entries. Highway crashes are also more likely to be logged under a single road name than surface-street crashes, which are spread across many streets.
- **Unspecified contributing factors:** A substantial share of crashes have unspecified factors, limiting conclusions about the most common reported causes.
- **Reported rather than confirmed causes:** Contributing factors reflect information recorded in collision reports and should not be treated as independently verified causes.
- **Potential time-recording issues:** The higher number of collisions recorded at midnight may partly reflect missing or default time values.
- **Small fatality counts:** Borough-level and road-level fatality totals are small and should be interpreted cautiously.

## Conclusion

The analysis of NYC's January to August 2020 motor vehicle collision records identifies substantial differences in collision distribution across boroughs, clear temporal patterns, and frequently reported contributing factors. Brooklyn and Queens account for the majority of recorded collisions and associated casualties in the cleaned borough-level dataset, while afternoon hours show the highest collision frequency.

The hotspot analysis shows that crashes are concentrated on a small set of major highways, led by the Belt Parkway, with distraction and following too closely as the leading reported factors. Roads with the highest crash counts are not always those with the most severe outcomes, as the Grand Central Parkway and Cross Island Parkway illustrate.

Although the findings provide useful insight into the city's collision patterns, incomplete data, unspecified contributing factors, and the exceptional circumstances of 2020 place important limits on interpretation.

## Tools and Technologies

- **Python:** Data analysis and cleaning
- **Pandas / NumPy:** Data manipulation and statistical calculations
- **Matplotlib / Seaborn:** Data visualization
- **Jupyter Notebook:** Exploratory data analysis and documentation

## Project Status

**In progress** — Borough-level, temporal, and road-level hotspot analyses have been completed. Data validation (notably Staten Island injuries), intersection-level hotspots, and additional investigation of fatality-related factors remain planned.
