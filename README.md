# India-Crime-Trends-Dashboard
This is a longitudinal analysis of Indian Crimes over a 13-year period

##  TABLE OF CONTENTS  

- [OVERVIEW](#overview)  
- [DATA SOURCE](#data-source)
- [TOOLS](#tools)  
- [DATA PROCESSING](#data-processing)  
- [SKILLS DEMONSTRATED](#skills-demonstrated)  
- [OBJECTIVES/PROBLEM STATEMENT](#objectivesproblem-statement)  
- [DATA ANALYSIS AND VISUALIZATION](#data-analysis-and-visualization)  
- [INSIGHTS](#insights)  
- [RECOMMENDATIONS](#recommendations)


# India Crime Trends Dashboard · Power BI

An interactive Power BI dashboard analysing 13 years of national crime data across India (2001–2013), built on the National Crime Records Bureau (NCRB) dataset. The project covers 36 states and Union Territories, 28 crime categories, and 468 records — uncovering long-term trends in violent crime, gender-based violence, and property crime at both national and state levels.

---

## OVERVIEW

This project transforms raw government crime statistics into a fully interactive, multi-page Power BI report. It was built end-to-end; from Excel data cleaning through Power Query transformation, star schema modelling, DAX measure development, and final visual design. The dashboard enables policymakers, researchers, and analysts to explore crime patterns across time and geography through dynamic slicers, KPI cards, trend lines, state rankings, and a gender violence deep-dive.


## DATA SOURCE

- **Dataset:** India Crime Statistics [National Crime Records Bureau (NCRB)]
- **Format:** Microsoft Excel (.xlsx)
- **Coverage:** 2001 to 2013 · 36 States and Union Territories
- **Records:** 468 rows · 35 columns
- **Crime Categories:** 28 IPC crime types including murder, rape, dowry deaths, theft, robbery, riots, and cruelty by husband
- **Additional fields:** State population, male/female population breakdown


## TOOLS

| Tool | Purpose |
|---|---|
| Microsoft Excel | Data cleaning, null handling, column renaming || Power BI Desktop | Data modelling, DAX, visualisation, dashboard design || Power Query (M) | Data transformation and dimension table creation || DAX | Measures for KPIs, rates, rankings, and YoY comparisons |


## DATA PROCESSING

**Excel (Pre-import cleaning)**
- Inspected dataset for blank rows, misaligned headers, and null values
- Replaced null entries in all crime columns with 0 using Find & Replace
- Shortened long column names (e.g. *Assault on Women with Intent to Outrage Her Modesty* → *Assault on Women*)
- Verified numeric columns were not stored as text

**Power Query (In Power BI)**
- Renamed main query to `CrimeData`
- Set `Year` and all crime count columns to Whole Number data type
- Created `DimYear` dimension table using `= {2001..2013}` converted to a table
- Created `DimState` dimension table by extracting distinct state names from `CrimeData`
- Replaced remaining nulls with 0 across all columns

**Data Model**
- Built a star schema with one fact table (`CrimeData`) and two dimension tables (`DimYear`, `DimState`)
- Established one-to-many relationships: `DimYear[Year] → CrimeData[Year]` and `DimState[State] → CrimeData[State]`
- Set filter direction to Single on both relationships
- Marked `DimYear` as the Date table for time-intelligence DAX functions
- Disabled Auto Date/Time to reduce model overhead


## SKILLS DEMONSTRATED

- Star schema data modelling in Power BI
- Power Query (M language) for data transformation and dimension table creation
- DAX measure writing: aggregations, DIVIDE(), RANKX(), CALCULATE(), DATEADD(), VAR/RETURN
- KPI design and year-over-year trend analysis
- Conditional formatting and data-driven colour scales in tables
- Cross-visual filtering and slicer configuration


## OBJECTIVES / PROBLEM STATEMENT

India's crime landscape over 2001–2013 presents a complex, multi-dimensional challenge for policymakers. Aggregate crime figures mask critical variation: certain categories rise sharply while others decline, and state-level disparities are obscured by national totals. The central analytical problem this dashboard addresses is threefold:

1. **Trend ambiguity** — Is crime in India rising or falling? The answer depends entirely on which category you examine.
2. **Gender violence severity** — Are gender-based crimes improving, worsening, or stable relative to overall crime growth?
3. **Geographic inequality** — Which states carry a disproportionate crime burden, and how does normalising for population change the rankings?

The dashboard was designed to make these distinctions visible and navigable for a non-specialist audience.


## DATA ANALYSIS AND VISUALIZATION

The report is structured across two pages with seven core visuals:

**Page 1 — National Overview**
- **KPI Cards (×4):** Total IPC Crimes, Total Rape Cases, Total Dowry Deaths, Murder trend — all with period-over-period change indicators
- **National Trends Line Chart:** Switchable between four views (All Crimes / Gender Violence / Property Crimes / Violent Crimes) 
- **Crime Composition Donut Chart:** Breakdown of all crime volume by category across the full 13-year period
<img width="1315" height="135" alt="image" src="https://github.com/user-attachments/assets/a1e5ae2e-91c4-4a86-abe7-87fd6ee16c0e" />
<img width="909" height="333" alt="image" src="https://github.com/user-attachments/assets/2be23a3f-2518-4184-8877-fecf88168e52" />

<img width="581" height="418" alt="image" src="https://github.com/user-attachments/assets/f3d889cb-df70-470c-a80f-f84811a79f92" />



**Page 2 — State Analysis**
- **State Crime Rate Bar Chart:** Top 10 states ranked by crimes per 100,000 population (2013)
- **State Rape Cases Bar Chart:** Top 10 states by absolute rape case count (2013)
- **Scatter Plot:** Rape cases vs. dowry deaths by state (2013) — reveals co-occurrence of gender crimes
<img width="611" height="394" alt="image" src="https://github.com/user-attachments/assets/9ff52a42-b516-4ab5-85dd-30ad050c71a9" />
<img width="591" height="401" alt="image" src="https://github.com/user-attachments/assets/bc58cd4c-d0ea-4401-baaa-795a4a0aa0ee" />
<img width="1208" height="421" alt="image" src="https://github.com/user-attachments/assets/3bc106fa-d42a-4123-adc6-07571a9b7718" />


**Slicers:** Year range (Between slider, 2001–2013) and State/UT (Dropdown with Select All)


## INSIGHTS

- **Total IPC crimes rose 49.7%** between 2001 and 2013, from approximately 7.1 million to 10.6 million cases nationally
- **Rape cases more than doubled** (+110%), rising from 64,300 in 2001 to 134,828 in 2013 — with a sharp single-year spike between 2012 and 2013 following the December 2012 Delhi gang rape case and subsequent legislative attention
- **Cruelty by husband rose 142%**, making it the fastest-growing gender crime category over the period — and the largest in absolute volume
- **Murder declined 8.3%** over the same period (144,808 → 132,804), representing one of the few categories showing genuine improvement
- **Madhya Pradesh, Rajasthan, and Tamil Nadu** recorded the highest rape case counts in 2013; when normalised by population, smaller states showed disproportionately high crime rates
- **Theft dominated crime composition** at approximately 27% of all IPC crime volume, followed by hurt/grievous hurt — property crime collectively accounted for the majority of reported cases
- **The scatter plot** revealed that states with high rape cases also tended to record high dowry deaths, suggesting shared structural drivers of gender-based violence rather than isolated incidents


## RECOMMENDATIONS

1. **Prioritise gender crime intervention in high-burden states.** The co-occurrence of rape and dowry deaths in the same states points to systemic gender inequality rather than random variation — policy responses should target the structural conditions, not individual crime types in isolation.

2. **Disaggregate the cruelty-by-husband data.** This category shows the steepest growth of all gender crimes yet receives less policy attention than rape. Future analysis should examine whether this reflects genuine increases or improved reporting following legal reforms.

3. **Use population-normalised rates, not raw counts, for resource allocation.** Raw crime counts bias attention toward large states. Crime rate per 100,000 population reveals a meaningfully different ranking that should inform where investigative and judicial capacity is deployed.

4. **Investigate the 2012–2013 rape spike further.** The single-year jump from ~99,000 to ~134,800 cases is too large to attribute to genuine crime increase alone. Separating reporting-rate change from actual incidence change requires survey data alongside administrative records.

5. **Extend the dataset beyond 2013.** The analysis period ends before several major legislative and policing reforms took effect. Updating the dashboard with post-2013 NCRB data would allow before-and-after evaluation of those interventions.
