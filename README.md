* Executive Summary
* Project Overview
* Dataset Description
* Tools
* SQL Techniques
* Detailed Insights
* Business Recommendations
* Reproducibility Section

---

# Global War Economic Impact Analysis

## Executive Summary

Armed conflicts generate profound economic disruptions that extend far beyond the battlefield. This project investigates the macroeconomic consequences of major global conflicts by analysing key indicators such as **GDP performance, unemployment rates, inflation levels, and the financial cost of war**.

Using SQL-based analytical queries in MySQL, this analysis explores how wartime conditions affect national economic stability across multiple countries and regions.

The analysis reveals several critical economic patterns:

* Major conflicts can trigger **severe GDP contractions**, sometimes exceeding **60% declines in economic output**.
* Wartime economies often experience **extreme inflation spikes**, in some cases surpassing **100%**, due to supply disruptions and currency instability.
* Labour markets become highly volatile during conflict, producing **significant increases in unemployment**.
* The **financial cost of war** can reach **hundreds of billions of dollars**, creating long-term fiscal strain on national economies.

Overall, this project demonstrates how **SQL-driven data analysis can be used to quantify the economic consequences of geopolitical conflict**, transforming raw economic indicators into meaningful analytical insights.

---

# Project Overview

Wars have historically shaped not only political landscapes but also the economic stability of nations. Armed conflicts disrupt production systems, destroy infrastructure, destabilize currencies, and displace labour markets.

This project explores the **economic impact of global conflicts** using structured economic data. By analysing key economic indicators before and during war periods, the project identifies patterns of economic disruption across different countries and conflict types.

The primary goal of this analysis is to demonstrate how **data analytics techniques can be used to understand the macroeconomic consequences of war**.

---

# Project Objectives

The project aims to answer several key analytical questions:

* Which conflicts caused the **largest GDP declines**?
* Which countries experienced the **highest inflation during wartime**?
* How significantly does **unemployment increase during conflict**?
* Which wars imposed the **largest financial costs** on national economies?
* What economic patterns emerge when comparing **multiple conflicts globally**?

By addressing these questions, the project quantifies how wars affect economic systems across several key indicators.

---

# Dataset Description

The dataset contains economic indicators related to multiple global conflicts. Each record represents a **conflict-country pair** and captures economic conditions before and during war periods.

### Key Dataset Variables

| Column                             | Description                                                |
| ---------------------------------- | ---------------------------------------------------------- |
| Conflict_Name                      | Name of the conflict                                       |
| Conflict_Type                      | Type of conflict (civil war, international conflict, etc.) |
| Region                             | Geographic region affected                                 |
| Start_Year                         | Year the conflict began                                    |
| End_Year                           | Year the conflict ended                                    |
| Status                             | Conflict status (ongoing or ended)                         |
| Primary_Country                    | Country primarily affected                                 |
| Pre_War_Unemployment_%             | Unemployment rate before the war                           |
| During_War_Unemployment_%          | Unemployment rate during the war                           |
| GDP_Change_%                       | Percentage change in GDP during conflict                   |
| Inflation_Rate_%                   | Inflation rate during conflict                             |
| Cost_of_War_USD                    | Estimated financial cost of the war                        |
| Reconstruction_Cost_USD            | Estimated cost required to rebuild infrastructure          |
| Informal_Economy_Size_Pre_War_%    | Size of informal economy before conflict                   |
| Informal_Economy_Size_During_War_% | Informal economy during conflict                           |
| Poverty_Rate                       | Poverty levels before and during conflict                  |

These variables allow a **multi-dimensional analysis of economic disruption during armed conflicts**.

---

# Tools & Technologies

**Database**

MySQL

**Query Language**

SQL

**Analytical Techniques**

* Data cleaning
* Analytical calculations
* Window functions
* Ranking analysis
* Economic indicator comparison

---

# Key SQL Techniques Demonstrated

## 1. Window Functions for Analytical Ranking

Window functions were used to rank conflicts by economic damage based on GDP contraction.

```sql
SELECT 
    Conflict_Name,
    Primary_Country,
    `GDP_Change_%`,
    `Inflation_Rate_%`,
    RANK() OVER (ORDER BY `GDP_Change_%` ASC) AS Economic_damage_rank
FROM war_economic_impact_dataset;
```

Window functions are commonly used in analytics for ranking, trend analysis, and comparative performance evaluation.

---

## 2. Analytical Metric Engineering

Derived economic metrics were calculated directly within SQL queries to measure wartime economic shocks.

Example: unemployment spike calculation.

```sql
SELECT
    Conflict_Name,
    Primary_Country,
    ROUND(`During_War_Unemployment_%` - `Pre_War_Unemployment_%`,2) AS unemployment_spike
FROM war_economic_impact_dataset
ORDER BY unemployment_spike DESC;
```

This metric quantifies labour market disruption during conflicts.

---

## 3. Data Transformation and Formatting

Large financial values were transformed to improve interpretability.

```sql
SELECT
    Conflict_Name,
    Primary_Country,
    ROUND(Cost_of_War_USD / 1000000000,2) AS Cost_of_War_Bn
FROM war_economic_impact_dataset
ORDER BY Cost_of_War_Bn DESC;
```

Transforming raw values into billions allows easier comparison across conflicts.

---

## 4. Ordered Comparative Analysis

Sorting techniques were used to identify extreme values and economic outliers.

```sql
SELECT
    Conflict_Name,
    Primary_Country,
    `Inflation_Rate_%`
FROM war_economic_impact_dataset
ORDER BY `Inflation_Rate_%` DESC;
```

