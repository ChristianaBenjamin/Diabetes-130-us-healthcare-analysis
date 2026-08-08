# Healthcare Data Quality & Patient Profile Analysis

## Project Overview

This project analyzes the **Diabetes 130-US Hospitals for Years 1999–2008** dataset using Python to assess data quality, understand patient-encounter characteristics, explore hospital utilization and diabetes medication patterns, and investigate hospital readmission outcomes.

The project follows a practical data-analysis workflow:

**Data Understanding → Data Quality Assessment → Data Cleaning → Exploratory Data Analysis → Insights → Recommendations**

> **Important:** Each row represents a **hospital encounter**, not necessarily a unique patient. Some patients appear in multiple encounters.

## Business Problem

Historical healthcare datasets can contain missing values, inconsistent categorical entries, and other quality issues that can affect the reliability of analysis and future predictive modeling.

This project addresses the need to:

- assess and improve the quality of the dataset;
- understand the characteristics of diabetic hospital encounters;
- explore hospital utilization and medication patterns; and
- identify initial patterns associated with readmission.

## Objectives

1. Understand the structure and variables in the dataset.
2. Assess missing values, duplicates, inconsistent values, and potential data-quality issues.
3. Clean the dataset and document key cleaning decisions.
4. Explore patient demographics and hospital utilization.
5. Examine diabetes medication usage and medication changes.
6. Analyze readmission patterns.
7. Translate findings into practical recommendations and identify opportunities for further analysis.

## Dataset

**Dataset:** Diabetes 130-US Hospitals for Years 1999–2008

The dataset contains **101,766 hospital encounters and 50 variables** before cleaning. It represents ten years of clinical care across 130 US hospitals and integrated delivery networks.

### Data source

UCI Machine Learning Repository:

https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008

The original dataset is described in:

> Strack, B., DeShazo, J. P., Gennings, C., Olmo, J. L., Ventura, S., Cios, K. J., & Clore, J. N. (2014). *Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records*. BioMed Research International.

## Tools & Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Data Quality & Cleaning

The dataset contained several quality issues that were investigated before EDA.

Key cleaning decisions included:

- Converted `?` placeholder values to missing values.
- Replaced missing race values with `Unknown`.
- Standardized the three `Unknown/Invalid` gender entries to `Unknown`.
- Removed `weight` because approximately 98,569 of 101,766 observations were missing.
- Filled missing values in the diagnosis columns with `Unknown`.
- Removed `max_glu_serum`, `A1Cresult`, `medical_specialty`, and `payer_code` because of substantial missingness and their limited relevance to the project's defined analysis scope.
- Retained repeated `patient_nbr` values because the dataset represents hospital encounters; repeated patients may have multiple valid encounters.
- Confirmed that there were no exact duplicate rows.

After cleaning, the working dataset contained **101,766 encounters and 45 variables**.

## Exploratory Data Analysis

### Patient Demographics

#### Gender

![Gender distribution](images/gender_distribution.png)

Female encounters represented a slightly larger share of the dataset than male encounters, while unknown gender values were negligible.

#### Age

![Age distribution](images/age_distribution.png)

The dataset was concentrated among older adults, particularly encounters involving patients aged 60–80 years.

#### Race

![Race distribution](images/race_distribution.png)

Caucasian encounters represented the largest racial group, followed by African American encounters. Other racial groups represented considerably smaller proportions of the dataset.

### Hospital Utilization

#### Length of Hospital Stay

![Length of stay](images/length_of_stay.png)

Most encounters involved relatively short hospital stays, with the distribution concentrated around 2–6 days. The average length of stay was approximately 4.4 days.

### Diabetes Medication

#### Top 10 Diabetes Medications

![Top 10 diabetes medications](images/top_10_diabetes_medications.png)

Insulin and metformin were the most frequently recorded diabetes medications in the dataset.

### Readmission

#### Overall Readmission Distribution

![Readmission distribution](images/readmission_distribution.png)

More than half of encounters had no recorded readmission, while 11.2% involved readmission within 30 days and 34.9% involved readmission after 30 days.

#### Early Readmission by Age Group

![Early readmission by age](images/early_readmission_by_age.png)

The proportion of encounters followed by readmission within 30 days varied across age groups, with the highest proportions observed among several older age groups.

#### Readmission by Medication Change

![Readmission by medication change](images/readmission_by_medication_change.png)

Encounters involving a diabetes medication change showed slightly higher proportions of both early and later readmission compared with encounters where medication was unchanged. This is an association and does not establish that medication changes cause readmission.

## Key Findings

- The dataset contains over 101,000 diabetic hospital encounters, with older adults—particularly those aged 60–80—forming a large share of the population.
- Female encounters slightly outnumbered male encounters.
- Hospital stays were generally short, with most encounters lasting between 2 and 6 days.
- Insulin and metformin were the most frequently recorded diabetes medications.
- 53.9% of encounters had no recorded readmission, 34.9% were associated with readmission after 30 days, and 11.2% were associated with readmission within 30 days.
- Length of stay differed only modestly across readmission groups, suggesting that it is not a strong differentiating factor on its own.
- Encounters involving medication changes showed slightly higher readmission proportions than encounters without medication changes.

## Recommendations

1. **Prioritize enhanced follow-up for potentially higher-risk encounters.**  
   Medication changes were associated with slightly higher readmission proportions. Patients requiring treatment adjustments may benefit from stronger discharge planning, medication counseling, and timely post-discharge follow-up.

2. **Develop a readmission-risk prediction model.**  
   Future work should combine demographic, medication, utilization, and clinical variables to identify encounters with elevated readmission risk.

3. **Strengthen medication-management processes.**  
   Medication reconciliation, patient education, and adherence support should be considered as part of discharge planning for diabetic patients.

4. **Improve healthcare data quality.**  
   Better completeness and standardization of clinically relevant variables would improve future descriptive and predictive analyses.

5. **Move from descriptive analysis to multivariate modeling.**  
   Future analysis should investigate how multiple variables jointly relate to readmission rather than assessing factors independently.

## Limitations

- This is an exploratory analysis and does not establish causal relationships.
- The dataset represents hospital encounters rather than unique patients, so some patients appear multiple times.
- Several variables contained substantial missing data and were excluded from this analysis.
- The analysis is based on historical data from 1999–2008 and may not represent current clinical practice.

## Future Work

The next stage of this project could include:

- feature engineering;
- statistical testing of observed associations;
- handling class imbalance;
- building and evaluating classification models for readmission;
- model interpretation and feature importance; and
- comparing predictive performance across multiple machine-learning algorithms.

## Project Structure

```text
diabetes-130-us-healthcare-analysis/
│
├── data/
│   └── processed/
│       └── diabetes_cleaned.csv
│
├── images/
│   ├── gender_distribution.png
│   ├── age_distribution.png
│   ├── race_distribution.png
│   ├── length_of_stay.png
│   ├── top_10_diabetes_medications.png
│   ├── readmission_distribution.png
│   ├── early_readmission_by_age.png
│   └── readmission_by_medication_change.png
│
├── notebooks/
│   └── Healthcare_Data_Quality_and_Analysis.ipynb
│
└── README.md
```

## Conclusion

This project demonstrates a complete exploratory healthcare data-analysis workflow, from data-quality assessment and cleaning to visualization and interpretation. The analysis provides an initial understanding of diabetic hospital encounters and readmission patterns while highlighting the need for deeper statistical and predictive analysis to better identify patients at elevated risk of readmission.

## Author

**Benjamin Christiana**  
Data Analyst | Aspiring Data Scientist
