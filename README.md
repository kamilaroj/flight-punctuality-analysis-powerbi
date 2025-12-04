# Flight Punctuality Analysis (2015–2017) – Power BI Dashboard

### A Data Analytics Project by **Kamila Rojek**

Welcome!
This repository contains an end-to-end data analytics project exploring flight punctuality at **Airport A** using historical data from **2015–2017**.
The goal is to identify operational bottlenecks, uncover delay patterns, and provide **data-driven recommendations** for airport operations and planning teams.

This README serves as a **business-focused case study** and a **technical overview** of the analysis.


# Project Background

Airport A is a major U.S. hub with more than **1.26 million arrivals and departures** during the 3-year period under review. The airport operates in a high-volume, capacity-constrained environment with dozens of domestic carriers.

As a data analyst working for the airport’s Operations & Planning department, the goal is to:

* understand structural causes of flight delays
* identify performance differences between airlines
* uncover seasonal and hourly punctuality patterns
* support operational decision-making with measurable insights

Insights and recommendations are provided in four key areas:

**Category 1:** Airline Performance //
**Category 2:** Long-term & Seasonal Trends //
**Category 3:** Weekly & Daily Patterns //
**Category 4:** Hourly Delay Dynamics & Arrival vs. Departure Effects

---

# Data Structure & Initial Checks

The dataset is sourced from airport flight operations records. After cleaning, cancelled and diverted flights were excluded, and “unpunctual” flights were defined as deviations of **≥ 5 minutes**.

**Data Source Structure:**

* **Flights table:** flight ID, airline, date, time, arrival/departure flag
* **Delays table:** scheduled vs. actual time, delay magnitude
* **Airlines table:** airline names and codes
* **Calendar table:** date attributes (week, month, season)

*(Add ERD here if you choose)* 

---

# Executive Summary

Airport A faces **significant punctuality challenges**, with **70.15%** of flights deviating from schedule by ≥ 5 minutes.
Three insights stand out:

1. **Large network carriers drive the majority of delays** (Southwest, American, SkyWest = >80% of all unpunctual flights).
2. **Delays follow a strong seasonal pattern**, with peaks in winter and year-end holidays.
3. **Night and early-morning hours show extreme delay spikes**, especially for arrivals, driven by cascading inbound delays.

These findings highlight structural operational pressures that require data-driven planning, resource allocation, and stronger coordination with major carriers.

*<img width="1718" height="461" alt="Bildschirmfoto 2025-12-04 um 14 09 14" src="https://github.com/user-attachments/assets/2ec5e41f-119b-41a1-9b29-fa379341dc09" />*

---

# Insights Deep Dive

---

## **Category 1: Airline Performance**

**Insight 1:** Large carriers (Southwest, American, SkyWest) account for **over 80%** of all unpunctual flights.
**Insight 2:** Smaller airlines such as Envoy, Frontier and JetBlue show **extreme average delays** of up to **40 minutes**, but represent only **3.5%** of all cases.
**Insight 3:** Network airlines with high volume show mid-range delays but dominate the airport’s overall reliability picture.
**Insight 4:** Performance differences suggest that **operational leverage** lies primarily with the top 5 airlines.

*<img width="1486" height="447" alt="Bildschirmfoto 2025-12-04 um 14 12 00" src="https://github.com/user-attachments/assets/d7b0110d-2d77-445d-a46f-9180f8d27d31" />*
*<img width="1496" height="864" alt="Bildschirmfoto 2025-12-04 um 14 12 16" src="https://github.com/user-attachments/assets/4704948a-038f-41ab-a872-cc0e71343d64" />*

---

## **Category 2: Annual & Seasonal Trends**

**Insight 1:** Punctuality worsened by nearly **5 percentage points** from 2015 to 2017.
**Insight 2:** Clear U-shaped seasonality: improvements in spring/summer, sharp declines in fall/winter.
**Insight 3:** December consistently shows the **highest unpunctuality (>72%)**.
**Insight 4:** Findings indicate **increasing structural strain**: traffic growth, capacity limits, and winter operations.

*<img width="1505" height="868" alt="Bildschirmfoto 2025-12-04 um 14 14 35" src="https://github.com/user-attachments/assets/2f4b329a-a008-4666-a46d-0addbe11dace" />*

---

## **Category 3: Weekly & Daily Patterns**

**Insight 1:** Weeks 50–52 experience the **highest peak** at **>75%** unpunctuality.
**Insight 2:** The rest of the year remains relatively stable (~70%).
**Insight 3:** No meaningful differences across weekdays → delays are **not calendar-driven**, but structural.
**Insight 4:** The consistency across weekdays highlights underlying operational bottlenecks.

*<img width="1498" height="859" alt="Bildschirmfoto 2025-12-04 um 14 15 32" src="https://github.com/user-attachments/assets/341e124b-e246-489f-bfa9-b9e188c1a86a" />*

---

## **Category 4: Hourly Delay Dynamics**

**Insight 1:** Early morning hours (2–4 AM) show **100% unpunctuality**.
**Insight 2:** Arrival flights suffer significantly more from cascading delays than departures.
**Insight 3:** Average delay durations exceed **200 minutes** during night peaks.
**Insight 4:** After early morning peaks, punctuality stabilizes around **73%**, with delays averaging **~40 minutes**.

*<img width="1052" height="600" alt="Bildschirmfoto 2025-12-04 um 14 23 34" src="https://github.com/user-attachments/assets/940c0a38-b634-4c71-846a-bc8cd56bd716" />*

---

# Recommendations

Based on the findings, the airport operations and planning team should consider:

1. **Prioritizing operational coordination with major carriers**, especially those contributing the highest volume of delays.
2. **Implementing winter operations planning**, including additional resources for ground handling and deicing.
3. **Developing a predictive model** for weeks 50–52 and December peak travel.
4. **Strengthening arrival management** to reduce cascading inbound delays.
5. **Optimizing gate and turnaround scheduling** during early-morning peak disruption windows.

---

# Assumptions and Caveats

To ensure analytical clarity, several assumptions were applied:

* Cancelled and diverted flights were excluded due to low operational comparability.
* “Unpunctual” was defined as ≥ 5 minutes, following industry standards.
* Delay duration outliers over 500 minutes were reviewed and retained unless clearly erroneous.
* Time records were normalized to local airport time.
* Early-morning spikes were assumed to be due to inbound overnight delays (consistent with operational patterns).

---

# Additional Resources

* **Power BI Dashboard:** [link]
* **Raw PDF Report:** included in this repository
* **SQL Scripts (Cleaning + Exploratory Checks):** [link, if applicable]

---

# Thank You!