This enables quick identification of conflicts with the highest inflationary impact.

---

# Key Analytical Insights

## Economic Damage Ranking (GDP Impact)
<img width="550" height="377" alt="insight four" src="https://github.com/user-attachments/assets/04cd3e8e-48f7-4151-866d-8e49485ff8c4" />
<img width="650" height="371" alt="page 4" src="https://github.com/user-attachments/assets/927e0a6f-d779-415d-af28-fecac0f6b035" />

GDP contraction is one of the most direct indicators of wartime economic damage. The analysis reveals that conflicts involving large-scale infrastructure destruction tend to produce the deepest GDP declines.

For example, the **Israel–Hamas War (Gaza)** recorded the largest GDP contraction in the dataset at approximately **64.99%**, reflecting severe economic disruption caused by infrastructure destruction and halted economic activity.

Other conflicts such as the **Afghanistan War** and **World War II (Germany)** also show significant GDP contractions exceeding **40%**, demonstrating how prolonged conflicts can cripple national economies.

These results highlight that wars fought within national territories often produce the **most severe economic damage** because they directly disrupt domestic production systems.

---

## Inflation Spikes During War
<img width="633" height="370" alt="insight three" src="https://github.com/user-attachments/assets/3bc61164-f7ae-4da8-b30c-8288a1826120" />
<img width="653" height="370" alt="page 3" src="https://github.com/user-attachments/assets/d4c17dbf-9a9e-4919-a123-a48daf789bdc" />

Inflation frequently rises during wartime due to supply shortages, currency depreciation, and increased government spending on military operations.

The analysis shows that the **Iraq War** experienced the highest inflation rate in the dataset at approximately **113%**, indicating severe macroeconomic instability.

Similarly, conflicts such as those in the **Democratic Republic of Congo** also experienced extremely high inflation levels, reflecting fragile monetary systems and disrupted supply chains.

These findings demonstrate that wars often generate **inflationary pressure through supply shocks and fiscal imbalances**.

---

## Financial Cost of War
<img width="541" height="388" alt="Insight two" src="https://github.com/user-attachments/assets/f22bae0a-2aa5-4a78-beff-e3e05c1bae67" />
<img width="661" height="371" alt="page 2" src="https://github.com/user-attachments/assets/f0acd250-e505-4429-998d-589b6d6c7b7e" />

The financial cost of war includes military spending, destroyed infrastructure, humanitarian aid, and reconstruction requirements.

Some conflicts analysed in this dataset show total economic costs reaching **hundreds of billions of dollars**.

These costs often extend beyond the duration of the conflict, creating long-term fiscal challenges such as increased national debt and slower economic recovery.

---

## Unemployment Shock During Conflict
<img width="653" height="419" alt="Insight one" src="https://github.com/user-attachments/assets/994ccedb-b8df-47c8-9e1e-1c9579b82f51" />
<img width="661" height="368" alt="page 1" src="https://github.com/user-attachments/assets/12627531-ee40-44aa-bd97-a1f1aa2d1c6f" />

Labour markets are highly sensitive to wartime disruptions. Businesses shut down, industries collapse, and workforce displacement becomes widespread.

The analysis reveals significant unemployment spikes across multiple conflicts, often increasing by **double-digit percentage points** during wartime periods.

These labour market shocks frequently lead to increased poverty levels and growth in informal economic activity.

---

# Business & Policy Recommendations

## Strengthening Economic Resilience

Governments should develop economic resilience frameworks that help stabilize national economies during geopolitical crises.

These may include:

* diversified economic sectors
* strategic reserves of essential goods
* emergency fiscal stabilization funds

Such measures can help reduce the severity of economic collapse during conflict.

---

## Inflation Stabilization Policies

Central banks should prioritize mechanisms that control inflation during crises, including:

* currency stabilization policies
* stronger monetary controls
* strategic commodity reserves

These tools help prevent extreme inflation during wartime disruptions.

---

## Labour Market Recovery Programs

Post-conflict recovery strategies should focus on rebuilding labour markets through:

* infrastructure reconstruction programs
* workforce reskilling initiatives
* public employment programs

These initiatives accelerate economic recovery and reduce poverty.

---

## Long-Term Economic Recovery Planning

Reconstruction strategies should include:

* international development funding
* debt restructuring programs
* long-term infrastructure investment

These policies help restore economic growth in post-conflict economies.

---

# How to Reproduce This Analysis

To reproduce the analysis in this project, follow the steps below.

### 1. Import Dataset

Download the dataset and import it into a MySQL database.

Example table name:

```
war_economic_impact_dataset
```

---

### 2. Create the Database Table

Ensure the dataset columns match the schema used in the queries.

---

### 3. Run SQL Queries

Execute the SQL queries included in the repository to generate the analytical insights.

Queries can be found in:

```
/sql_queries/war_economic_analysis.sql
```

---

### 4. Review Insights

The query results can be used to:

* identify economic shocks caused by conflicts
* compare economic indicators across wars
* evaluate the financial cost of war

---

# Repository Structure

```
Global-War-Economic-Impact-Analysis
│
├── dataset
│   └── war_economic_impact_dataset.csv
│
├── sql_queries
│   └── war_economic_analysis.sql
│
└── README.md
```

---

# Future Improvements

Potential extensions of this project include:

* Building an **interactive Power BI dashboard**
* Performing **regional conflict trend analysis**
* Integrating **World Bank or IMF datasets**
* Applying **time-series economic modelling**

---
