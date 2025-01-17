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
### Scatter Plot: Age vs. BMI by Retinopathy Status
<img width="377" alt="Picture5" src="https://github.com/user-attachments/assets/9ebad63e-c2ca-445c-bec1-21450996de92" />


This scatter plot visualizes the relationship between Age and BMI, categorized by the presence or absence of retinopathy.

### Observations:
1. **Data Spread**:
   - Data points are spread across all age ranges, indicating varied BMI levels irrespective of retinopathy status.

2. **Retinopathy Levels**:
   - Orange markers represent patients with retinopathy, while blue markers denote those without.

3. **Lack of Clear Trend**:
   - No evident trend or pattern suggests a strong correlation between Age and BMI concerning the effects of retinopathy.

This plot highlights the complexity of relationships between variables and reinforces the need for further statistical analysis or feature engineering.

---
### Distribution of Eye Blindness by Race
<img width="354" alt="image" src="https://github.com/user-attachments/assets/59aa71b8-4a9d-4f76-bd35-5998de2f64a0" />

The bar chart above visualizes the distribution of eye blindness by racial groups, with a focus on the presence of retinopathy.

### Observations:
1. **High Prevalence in African American and White Groups**:
   - Both African American and White groups show higher counts of blindness, with a marked increase in the presence of retinopathy (darker bars).
   - This highlights the disproportionate impact of retinopathy in these racial groups.

2. **Lower Variation in Mexican Americans**:
   - Mexican Americans display the lowest variation in blindness across retinopathy status, indicating relatively consistent blindness rates regardless of retinopathy presence.

3. **Other Groups**:
   - Other Hispanic and "Others" categories display intermediate distributions, with slightly more variation between retinopathy statuses compared to Mexican Americans.

This visualization emphasizes potential racial disparities in eye health, which can guide targeted research or healthcare interventions.

---

### Box Plot: Distribution of BMI by Retinopathy Status
<img width="808" alt="Screenshot 2025-01-14 at 9 29 59 PM" src="https://github.com/user-attachments/assets/17db03f7-d51d-4a18-8948-c75304559e85" />


The box plot above illustrates the distribution of BMI values categorized by the presence or absence of retinopathy.

### Observations:
1. **Higher BMI in Retinopathy**:
   - Individuals with retinopathy have higher BMI values on average compared to those without.

2. **Median BMI Comparison**:
   - The median BMI is slightly higher in the retinopathy group (31.0) compared to the non-retinopathy group (28.1).

3. **Presence of Outliers**:
   - Both groups show the presence of outliers, indicating individuals with significantly higher BMI values beyond the typical range.
---
### Bar Chart: Diabetic Status vs. Retinopathy (Percentage)
<img width="360" alt="image" src="https://github.com/user-attachments/assets/fa3f060b-85c6-407b-ac9b-937e5b799489" />

The bar chart above illustrates the relationship between diabetic status and the presence of retinopathy, represented as percentages.

### Observations:
1. **Prevalence of Retinopathy in Diabetics**:
   - The majority of individuals with retinopathy are diabetic, highlighting a strong association between diabetes and retinopathy.

2. **Non-Diabetic Group**:
   - All non-diabetics in this sample do not have retinopathy, indicating no presence of retinopathy in this group.

This visualization provides a clear depiction of the link between diabetes and retinopathy, underscoring diabetes as a significant risk factor for retinopathy.

---
## Principal Component Analysis (PCA)

