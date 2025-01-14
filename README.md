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

## Data Profile

### Continuous Features
- **`Age`**
- **`BMI`**

### Categorical Features
- **`Gender`**
- **`Race`**
- **`Blood Pressure`**
- **`Cholesterol Level`**
- **`Retinopathy`**

---

## Sample Data

| SEQN   | Gender | Age | Race | BMI  | Blood Pressure | Cholesterol Level | Retinopathy | Diabetic |
|--------|--------|-----|------|------|----------------|-------------------|-------------|----------|
| 109316 | 2      | 13  | 4    | 30.5 | 1              | 1                 | 1           | 1        |
| 109373 | 2      | 9   | 3    | 27.2 | 2              | 2                 | 1           | 1        |
| 109490 | 1      | 8   | 4    | 45.4 | 1              | 1                 | 1           | 1        |
| 109612 | 1      | 9   | 4    | 29.8 | 1              | 1                 | 1           | 1        |
| 109638 | 2      | 8   | 3    | 43.6 | 1              | 1                 | 1           | 1        |

---

## Usage

This dataset is ideal for:
- **Exploratory Data Analysis (EDA)**: Analyze trends and relationships among features.
- **Predictive Modeling**: Build classification models for identifying diabetes risks.
- **Feature Engineering**: Create and optimize features for machine learning tasks.

---

## Repository Structure

```plaintext
.
├── data/                  # Folder containing the dataset
├── notebooks/             # Jupyter notebooks for analysis
├── src/                   # Source code for preprocessing and modeling
├── README.md              # Project documentation
