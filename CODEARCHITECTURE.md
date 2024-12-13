# Code Architecture Overview

This document provides an overview of the steps and components used in the project to predict **batting average (BA)** and **earned run average (ERA)** for individual players using machine learning.

---

## **Project Steps**

The project is broken down into 8 major steps:

---

### **1. Problem Definition**

- **Objective**: Determine whether machine learning can be effectively used to predict individual player performance metrics, such as:
  - Batting Average (BA) for Mookie Betts.
  - Earned Run Average (ERA) for Jack Flaherty.
- The challenge is to utilize historical data to train predictive models and evaluate their effectiveness for real-world predictions.

---

### **2. Data Collection**

- **Sources**:
  - Used the `pybaseball` library to fetch batting statistics for Mookie Betts from 2017 to 2023.
  - Downloaded Jack Flaherty’s pitching statistics from the Baseball Reference website, stored in `jack_flaherty.csv`.
  
- **Preprocessing**:
  - The 2020 season was excluded due to the shortened schedule caused by COVID-19, which could introduce biases or inconsistencies.

- **Note**: Feature engineering (e.g., creating or transforming features) was **not utilized** in this project.

---

### **3. Data Splitting**

- The collected data was split into **training** and **testing** datasets using an 80/20 ratio:
  - **80% Training**: Used to train the machine learning models.
  - **20% Testing**: Used to evaluate the model’s performance on unseen data.

---

### **4. Model Selection**

Three machine learning models were implemented to predict batting average and ERA:

1. **Linear Regression**:
   - A simple model that assumes a linear relationship between input features and target variables.

2. **Random Forest**:
   - An ensemble learning method that uses multiple decision trees to capture non-linear relationships in the data.

3. **Gradient Boosting**:
   - Another ensemble method that builds trees sequentially, each correcting the errors of the previous tree.

> The code for these models is implemented in the notebooks and scripts in the repository, using libraries like `scikit-learn`.

---

### **5. Model Evaluation**

To evaluate the models, the following metrics were calculated using libraries available in Jupyter Notebook:

1. **Mean Absolute Error (MAE)**:
   - Measures the average magnitude of errors between predicted and actual values. Lower MAE indicates better performance.

2. **R-squared (\(R^2\))**:
   - Explains the proportion of variance in the target variable captured by the model. Higher \(R^2\) values indicate better performance.

---

### **6. Hyperparameter Tuning**

- **Method**: Grid search was used to find the best combination of hyperparameter settings for the Random Forest and Gradient Boosting models.
- **Key Parameters Tuned**:
  - Random Forest: Number of trees (`n_estimators`).
  - Gradient Boosting: Learning rate, number of trees, and tree depth (`max_depth`).

> This step ensures that models achieve optimal performance without overfitting.

---

### **7. Cross-Validation**

- **Method**: K-fold cross-validation was applied to validate model performance on different subsets of data.
- **Configuration**: Used 2 folds (K=2), ensuring the data was split into two subsets for training and validation in each fold.

---

### **8. Deploy Model**

- The trained models were used to make predictions for the 2024 season:
  1. **Mookie Betts**:
     - Predicted overall batting average for the 2024 season.
  2. **Jack Flaherty**:
     - Predicted overall earned run average (ERA) for the 2024 season.

---

## **How the Components Relate**

### **Data Flow**:
1. **Data Collection** → Data is fetched from `pybaseball` or loaded from CSV files.
2. **Data Splitting** → The cleaned data is split into training and testing sets.
3. **Model Selection and Training** → Models are trained on the training dataset.
4. **Evaluation and Deployment** → Trained models are evaluated and used for predictions.
