# E-Commerce Conversion Prediction using Feature Engineering and XGBoost

## Overview

This project was developed as part of the Summer Analytics 2026 Week 2 Hackathon. The objective is to predict whether a user will convert (make a purchase) based on demographic information, browsing behavior, device characteristics, marketing campaign exposure, and historical purchase data.

The solution uses machine learning techniques, feature engineering, and an XGBoost classifier to perform binary classification and generate predictions for unseen user data.

---

## Problem Statement

Businesses often collect large amounts of user interaction data but need intelligent systems to identify which users are most likely to convert.

Given anonymized user-level data containing:

* User demographics
* Device and browser information
* Traffic acquisition sources
* Browsing and engagement metrics
* Historical purchase behavior
* Marketing campaign information

the task is to predict whether a user will convert.

Target Variable:

* Converted = 1 → User converted
* Converted = 0 → User did not convert

Evaluation Metric:

* F1 Score

---

## Dataset

The project uses four datasets:

### train.csv

Training dataset containing features and target labels.

### public_test.csv

Labeled validation dataset used for model evaluation and threshold tuning.

### private_test.csv

Unlabeled dataset used for final prediction and competition evaluation.

### sample_submission.csv

Template for generating the final submission file.

---

## Machine Learning Concepts Used

This project is based on the following concepts:

### Data Preprocessing

* Missing Value Handling
* Feature Selection
* Data Cleaning

### Feature Engineering

Creation of new informative features from existing variables.

### Categorical Encoding

* One-Hot Encoding

### Supervised Learning

* Binary Classification

### Ensemble Learning

* XGBoost Classifier

### Model Evaluation

* F1 Score
* Threshold Optimization

### Machine Learning Pipeline

* Scikit-learn Pipeline
* ColumnTransformer

---

## Features Used

### Original Features

* User_ID
* Age
* Income
* City_Tier
* Device_Type
* Traffic_Source
* Pages_Viewed
* Products_Viewed
* Time_On_Site
* Previous_Purchases
* Discount_Seen
* Browser_Version
* Campaign_Code

### Engineered Features

#### Pages_per_Product

Measures browsing intensity relative to products viewed.

Pages_per_Product = Pages_Viewed / (Products_Viewed + 1)

#### Income_per_Age

Normalizes income with respect to age.

Income_per_Age = Income / (Age + 1)

#### Engagement

Represents user engagement level.

Engagement = Pages_Viewed × Time_On_Site

---

## Missing Value Handling

The dataset contains missing values in:

* Age
* Income
* Time_On_Site

These values are handled using:

* Median Imputation for numerical features
* Most Frequent Imputation for categorical features

---

## Model Architecture

### Baseline Model

The starter notebook provided a Logistic Regression baseline.

### Final Model

The final solution uses:

* XGBoost Classifier

Parameters:

* n_estimators = 300
* max_depth = 5
* learning_rate = 0.05
* subsample = 0.8
* colsample_bytree = 0.8
* random_state = 42

---

## Workflow

1. Load datasets
2. Perform exploratory analysis
3. Handle missing values
4. Engineer new features
5. Encode categorical variables
6. Train XGBoost model
7. Validate using public_test.csv
8. Tune classification threshold
9. Retrain on train + public_test
10. Generate predictions for private_test.csv
11. Create submission.csv

---

## Installation

Create a virtual environment:

```bash
python -m venv venv
```

Activate environment:

### Windows

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn xgboost lightgbm ipykernel
```

---

## Project Structure

```text
SA2026_Hackathon/
│
├── train.csv
├── public_test.csv
├── private_test.csv
├── sample_submission.csv
│
├── notebook.ipynb
├── submission.csv
├── report.pdf
└── README.md
```

---

## How to Run

### Step 1

Open the project folder in VS Code.

### Step 2

Open:

```text
notebook.ipynb
```

### Step 3

Select the Python virtual environment kernel.

### Step 4

Run all notebook cells from top to bottom.

### Step 5

After execution, a file named:

```text
submission.csv
```

will be generated automatically.

---

## Output

The generated submission file contains:

```text
User_ID,Converted
10001,0
10002,1
10003,0
...
```

This file can be uploaded directly to the competition platform.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* LightGBM
* Jupyter Notebook
* VS Code

---

## Results

Validation was performed using the provided public_test dataset.

Best Threshold:

```text
0.27
```

Best Validation F1 Score:

```text
0.5391
```

The final model was retrained using both train.csv and public_test.csv before generating predictions for private_test.csv.

---

## Future Improvements

Potential improvements include:

* Hyperparameter tuning
* Cross-validation
* Advanced feature engineering
* Feature importance analysis
* Ensemble methods
* Automated machine learning (AutoML)

---

## Author

Developed as part of the Summer Analytics 2026 Week 2 Hackathon submission.
