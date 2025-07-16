# KaggleTitanic

This repository presents an end-to-end analysis and machine learning solution for the Titanic dataset, a classic binary classification problem from Kaggle. The project walks through understanding the data, engineering features, building models, and evaluating results.

## Project Overview

The Titanic dataset contains demographic and passenger information for those aboard the RMS Titanic. The goal is to predict which passengers survived the disaster using machine learning techniques.

## Analysis Workflow

### 1. Data Loading and Exploration

- The dataset is loaded using pandas, and initial exploration is performed to understand its structure and the meaning of each column.
- Summary statistics and visualizations (histograms, value counts) are used to identify distributions, outliers, and missing values.

### 2. Data Cleaning and Imputation

- Columns deemed unnecessary for prediction (such as `PassengerId` and `Ticket`) are dropped.
- Missing values in the `Age` column are imputed using the mean age, ensuring that the feature can be used reliably during modeling.
- For the `Cabin` feature, only the initial letter is kept (as it may relate to location on the ship), and missing values are filled with a placeholder ('U' for unknown).
- Categorical variables (`Sex`, `Embarked`, `Cabin`) are converted to numerical form using one-hot encoding, facilitating their use in ML algorithms.

### 3. Feature Engineering

Several new features are created to better represent passenger relationships and status:
- **Family Size** (`famSize`): Sum of siblings/spouses (`SibSp`) and parents/children (`Parch`) for each passenger, to capture group survival patterns.
- **IsAlone**: Indicates if the passenger is traveling alone (family size = 0).
- **Title Extraction**: The passenger's title is extracted from their name (e.g., Mr., Miss., Mrs., Master, Dr., etc.), which can reflect social status or age group.
- **Fare Bands**: The fare column is analyzed for extreme values and binned to manage outliers.

### 4. Modeling

- Data is split into features and target (Survived).
- Several classification models are trained and compared, including:
  - **Ridge Classifier**
  - **Decision Tree**
  - **Random Forest**
  - **Gradient Boosting**
  - **Logistic Regression**
- Models are evaluated primarily by accuracy. Example scores:
  - Ridge Classifier: **0.799**
  - Decision Tree: **0.782**
  - Random Forest: **0.799**
  - Gradient Boosting: **0.816** (best result)
- Feature importance is examined, revealing that factors like sex, passenger class, age, and family size are strong predictors of survival.

### 5. Prediction and Submission

- Once the model is tuned and achieves satisfactory accuracy, predictions are made on the test set.
- The results are formatted for Kaggle submission, including `PassengerId` and the predicted `Survived` value.

## Key Insights

- Social and demographic features (Title, Family Size, Sex, Pclass) significantly impact survival probability.
- Careful handling of missing data and effective feature engineering improve model performance.

## How to Use

1. Clone the repository.
2. Open `Titanic.ipynb` in Jupyter or Colab to follow the steps.
3. Ensure required libraries (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`) are installed.
4. Run the notebook cells to reproduce the analysis and generate predictions.

## Author

ifzaal4dev

---

This README is based on code and explanations found in the `Titanic.ipynb` notebook. For full details and code, please see the [notebook file](Titanic.ipynb).
