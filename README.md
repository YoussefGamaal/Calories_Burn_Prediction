# Calories Burn Prediction using Encoder–Decoder Architecture

## Project Overview

This project develops an Encoder–Decoder regression pipeline for predicting Calories Burned using physiological and activity-related features.

The project covers data exploration, data cleaning, feature encoding, feature importance analysis, and comparison of different regression decoders using the R² metric.

## Dataset

The dataset contains 15,000 observations and the following features:

* User_ID
* Gender
* Age
* Height
* Weight
* Duration
* Heart_Rate
* Body_Temp
* Calories

The target variable is **Calories**.

`User_ID` is treated as an identifier and is excluded from model training.

## Exploratory Data Analysis

The following visualizations were performed:

* Numerical feature histograms
* Gender distribution
* Boxplots for outlier detection
* Duration vs Calories
* Heart Rate vs Calories
* Correlation heatmap

The analysis showed that **Duration** has the strongest correlation with Calories, followed by **Heart Rate**.

## Data Preprocessing

The preprocessing steps include:

* Handling missing values
* Validating data types
* Detecting and removing extreme invalid observations
* One-Hot Encoding for categorical features
* Standard Scaling for numerical features

Numerical features were standardized using:

X_scaled = (X - μ) / σ

## Encoder

The encoder transforms the original mixed-type features into a numerical representation suitable for regression models.

* Gender → One-Hot Encoding
* Numerical features → Standard Scaling

For the final evaluation, the encoder was fitted only on the training data and then applied to the test data to prevent data leakage.

## Feature Importance

Linear Regression coefficients were analyzed to estimate feature importance.

Duration was one of the most influential features, followed by Body Temperature and Heart Rate.

Lasso Regression was also used to analyze feature sparsity and feature selection.

## Decoder Comparison

Five regression decoders were evaluated:

1. Normal Equation
2. Gradient Descent
3. Ridge Regression
4. Lasso Regression
5. Elastic Net

  Decoder                R² 
 
  Gradient Descent   0.84258 
  Normal Equation    0.84257 
  Ridge              0.84257 
  Lasso              0.84049 
  Elastic Net        0.80268 

## Final Results

Gradient Descent achieved the highest R² score of **0.84258**, making it the best-performing decoder in this experiment.

However, the difference between Gradient Descent, Normal Equation, and Ridge was extremely small, indicating very similar predictive performance.

Lasso achieved a slightly lower R² but provided greater coefficient sparsity and feature selection.

Elastic Net achieved a lower R² with the selected hyperparameters.

## Accuracy vs Interpretability

Gradient Descent provided the highest predictive performance.

Lasso provided greater sparsity and interpretability by reducing some feature coefficients to zero.

Therefore:

* **Best predictive performance:** Gradient Descent
* **Better feature sparsity and interpretability:** Lasso

## Project Structure

```text
Calories_Burn_Prediction/
│
├── data/
│   └── calories_Dataset.xlsx
│
├── notebooks/
│   └── calories_prediction.ipynb
│
├── visualizations/
│   ├── numerical_histograms.png
│   ├── gender_distribution.png
│   ├── outlier_boxplots.png
│   ├── duration_vs_calories.png
│   ├── heart_rate_vs_calories.png
│   ├── correlation_heatmap.png
│   ├── feature_importance.png
│   └── lasso_sparsity.png
│
├── models/
├── report/
└── README.md
```

## Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

## Conclusion

This project demonstrates a complete machine learning pipeline for predicting calories burned, starting from exploratory data analysis and data cleaning through feature encoding, feature importance analysis, and decoder comparison.

The final results show that the encoded features provide a strong basis for regression, with Gradient Descent achieving the highest R² score of **0.84258** among the evaluated decoders.



