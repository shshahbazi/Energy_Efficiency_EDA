# Data Science Final Project - Energy Efficiency Prediction

This repository contains the final project for the **Data Science** course.  
The project focuses on analyzing the **[Energy Efficiency Data Set](https://www.kaggle.com/datasets/elikplim/eergy-efficiency-dataset)**   and building predictive models to estimate **Heating Load** and **Cooling Load** of residential buildings using various machine learning algorithms.

---

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Preprocessing](#data-preprocessing)
- [Modeling](#modeling)
  - [Neural Network](#1-neural-network)
  - [Random Forest](#2-random-forest)
  - [XGBoost](#3-xgboost)
- [Results and Evaluation](#results-and-evaluation)
- [Conclusion](#conclusion)
- [References](#references)

---

## Introduction
The aim of this project is to analyze the **energy consumption of residential buildings** and predict **heating** and **cooling loads** based on architectural and design features.  
By applying different **machine learning models**, the goal is to identify key factors influencing energy efficiency and determine the most accurate model for prediction.

---

## Dataset
I used the **[Energy Efficiency Data Set](https://www.kaggle.com/datasets/elikplim/eergy-efficiency-dataset)**, which includes **768 samples** with 8 input features:  
- Relative Compactness  
- Surface Area  
- Wall Area  
- Roof Area  
- Overall Height  
- Orientation  
- Glazing Area  
- Glazing Area Distribution  

**Target variables:**
- Heating Load  
- Cooling Load  

This dataset is commonly used to evaluate building design impact on energy consumption.

---

## Exploratory Data Analysis
Several important insights were gained during the EDA phase:

1. **Initial inspection** showed that the dataset contains no missing values, with balanced numeric features suitable for modeling.  
2. **Distribution of features** revealed that variables had diverse ranges and required scaling for proper model performance.  
3. **Correlation analysis** showed:  
   - Strong negative correlation between `Relative_Compactness` and `Surface_Area` (-0.99).  
   - Strong positive correlation between `Overall_Height` and `Roof_Area` (0.97).  
   - Very strong correlation between the target variables: `Heating_Load` and `Cooling_Load` (0.98).  
4. **Outlier detection** confirmed that some unusual values exist, but they do not significantly affect the overall dataset and can be retained.  

These findings guided the preprocessing and feature selection process.


---

## Data Preprocessing
- Removed redundant features (`Surface_Area`, `Roof_Area`) based on correlation.  
- Normalized and scaled features.  
- Split data into **training** and **testing sets** for model evaluation.  


---

## Modeling

### 1. Neural Network
A simple feedforward neural network (MLP) with one hidden layer was implemented using **Scikit-learn**.  
- Training epochs: 500  
- Evaluation metrics: **MAE** and **RMSE**  


---

### 2. Random Forest
A **Random Forest Regressor** with 100 trees was trained.  
- Robust against overfitting  
- Performed significantly better than the neural network  


---

### 3. XGBoost
The **XGBoost Regressor** was implemented as the most advanced model in this project.  
- Outperformed both Neural Network and Random Forest  
- Achieved the **lowest error values**  


---

## Results and Evaluation
| Model           | MAE    | RMSE   |
|-----------------|--------|--------|
| Neural Network  | 2.903  | 3.769  |
| Random Forest   | 1.065  | 1.708  |
| XGBoost         | **0.440** | **0.809** |

**Key Insights**:  
- The Neural Network underperformed compared to tree-based models.  
- Random Forest achieved good results with stable predictions.  
- XGBoost showed the **best performance**, with predictions almost perfectly aligned with actual values.  

---

## Conclusion
- It is possible to predict **heating and cooling energy loads** of buildings with high accuracy using architectural features.  
- **XGBoost** proved to be the most reliable and accurate model in this study.  
- Understanding feature correlations (e.g., Relative Compactness, Overall Height) helps in improving building design for **energy efficiency optimization**.  

---
