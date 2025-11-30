# DSA210 Individual Project: Analysis of the Impact of COVID-19 on Online Shopping Behavior and Product Category Demand

**DSA210 Individual Project - Fall 2025-2026 - Sabancı University**

*Prepared by : Ali Kaan Koç*

---

## Contents
1. [Overview](#overview)
2. [Motivation](#motivation)
3. [Research Question & Sub-Questions](#research-question--sub-questions)
4. [Hypothesis](#hypothesis)
5. [Project Goal](#project-goal)
6. [Data Collection](#data-collection)
7. [Data Sources](#data-sources)
8. [Expected Outcomes](#expected-outcomes)
   
---

## Overview 
This project examines the impact of the COVID-19 pandemic on global shopping practices, mainly focusing on fluctuations in purchasing behavior across various product categories. By analyzing daily purchase counts and products prices, i expect to understand how consumer behavior shifted during the pandemic period. The comparison between pre-pandemic, pandemic and post-pandemic periods will show if the lockdowns were one of the leading reasons why people started shopping on a greater scale, and if the shift and the scale remained the same after the lockdowns were lifted.

---
## Motivation 

As a data science student, I am interested in how major global events influence shopping habits and everyday decision-making. The COVID-19 pandemic created one of the most significant shifts in consumer habits,which increased shopping dependence.Like many households, mine also began relying heavily on digital platforms for both essential and non-essential purchases during lockdown periods. Studying this shift will help me explore how consumer preferences change under disruptive conditions using data-driven analysis.

---
## Research Question & Sub-Questions 

**Research Question:**

- How did global shopping demand and category-level purchasing behavior change across the pre-pandemic, pandemic, and post-pandemic periods of COVID-19?


**Sub-Questions**
- Did shopping demand rise significantly during the pandemic compared to the pre-pandemic period?
- Which product categories experienced the strongest changes in daily demand during lockdown restrictions?
- Do lockdown restrictions lead to noticeable changes in daily shopping demand?
- Did demand remain permanently above pre-pandemic levels after restrictions were lifted?

---

## Hypothesis 

**Null Hypothesis (H₀)**
There is no significant difference in daily shopping demand between the pre-pandemic and pandemic periods.

**Alternative Hypothesis (H₁)**  
Daily shopping demand increased significantly during the pandemic compared to the pre-pandemic period.

A statistical significance threshold of α = 0.05 will be used when evaluating the p-value for hypothesis testing.

---

## Project Goal 
The project investigates how the COVID-19 pandemic changed the way people buy products on platforms globally, especially which types of categories products people bought more and how this varied from country to country.
I also look at how lockdown restrictions affected the scale of purchases and if people kept shopping online more often even though the restriction were lifted.

---

## Data Collection 

For this project, I collected the data from numerous publicly available sources to create a large and reliable dataset. Below, I explain the steps of my data collection process in detail:

**1 - Looking for Relevant Data:**
I searched multiple open data platforms for datasets on online sales and pandemic-related policies, using keywords like “online sales” and “COVID-19 lockdown data” to guide the process.

**2 - Selecting Usefull Datasets:**
I focused on datasets that provided daily purchase activity, product category and country details during the analysis period. In order to connect shopping patterns with COVID-19 period, I also included a global pandemic dataset that shows the date range of lockdowns.

**3 - Downloading and Storing Data:**
The datasets were downloaded in CSV format from Kaggle and stored in my project repository. All of the necessary files will be cleaned and merged in the future.

---
## Data Sources 
### ** 1 - E-commerce Dataset (2018) **
- **Content:** Product category, product purchase date, value of the product.
- **Usage in Project:** It will provide a solid foundation to the pre-pandemic period and create a basis for comparison.
- **Data:** `E-commerce Dataset.csv` [https://github.com/AliKaanKoc2/DSA210-COVID-Online-Shopping-Analysis/blob/main/data/unprocessed/E-commerce%20Dataset.csv]
- **Source:** [https://www.kaggle.com/datasets/mervemenekse/ecommerce-dataset/discussion?sort=hotness]
  
### ** 2 - Global Online Sales Dataset (2020–2025)**
- **Content:** Product category, item purchase date, value of the product and country that it was purchased from, information about review.
- **Usage in Project:** It will be a baseline for pandemic and post-pandemic period.
- **Data:** `online_sales_dataset_for_2020-2025.csv` [https://github.com/AliKaanKoc2/DSA210-COVID-Online-Shopping-Analysis/blob/main/data/unprocessed/online_sales_dataset_for_2020-2025.csv]
- **Source:** [https://www.kaggle.com/datasets/yusufdelikkaya/online-sales-dataset]

### ** 3 - COVID-19 Lockdown Policy Dataset**
- **Content:** Contains every countries case count, the strictness of the lockdown, the specific dates of the lockdown for all countries.
- **Key Variable:** A binary (0-1) variable `is_lockdown` will be created and included in the merged csv files.
- **Usage in Project:** The created variable will show the dates when the country had a lockdown.
- **Data:** `covid_policy-lockdown_tracker.csv` [https://github.com/AliKaanKoc2/DSA210-COVID-Online-Shopping-Analysis/blob/main/data/unprocessed/covid_policy-lockdown_tracker.csv]
- **Source:** [https://github.com/OxCGRT/covid-policy-tracker/blob/master/data/OxCGRT_nat_latest.csv]
  

---
### Data analysis
After gathering these 3 datasets, I will use data cleaning steps to shape them into a consisten usable format. The goal is to drop the variables that are not relevant or empty and merge the parameters I need into a final dataset to conduct EDA later on.

1- The cleaning steps included droping irrelevant rows, unusable or dataset-specific metrics like customerID, selecting essential columns like date, product category, product price, quantities.
Some datasets used different names for the same variable like product_category and category, while merging I changed the names of the columns so that when we conduct analysis the code won't treat them like different individuals. After that, I merged the datasets consecutively based on their dates and sorted the final dataset to ensure it was in proper chronological order.

2- EDA : In this part we will use exploratory data analysis to summarize patterns, describe the data and find relationship between different metrics.
I will use various graphics like box plots, time series analysis, histograms, heatmaps, line-plots to either describe the data or search for paterns/relationships.

3-Hypothesis testing
I will use Mann–Whitney U and Kruskal–Wallis test to find if the evidence we have is significant enough to reject Null Hypothesis. In our code we saw that p value is e-6 so we can reject null hypothesis

---
## Expected Outcomes 
- I expect that shopping trends will increase immensely compared to the pre-pandemic period, especially in categories linked to essential needs such as groceries and household products. Additionally, the alteration in human shopping habits will keep them making general purchases more compared to pre-Covid period.

