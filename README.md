# Healthcare Stroke Analysis

## Project Overview

This project analyzes a healthcare dataset to explore factors associated with stroke occurrence.

The project focuses on data cleaning, exploratory data analysis (EDA), feature engineering, and business-oriented analysis to identify patterns related to stroke cases.

The analysis was performed using Python and Pandas, with visualizations created using Matplotlib and Seaborn.




## Dataset

The dataset contains healthcare information for patients and includes demographic, medical, and lifestyle-related features.

### Main Features

- `age` — Patient age
- `gender` — Patient gender
- `hypertension` — Whether the patient has hypertension
- `heart_disease` — Whether the patient has heart disease
- `ever_married` — Marital status
- `work_type` — Type of employment
- `residence_type` — Urban or rural residence
- `avg_glucose_level` — Average glucose level
- `bmi` — Body Mass Index
- `smoking_status` — Smoking status
- `stroke` — Target variable indicating whether the patient had a stroke

Each row represents one patient record.

The target variable is `stroke`, where `0` represents no stroke and `1` represents stroke.

## Project Objectives

The main objectives of this project are:

- Load and understand the healthcare dataset.
- Identify and handle missing values.
- Investigate unusual categorical values.
- Analyze numerical distributions and potential outliers.
- Explore categorical and numerical features in relation to stroke.
- Create meaningful engineered features.
- Answer business-oriented questions using the data.
- Identify patterns and associations related to stroke occurrence.





## Project Objectives

The main objectives of this project are:

- Load and understand the healthcare stroke dataset.
- Identify and handle missing values.
- Investigate unusual categorical values.
- Analyze numerical feature distributions and potential outliers.
- Explore categorical and numerical features in relation to stroke occurrence.
- Create meaningful engineered features.
- Analyze combinations of age, BMI, and glucose levels.
- Develop an engineered risk-factor score.
- Answer business-oriented questions using the dataset.
- Identify important patterns and associations related to stroke occurrence.




## Data Cleaning

The dataset was inspected and cleaned before performing the analysis.

### Cleaning Steps

- Missing values in the `bmi` column were handled using median imputation.
- The `gender = Other` category was retained because it represents a valid categorical value.
- The `smoking_status = Unknown` category was retained as a separate category rather than automatically treating it as missing.
- Potential numerical outliers in `age`, `bmi`, and `avg_glucose_level` were investigated using statistical methods and visualizations.
- Statistical outliers were not automatically removed because an extreme value is not necessarily a data error.
- The `id` column was removed because it is an identifier and does not provide useful analytical information.
- Column names were standardized by removing extra spaces and converting them to lowercase.
- Duplicate rows and remaining missing values were checked after cleaning.



## Exploratory Data Analysis

Exploratory Data Analysis (EDA) was performed to understand the structure and distribution of the data and to identify patterns related to stroke occurrence.

### Numerical Features

The following numerical features were analyzed:

- `age`
- `bmi`
- `avg_glucose_level`

Histograms, KDE plots, and boxplots were used to examine the distributions, central tendency, spread, skewness, and potential extreme values.

### Categorical Features

The following categorical features were analyzed:

- `gender`
- `work_type`
- `smoking_status`
- `residence_type`
- `hypertension`
- `heart_disease`
- `ever_married`

Bar charts were used to compare the distribution of different categories.

### Target Variable

The target variable `stroke` was investigated to understand the distribution of stroke and non-stroke cases.

The dataset is strongly imbalanced, with approximately **95.13% non-stroke cases** and **4.87% stroke cases**.

Because of this imbalance, accuracy alone may not be sufficient when evaluating a future machine-learning model. Metrics such as precision, recall, F1-score, and the confusion matrix should also be considered.




## Feature Engineering

Several new features were created to make the analysis more meaningful and to support the business questions.

### Age Group

Patients were divided into four age groups:

- **Child:** age below 18
- **Young Adult:** 18–39
- **Middle-aged:** 40–59
- **Senior:** 60 and above

### BMI Category

BMI was categorized using standard BMI thresholds:

