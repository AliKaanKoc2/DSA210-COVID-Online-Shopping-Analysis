# DSA210 Individual Project: Analysis of COVID-19 Government Policies & Human Mobility

**DSA210 Individual Project - Fall 2025-2026 - Sabancı University**

*Prepared by : Ali Kaan Koç*

---

## Contents
1. [Overview](#overview)
2. [Motivation](#motivation)
3. [Research Question](#research-question)
4. [Hypotheses](#hypotheses)
5. [Project Goal](#project-goal)
6. [Data Collection](#data-collection)
7. [Data Sources and Description](#data-sources-and-description)
8. [Methodology](#methodology)
9. [Expected Outcomes](#expected-outcomes)
10. [Key Findings](#key-findings)
11. [Limitations](#limitations)
12. [Future Work](#future-work)
   
---

## Overview 
This project analyzes how COVID-19 government policy measures affected human mobility patterns across 11 countries, using data from the OXFORD COVID-19 Government Response Tracker(OxCGRT) and Google Community Mobility Reports. The analysis covers February 2020 through January 2021 and examines mobility across multiple sectors such as workplace,parks,retail,residential,transit in order to understand how populations responded to government restrictions and strict rules they enforced.

---
## Motivation 

As a data science student,I am interested in how government decisions translate into behavioral changes among the human population. The COVID-19 pandemic created an unprecedented large-scale natural experiment in which the governments worldwide implemented varying levels of restrictions, and populations responded differently.
Did people comply with orders because they were told to obey them, or because they were scared? I wanted to use data to explore the shift of human behavior.

---
## Research Question

**Research Question:**

- How did government COVID-19 policy measures affect human mobility patterns, and did these relationships vary across countries, mobility sectors, and pandemic phases?

---

## Hypotheses

**H1 — Policy-Mobility Association**  

**Null Hypothesis (H₀):** There is no significant correlation between government policy stringency and mobility changes.  
**Alternative Hypothesis (H₁):** Government policies and mobility are significantly correlated. ***Supported*** ✅

**H2 — Sector Spillover**  

**Null Hypothesis (H₀):** Mobility sectors respond independently to policies.  
**Alternative Hypothesis (H₁):** Mobility sectors move together (spillover behavior). ***Supported*** ✅

**H3 — Cross-Country Variation**  

**Null Hypothesis (H₀):** Policy-mobility relationships are consistent across countries.  
**Alternative Hypothesis (H₁):** Policy-mobility relationships differ significantly across countries. ***Supported*** ✅

**H4 — Temporal Weakening**  

**Null Hypothesis (H₀):** Policy-mobility relationships remain constant across pandemic phases.  
**Alternative Hypothesis (H₁):** Relationships weaken over time (behavioral adaptation). ***Supported*** ✅

A statistical significance threshold of α = 0.05 was used when evaluating p-values for hypothesis testing.

---

## Project Goal 

The goal of this project is to investigate how COVID-19 government restrictions affected human mobility patterns across different countries and sectors. Beyond visual exploration, the project aims to statistically validate policy-mobility relationships, use machine learning to predict mobility drops from policy indicators, and identify behavioral response clusters among countries.

---

## Data Collection 

For this project, I collected the data from numerous publicly available sources to create a large and reliable dataset. Below, I explain the steps of my data collection process in detail:

**1 - Looking for Relevant Data:**
I searched multiple open data platforms for datasets on pandemic-related policies and mobility data during pandemic, using keywords like “behavior shift”, "mobility" and “COVID-19 lockdown data” to guide the process.

**2 - Selecting Usefull Datasets:**
I focused on datasets that provided daily observations, country-level detail and could be merged by **date** and **country_code**. The Oxford COVID-19 Government Response Tracker offered policy indicators (C1–C8, stringency index), while Google Community Mobility Reports provided sector-level mobility changes.

**3 - Downloading and Storing Data:**
The dataset were downloaded in CSV format. The original Google Mobility dataset exceeded 1GB, so only relevant countries and variables were extracted. All files were cleaned and merged in the data cleaning notebook.

---
## Data Sources and Description
### **1 - Google Community Mobility Reports**
- **Content:** Dail percentage changes in visits to places compared to baseline, across six sectors: workplaces, retail & recreation, grocery & pharmacy, transit stations, parks, and residential.
- **Usage in Project:** Provides mobility data to measure how human behavior shifted during the pandemic.
- **Data:** `mobility_12_countries.csv`[https://github.com/AliKaanKoc2/DSA210-COVID-Online-Shopping-Analysis/blob/main/data/unprocessed/mobility_12_countries.csv]
- **Source:** [[https://www.google.com/covid19/mobility/](https://www.google.com/covid19/mobility/](https://www.google.com/covid19/mobility/)]
  
### **2 - COVID-19 Lockdown Policy Dataset**
- **Content:** Daily policy indicators (C1–C8) covering school closures, workplace closures, public event cancellations, gathering restrictions, public transport closures, stay-at-home requirements, internal movement restrictions, and international travel controls. Also includes a composite stringency index.
- **Usage in Project:** Provides government policy data to analyze relationships with mobility changes.
- **Source:** [OxCGRT GitHub Repository](https://github.com/OxCGRT/covid-policy-dataset)

| Indicator | Policy Name | Index Scale / Meaning |
| :--- | :--- | :--- |
| **C1** | **School Closing** | `0` - No measures <br> `1` - Recommend closing <br> `2` - Require closing (some levels) <br> `3` - Require closing (all levels) |
| **C2** | **Workplace Closing** | `0` - No measures <br> `1` - Recommend closing (or work from home) <br> `2` - Require closing (for some sectors) <br> `3` - Require closing (for all-but-essential) |
| **C3** | **Cancel Public Events** | `0` - No measures <br> `1` - Recommend cancelling <br> `2` - Require cancelling |
| **C4** | **Gathering Restrictions** | `0` - No restrictions <br> `1` - Restrictions on >1000 people <br> `2` - Restrictions on 100-1000 people <br> `3` - Restrictions on 10-100 people <br> `4` - Restrictions on <10 people |
| **C5** | **Close Public Transport** | `0` - No measures <br> `1` - Recommend closing (or reduce volume) <br> `2` - Require closing (or prohibit use) |
| **C6** | **Stay at Home** | `0` - No measures <br> `1` - Recommend not leaving house <br> `2` - Require not leaving house (with exceptions) <br> `3` - Require not leaving house (minimal exceptions) |
| **E1** | **Income Support** | `0` - No income support <br> `1` - Government replaces <50% of lost salary <br> `2` - Government replaces >50% of lost salary |

---
### Data analysis
After gathering these 2 datasets, I will use data cleaning steps to shape them into a consistent usable format. The goal is to drop the columns that are not relevant or empty and merge the parameters I need into a final dataset to conduct EDA later on.

1 - The cleaning steps included dropping irrelevant columns, fixing corrupted Excel-formatted dates, selecting essential variables (date, country, mobility sectors, policy indicators), and handling missing values. The policy and mobility datasets were merged by country and date into a single working dataset: `covid_merged_final.csv`.

2 - Exploratory Data Analysis : EDA was used to summarize patterns and explore relationships between policy stringency and mobility across sectors. Visualizations included time series plots, scatter plots, heatmaps, and cross-country comparisons to identify trends before statistical testing.

3 - Hypothesis testing
Spearman and Kendall correlation tests were used to evaluate H1–H4. These non-parametric tests were chosen because the data did not assume normal distribution.

4 — Machine Learning:
Supervised learning (Linear Regression, Lasso, Random Forest) was used to predict mobility from policy indicators. Classification models detected large mobility drops. K-Means clustering identified policy-response behavioral groups across countries. 

---

## Methodology

This project treats the COVID-19 pandemic as a natural experiment—different countries implemented different policies, and mobility data shows how people actually responded.

The analysis follows three stages:

**EDA:** I visualized mobility trends, compared countries, and looked at how sectors moved together. This helped me form hypotheses before testing them.

**Hypothesis Testing:** I used Spearman and Kendall correlation tests to validate policy-mobility relationships. I tested globally, by country, by sector, and across time periods to see where relationships hold and where they break down.

**Machine Learning:** I used regression (**Linear, Lasso, Random Forest**) to predict mobility from policy indicators, classification (**Logistic Regression, Random Forest**) to detect large drops, and clustering (**K-Means**) to find behavioral groups. For supervised models, I used a time-aware split (train on early months, test on later) to avoid leakage.

The goal is to find statistical associations—not prove causation, since this is observational data.

---
## Expected Outcomes 
- I expect that stronger government policies will be associated with larger mobility drops, especially in workplace and transit sectors. However, since people naturally resist being confined for long periods, I think compliance will weaken over time and mobility will start recovering even under restrictions. I also expect different countries to react on a diverse scale since every country has different culture, compliance norms, and trust in government.
---

## Key Findings
1. All four hypotheses supported (p < 0.05), meaning that there is significant evidence for accepting the fact that stronger government policies affect human mobility among various countries.
2. Policies explain ~24% of mobility variation (R² ≈ 0.24)
3. Policy effects weakened from Phase 1 to Phase 3 (pandemic fatigue)
4. Some countries reduced mobility voluntarily before strict mandates
5. ***Bottom line:*** Policies matter, but people are more complex than what models can fully capture.
---

## Limitations
- Observational data — correlation, not causation
- Limited to 11 countries due to data quality
---
## Future Work
As future work, if variables such as economic indicators or cultural context are added to the study with a higher count of countries, the findings may be able to predict mobility changes more accurately.