![image](https://github.com/user-attachments/assets/d460ed1e-dd4f-4cca-8b6b-4ee8a83b2301)

These plots provide insights into the dimensionality reduction using Principal Component Analysis (PCA).

### Observations:
1. **Explained Variance Ratio (Left Plot)**:
   - The plot demonstrates the proportion of variance captured by each Principal Component.
   - The first component explains the majority of the variance, with diminishing contributions from subsequent components.

2. **Cumulative Explained Variance (Right Plot)**:
   - This plot shows the cumulative variance explained by adding each Principal Component sequentially.
   - By the fourth component, almost all the variance (approximately 95%) is captured, indicating that the first few components are sufficient for dimensionality reduction.

These plots are essential for determining the optimal number of components to retain in PCA, balancing dimensionality reduction and information preservation.

## Key Predictors of Retinopathy

### Feature Importance
<img width="427" alt="image" src="https://github.com/user-attachments/assets/159d7156-0dcb-49e4-9f4a-84e07474b549" />


This bar chart highlights the relative importance of various features in predicting retinopathy.

### Observations:
1. **Diabetes Status**:
   - The most significant predictor of retinopathy, contributing over **60%** to the model's decision-making process.

2. **BMI**:
   - The second most influential factor, contributing approximately **14%** to predictions.

3. **Minor Contributors**:
   - **Age**, **Blood Pressure**, **Cholesterol Level**, and **Race** each contribute less than **10%**.
   - **Gender** has the least influence, with a contribution of around **1.6%**.

These insights underline the critical role of diabetes status and BMI in identifying retinopathy risks while suggesting a minor influence from other factors.

---
## Model Selection

Three classification models—**Logistic Regression**, **Decision Tree**, and **Random Forest**—were evaluated for predicting retinopathy. The evaluation metrics include precision, recall, F1-score, and accuracy. Below are the results and confusion matrices for each model.

---

### Logistic Regression
| Metric      | Precision | Recall | F1-Score | Support |
|-------------|-----------|--------|----------|---------|
| **Yes**     | 0.90      | 1.00   | 0.95     | 47      |
| **No**      | 1.00      | 0.91   | 0.95     | 54      |
| **Accuracy**|           |        | **0.95** | 101     |

**Confusion Matrix**:
<img width="231" alt="image" src="https://github.com/user-attachments/assets/3cb6736e-674e-4645-9af6-6793fe504d54" />

#### Observations:
- Logistic Regression achieved an **accuracy of 95%**, demonstrating strong predictive performance.
- It perfectly identified all positive cases (`Yes` for retinopathy) but misclassified 5 negative cases (`No`).

---

### Decision Tree
| Metric      | Precision | Recall | F1-Score | Support |
|-------------|-----------|--------|----------|---------|
| **Yes**     | 0.89      | 0.87   | 0.88     | 47      |
| **No**      | 0.89      | 0.91   | 0.90     | 54      |
| **Accuracy**|           |        | **0.89** | 101     |

**Confusion Matrix**:
<img width="223" alt="image" src="https://github.com/user-attachments/assets/d4254347-25e6-404e-b727-bf648099d82b" />


#### Observations:
- The Decision Tree achieved an **accuracy of 89%**, slightly lower than Logistic Regression.
- It misclassified 6 positive cases (`Yes`) and 5 negative cases (`No`), indicating room for improvement.

---

### Random Forest Classifier
| Metric      | Precision | Recall | F1-Score | Support |
|-------------|-----------|--------|----------|---------|
| **Yes**     | 0.87      | 1.00   | 0.93     | 47      |
| **No**      | 1.00      | 0.90   | 0.95     | 54      |
| **Accuracy**|           |        | **0.94** | 101     |

**Confusion Matrix**:
<img width="263" alt="image" src="https://github.com/user-attachments/assets/f2584c64-9dce-4ba5-8611-3f501206f46a" />

#### Observations:
- The Random Forest Classifier achieved an **accuracy of 94%**, slightly lower than Logistic Regression but higher than Decision Tree.
- It perfectly identified all negative cases (`No`) but misclassified 2 positive cases (`Yes`).

---

### Comparison of Models
| Model                  | Accuracy | Precision (Yes) | Recall (Yes) | F1-Score (Yes) |
|------------------------|----------|-----------------|--------------|----------------|
| Logistic Regression    | 95%      | 0.90            | 1.00         | 0.95           |
| Decision Tree          | 89%      | 0.89            | 0.87         | 0.88           |
| Random Forest          | 94%      | 0.87            | 1.00         | 0.93           |

#### Key Takeaways:
- **Logistic Regression** is the top-performing model, with the highest accuracy and F1-score.
- **Random Forest** is a competitive alternative, offering perfect recall for positive cases (`Yes`).
- **Decision Tree** showed slightly lower performance, highlighting the need for further optimization.

---
## Conclusion

### Key Finding
- **Diabetes** is identified as a significant predictor of retinopathy, along with secondary contributors such as **BMI**, **age**, and **blood pressure**.

### Model Performance
- The **Logistic Regression model** achieved an accuracy of approximately **95%**, demonstrating robust predictive capabilities and reliability for identifying individuals at risk of retinopathy.

### Implications
1. **For Healthcare**:
   - Screening for diabetes can serve as an **early indicator** for retinopathy risk management, enabling timely interventions and reducing long-term complications.
   
2. **Policy Recommendations**:
   - Advocate for **regular retinal exams** in populations at risk of diabetes to promote early detection and prevention of severe outcomes.

### Future Directions
1. **Model Enhancement**:
   - Explore more comprehensive models by incorporating additional predictors such as **diet**, **genetic factors**, and **lifestyle variables** for improved accuracy and insights.

2. **Interdisciplinary Collaboration**:
   - Collaborate with **ophthalmological** and **endocrinological experts** to refine screening guidelines and implement effective strategies for retinopathy prevention.

---