- **Underweight:** BMI below 18.5
- **Normal:** 18.5–24.9
- **Overweight:** 25–29.9
- **Obese:** 30 and above

### Glucose Category

Average glucose level was divided into three approximately equal-sized groups using quantiles:

- **Low**
- **Medium**
- **High**

This approach was used to create balanced groups based on the distribution of glucose values in the dataset.

### Risk Factor Count

A combined risk-factor score was created using five observed indicators:

- Hypertension
- Heart disease
- Current or former smoking
- High glucose
- Obesity

The number of present risk factors was combined into `risk_factor_count`.

Patients were then grouped into:

- **0 risks**
- **1 risk**
- **2 risks**
- **3+ risks**

A `high_risk_segment` was also created for patients with **3 or more risk factors**.



## Business Questions & Key Findings

### Business Question 1

**Which combination of age group, BMI category, and glucose category has the highest observed stroke rate?**

Among groups containing at least 20 people, the highest observed stroke rate was found among **Senior** patients with **Overweight BMI** and **High glucose**.

- Group size: **218 patients**
- Stroke cases: **42**
- Observed stroke rate: **19.27%**

This finding represents an observed association in the dataset and should not be interpreted as a causal relationship.

### Business Question 2

**How does the observed stroke rate change as the number of risk factors increases?**

The analysis showed that the observed stroke rate generally increased as the number of engineered risk factors increased.

This suggests an association between the combined number of observed risk factors and stroke occurrence in this dataset.

### Business Question 3

**Which demographic or lifestyle groups contain the largest number of people in the engineered high-risk segment?**

The high-risk segment was defined as patients with **3 or more engineered risk factors**.

The segment was analyzed across:

- Age group
- Work type
- Smoking status
- Residence type
- Gender

The analysis identified the largest groups within the high-risk segment for each demographic and lifestyle feature.

These findings describe patterns observed in the dataset and do not represent medical diagnoses or causal relationships.




## Tools & Technologies

- **Python**
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical operations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Jupyter Notebook** — Interactive data analysis
- **Visual Studio Code** — Development environment
- **Git & GitHub** — Version control and project sharing



## Project Structure

```text
healthcar/
│
├── data/
│   ├── healthcare-dataset-stroke-data.csv
│   └── healthcare_stroke_cleaned_engineered.csv
│
├── images/
│   ├── age_distribution.png
│   ├── bmi_distribution.png
│   ├── avg_glucose_level_distribution.png
│   ├── stroke_target_distribution.png
│   ├── stroke_rate_by_engineered_risk_group.png
│   └── ...
│
├── stroke_prediction_eda.ipynb
│
└── README.md
```

### Folder Description

- **data/** — Contains the original and cleaned datasets.
- **images/** — Contains visualizations generated during the analysis.
- **stroke_prediction_eda.ipynb** — Main Jupyter Notebook containing the complete analysis.
- **README.md** — Project documentation and key findings.




## Limitations

- This dataset is observational, so the identified relationships do not prove causation.
- The target variable is highly imbalanced, with a relatively small number of stroke cases.
- The engineered risk factors are analytical indicators created for this project and should not be interpreted as clinical risk scores.
- The results should not be used as individual medical diagnoses or clinical decision rules.
- The dataset may not fully represent all patient populations or healthcare settings.

## Future Improvements

Future work could include:

- Building machine-learning models to predict stroke occurrence.
- Applying appropriate techniques to handle class imbalance.
- Comparing multiple classification algorithms.
- Evaluating models using precision, recall, F1-score, ROC-AUC, and the confusion matrix.
- Performing feature selection and hyperparameter tuning.
- Validating the model on an independent dataset.
- Developing an interactive dashboard to present the analysis and predictions.

## Conclusion

This project provides an exploratory analysis of a healthcare stroke dataset and identifies several patterns associated with stroke occurrence.

The analysis demonstrates the importance of data cleaning, exploratory analysis, feature engineering, and appropriate evaluation when working with an imbalanced healthcare dataset.

The findings provide a foundation for future predictive modeling and deeper analysis.