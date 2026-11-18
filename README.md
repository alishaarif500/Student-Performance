
# Student Performance Prediction

A regression project that predicts students' final grade (G3, on a 0-20 scale) from demographic, social, behavioural and academic features, using the UCI Student Performance dataset.

## Overview

The notebook downloads the dataset, explores it, preprocesses the features, trains and compares five regression models separately for two student cohorts (Mathematics and Portuguese), tunes a Random Forest with grid search, and examines feature importance.

## Dataset

- **Source:** UCI Machine Learning Repository, Student Performance dataset (downloaded in the notebook).
- **Mathematics cohort:** 395 students. **Portuguese cohort:** 649 students. Both have 33 columns, with no missing values and no duplicate rows.
- **Target:** `G3`, the final grade (0-20).
- **Features:** 16 numeric columns (including age, study time, failures, absences, and the earlier grades `G1` and `G2`) and 17 categorical columns (such as school, parental jobs, internet access).

## Methodology

1. Download, load and explore both cohorts, including grade distributions.
2. Encode categorical variables and scale numeric features (41 features after encoding).
3. Split each cohort 80/20: Mathematics 316 training and 79 test students; Portuguese 519 training and 130 test students.
4. Train Linear Regression, Ridge Regression, Random Forest, Gradient Boosting and Support Vector Regression.
5. Evaluate with MAE, MSE, RMSE and R².
6. Tune a Random Forest with `GridSearchCV` (5-fold) and analyse feature importance.

## Results

Test-set results (first evaluation, before tuning):

**Mathematics cohort (79 test students)**

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 1.647 | 2.378 | 0.724 |
| Ridge Regression | 1.635 | 2.368 | 0.727 |
| Random Forest | 1.179 | 1.958 | 0.813 |
| Gradient Boosting | 1.159 | 2.005 | 0.804 |
| SVR | 1.481 | 2.364 | 0.728 |

**Portuguese cohort (130 test students)**

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 0.765 | 1.215 | 0.849 |
| Ridge Regression | 0.764 | 1.214 | 0.849 |
| Random Forest | 0.747 | 1.243 | 0.842 |
| Gradient Boosting | 0.789 | 1.338 | 0.817 |
| SVR | 0.905 | 1.515 | 0.765 |

Tree-based models did best on the Mathematics cohort, while the simple linear models matched them on the Portuguese cohort.

## Limitations

- The earlier grades `G1` and `G2` are included as inputs. They are strongly related to `G3`, so the high R² mostly reflects that students' grades tend to stay similar from one period to the next. Predicting without them would be a harder problem.
- The test sets are small (79 and 130 students), so scores can change with a different split.
- The two cohorts come from schools in one region and may not represent other populations.
- The Streamlit interface code in the notebook uses a simple hand-weighted formula for demonstration rather than the trained model.
- Predictions are meant to support students, not to label or penalise them.

## Future Improvements

- Evaluate a version without `G1` and `G2`.
- Use cross-validation instead of a single split and report the tuned model's test results.
- Connect the interface to the trained model and add it to the repository.

## Project Files

| File | Description |
|---|---|
| `Student_Performance_Prediction.ipynb` | Main notebook: exploration, preprocessing, modelling, tuning |
| `student_performance_prediction.py` | Python export of the notebook |

## How to Run

The notebook was built in Google Colab and downloads the dataset from the UCI repository.

**Google Colab (recommended):** upload the notebook and run all cells.

**Locally:**

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook Student_Performance_Prediction.ipynb
```

## Technologies

Python · Pandas · NumPy · scikit-learn · Matplotlib · Seaborn · Google Colab

## Author

**Alisha Arif** · [GitHub](https://github.com/alishaarif500) · [LinkedIn](https://linkedin.com/in/alisha-arif-22aa42386/)
