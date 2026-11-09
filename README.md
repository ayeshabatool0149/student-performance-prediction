# Student Performance Prediction

Predicting students' final marks (G3) using linear regression, built with Python, pandas and scikit-learn.

## Overview

This project uses the UCI Student Performance dataset (maths course, `student-mat.csv`) to predict a student's final grade. It also compares two models to show how much previous grades (G1, G2) matter compared with study habits and background factors.

## Dataset

- Source: UCI Machine Learning Repository, Student Performance dataset (Cortez & Silva, 2008)
- Size: 395 students, 33 columns
- Missing values: none
- Target: `G3` (final grade, 0 to 20)

## Approach

1. Loaded the data and checked its shape, missing values and summary statistics.
2. Explored the distribution of final marks and the correlation of features with `G3`.
3. Split the data 80% train / 20% test (`random_state=42`).
4. Trained two Linear Regression models and evaluated them with Mean Absolute Error (MAE) and R².

## Results

| Model | Features | MAE (marks) | R² |
|---|---|---|---|
| Model 1 | G1, G2, failures, studytime, age, absences | 1.33 | 0.78 |
| Model 2 | failures, studytime, age, absences | 3.54 | 0.04 |

## Key Findings

- Previous grades (G1 and G2) are by far the strongest predictors of the final grade. Including them reduces the average error from 3.54 to 1.33 marks.
- Without G1 and G2, the selected features explain almost none of the variation in final marks (R² = 0.04).
- About 10% of students have G3 = 0 (likely dropouts or absentees), which are hard for a linear model to predict.

## Limitations and Future Work

- Only linear regression was used; tree-based models (Random Forest, Gradient Boosting) could be tested.
- Categorical features (e.g. school support, parental education, alcohol use) were not included yet.
- Students with G3 = 0 could be handled separately, for example with a classifier for dropout risk.

## How to Run

1. Clone the repository:
   ```
   git clone https://github.com/ayeshabatool0149/student-performance-prediction.git
   ```
2. Install the requirements:
   ```
   pip install pandas scikit-learn matplotlib seaborn jupyter
   ```
3. Download `student-mat.csv` from the UCI Student Performance dataset and place it in the project folder.
4. Open `Student_Performance_Prediction.ipynb` in Jupyter or Kaggle and run all cells.
5. If running on Colab, upload the dataset and update the file path in the first cell (for example `/content/student/student-mat.csv`).

## Tools

Python, pandas, scikit-learn, matplotlib, seaborn
