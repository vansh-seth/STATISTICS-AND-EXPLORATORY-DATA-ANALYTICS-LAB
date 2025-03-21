# Linear Regression and Logistic Regression

## Overview
This project explores **Linear Regression** and **Logistic Regression** using the **Diabetes dataset** from `sklearn.datasets`. The dataset includes medical predictor variables and a target variable representing disease progression. 

Key aspects covered:
- **Exploratory Data Analysis (EDA)**
- **Feature Correlation Analysis**
- **Linear Regression Model for Disease Progression Prediction**
- **Logistic Regression using Median Split for Binary Classification**
- **Gradient Descent Implementation**
- **Lasso Regression with Hyperparameter Tuning**

---

## Requirements
To run the code, install the necessary libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

---

## Dataset
The dataset is loaded from `sklearn.datasets.load_diabetes()`. It consists of:
- **10 predictor features** (age, sex, BMI, blood pressure, etc.)
- **1 target variable** (a continuous value representing disease progression)

---

## Exploratory Data Analysis (EDA)
- First 5 rows of the dataset are displayed.
- A histogram of the target variable is plotted.
- A **heatmap** of feature correlations is generated.

---

## Linear Regression Model
### Steps:
1. **Train-Test Split**: 80% training, 20% testing.
2. **Model Training**: Using `sklearn.linear_model.LinearRegression()`.
3. **Prediction & Evaluation**:
   - Mean Squared Error (MSE)
   - R² Score
4. **Visualization**:
   - Regression line plot for BMI vs. Disease Progression.
   - ROC Curve for classification using regression outputs.

### Results:
- **MSE**: 2900.19
- **R² Score**: 0.45

---

## Logistic Regression Approximation
Since the target is continuous, we convert it into a **binary classification problem** using the median split technique:
- Targets above the median are labeled **1**.
- Targets below the median are labeled **0**.

A **ROC Curve** is plotted using the regression predictions as probability estimates.

---

## Gradient Descent Implementation
A manual implementation of gradient descent is provided to optimize the linear regression model. However, due to improper learning rate adjustments, the loss explodes over iterations, demonstrating the importance of tuning hyperparameters correctly.

---

## Lasso Regression (Regularized Model)
### Steps:
1. **Data Standardization** using `StandardScaler()`.
2. **Hyperparameter Tuning** using `GridSearchCV` to find the best `alpha`.
3. **Best Alpha Selection & Model Evaluation**.
4. **Feature Importance Analysis**.

### Results:
- **Best Alpha**: 1
- **Best MSE**: 2824.56
- **Feature Importance Plot**: Shows impact of each variable on the target.

---

## Visualizations
1. **Target Distribution** (Histogram)
2. **Correlation Matrix** (Heatmap)
3. **Linear Regression Fit** (BMI vs Target)
4. **ROC Curve** (Classification Performance)
5. **Gradient Descent Loss Curve**
6. **Lasso Regression Alpha vs. MSE**
7. **Feature Importance in Lasso Regression**

---

## Conclusion
- **Linear Regression** gives an MSE of ~2900 with R² = 0.45, indicating a moderate fit.
- **Lasso Regression** improves the MSE slightly and highlights the most important features.
- **Gradient Descent** needs proper tuning to avoid divergence.
- **Logistic Regression Approximation** using median split provides a method for classification but is not ideal for this dataset.

---

## Future Improvements
- Implement a proper Logistic Regression model instead of using median-split classification.
- Try other regression models such as **Ridge Regression** or **Random Forest Regressor**.
- Perform feature engineering for better model accuracy.
- Optimize gradient descent parameters.

