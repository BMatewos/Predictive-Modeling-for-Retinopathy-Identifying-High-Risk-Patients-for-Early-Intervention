# Predictive Modeling for Retinopathy-Identifying High Risk Patients for Early Intervention

## Objectives 
Primary Objective: Investigate the impact of diabetes on retinopathy  using machine learning models.
Secondary Objectives:
Assess the predictability of retinopathy  outcomes from diabetes and other health indicators.
Provide targeted recommendations based on the impact of diabetes and other factors on retinopathy .
Audience: Ophthalmologists and healthcare policy makers


![image](https://github.com/user-attachments/assets/c3a5330d-7815-4136-867f-51021231f458)

# Diabetes Dataset Repository

## Overview
This repository contains a dataset focused on identifying factors related to diabetes. The dataset includes health, demographic, and diagnostic information for individuals, enabling predictive modeling and exploratory data analysis (EDA).

---

## Dataset Description

- **Total Rows**: 9,005 
- **Total Columns**: 9

### Features

1. **Demographic Variables**:
   - **`SEQN`**: Unique identifier for each individual.
   - **`Gender`**: Categorical (1 = Male, 2 = Female).
   - **`Age`**: Continuous (Age in years).
   - **`Race`**: Categorical (Encoded race/ethnicity information).

2. **Health Metrics**:
   - **`BMI`**: Continuous (Body Mass Index).
   - **`Blood Pressure`**: Categorical (1 = Normal, 2 = Pre-hypertensive, 3 = Hypertensive).
   - **`Cholesterol Level`**: Categorical (1 = Normal, 2 = Elevated).

3. **Medical Conditions**:
   - **`Retinopathy`**: Categorical (1 = Yes, 0 = No; Presence of diabetic retinopathy).
   - **`Diabetic`**: Binary target variable (1 = Diabetic, 0 = Non-diabetic).

---


## Sample Data

| SEQN   | Gender | Age | Race | BMI  | Blood Pressure | Cholesterol Level | Retinopathy | Diabetic |
|--------|--------|-----|------|------|----------------|-------------------|-------------|----------|
| 109316 | 2      | 13  | 4    | 30.5 | 1              | 1                 | 1           | 1        |
| 109373 | 2      | 9   | 3    | 27.2 | 2              | 2                 | 1           | 1        |
| 109490 | 1      | 8   | 4    | 45.4 | 1              | 1                 | 1           | 1        |
| 109612 | 1      | 9   | 4    | 29.8 | 1              | 1                 | 1           | 1        |
| 109638 | 2      | 8   | 3    | 43.6 | 1              | 1                 | 1           | 1        |

## Data Balancing Techniques and Strategies

To address class imbalance within the dataset, the following data balancing strategy was implemented. This ensures that the analysis and predictive models built from the data do not suffer from bias toward the majority class (patients without retinopathy).

### Process Overview
![Picture2](https://github.com/user-attachments/assets/04470a62-2d94-445b-bfdf-8912128353ad)


The flowchart above illustrates the data balancing strategy in detail.

### Explanation

1. **Data Overview**:
   - The dataset initially contained 9,005 records.
   - After filtering invalid or incomplete records, 8,208 valid records remained.

2. **Class Separation**:
   - 252 patients with retinopathy.
   - 7,956 patients without retinopathy.

3. **Feature Selection**:
   - Continuous variables (e.g., Age, BMI) and categorical variables (e.g., Race) were retained.

4. **Statistical Comparison**:
   - **Kolmogorov-Smirnov Test**: Evaluated the distribution similarity for continuous variables.
   - **Chi-Squared Test**: Assessed the dependency of categorical variables on the target.

5. **Sampling**:
   - 1,000 random samples were generated from the majority class.
   - The sample with the highest statistical grade (aggregated p-values) was selected.

6. **Final Balanced Dataset**:
   - 252 patients with retinopathy.
   - 252 patients without retinopathy.
   - **Total Records**: 504.

This approach ensures the dataset is balanced while retaining its key statistical properties, making it suitable for robust predictive modeling and analysis.

---
## Exploratory Data Analysis

As part of the data exploration process, we analyzed the relationships between key health-related variables with a focus on the presence of retinopathy. Below is a **pair plot** visualization that highlights potential correlations and distributions among variables like `Age`, `BMI`, and `Cholesterol Level`, categorized by the presence of retinopathy.

### Pair Plot Visualization
<img width="459" alt="Picture3" src="https://github.com/user-attachments/assets/406e4065-e199-4ed7-ad57-8261923ffac7" />

### Insights from the Pair Plot:
1. **Variable Relationships**:
   - Scatter plots in the matrix show potential relationships between pairs of variables.
   - Continuous variables like `Age` and `BMI` demonstrate their distribution and possible trends in relation to retinopathy.

2. **Class Differentiation**:
   - The data is color-coded based on the presence of retinopathy (`1` for presence, `0` for absence), allowing for a clear distinction between the two groups.

3. **Univariate Distributions**:
   - Diagonal elements represent the distribution of individual variables, showing trends like the concentration of `Age` and `BMI` values in specific ranges.

This plot serves as an initial exploration to uncover potential patterns, which will inform feature selection and modeling steps.

### Correlation Heatmap with p-values
<img width="356" alt="Picture4" src="https://github.com/user-attachments/assets/56f36e94-63e7-4dd6-b33b-0d75c06a268d" />


The heatmap above highlights the correlation coefficients (and corresponding p-values) between key variables in the dataset. This visualization is critical for understanding relationships and dependencies among variables, which helps in feature selection and predictive modeling.

### Insights from the Correlation Heatmap:
1. **Diagonal Cells**:
   - The diagonal cells (marked with **1.00**) represent each variable's perfect correlation with itself, as expected.

2. **Key Observations**:
   - **BMI and Retinopathy**: A moderate negative correlation is observed between BMI and retinopathy, indicating that higher BMI might be associated with lower chances of retinopathy.
   - **Retinopathy and Diabetes**: A strong positive correlation is seen between retinopathy and a diabetes diagnosis, signifying that individuals with retinopathy are more likely to have diabetes.

3. **Statistical Significance**:
   - The corresponding p-values for significant correlations are close to 0, indicating strong evidence against the null hypothesis and validating the relationships observed.

This heatmap provides critical insights for hypothesis generation and informs the selection of features for predictive modeling.

---



