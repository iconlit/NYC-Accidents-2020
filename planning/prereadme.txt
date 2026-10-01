Project Summary: NYC Motor Vehicle Collisions, 2020

Objective
This project analyzes New York City's 2020 motor vehicle collision records to understand where, when, and why crashes occur, and what harm they cause. The goal is to identify patterns that can inform safety priorities and resource allocation.

Data
The dataset contains 74,881 crash records across 32 fields. These cover:

When: crash date, time, month, hour of collision, and time period of day
Where: borough, zip code, latitude/longitude, and street names
Impact: persons injured and killed, broken down by pedestrians, cyclists, and motorists
Causes: up to five contributing factors and five vehicle types per crash

Data Quality and Cleaning
Borough was the most significant gap in the raw data, with only 49,140 of 74,881 records populated (65.6%). Missing values were filled using the available location information, which raised coverage to 70,316 records (93.9%). Missing borough values fell from 25,741 to 4,565, so about 82% of the original gaps were recovered. The remaining 4,565 records (6.1%) still lack a borough.

Other fields have expected gaps. Secondary contributing factors and vehicle types are populated only when more than one vehicle is involved (e.g., factor 2 is present in about 79% of records, factor 5 in under 1%). Location fields such as zip code (about 66%) and cross street (about 48%) are also incomplete.

Analysis Approach

Crash volume by borough over time (monthly trends)
Crash volume by borough across hours of the day
Contributing factors and vehicle types involved
Injury and fatality counts by road user type (pedestrian, cyclist, motorist)

Key Findings
(to be completed once the results are finalized)

Limitations

About 6% of crashes still have no borough assigned
Zip code and street name fields are sparsely populated
Contributing factors are as recorded at the scene, so they reflect reported cause rather than confirmed cause
2020 was an atypical year because of COVID-19 lockdowns, so patterns may not generalize to other year