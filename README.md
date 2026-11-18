
# 🎓 Student Performance Prediction

**A Machine Learning regression project that predicts students' final grades (G3, on a 0–20 scale) using demographic, academic, social, and behavioral features from the UCI Student Performance Dataset.**

---

## 📌 Overview

This project analyzes factors associated with students' academic performance and applies supervised Machine Learning regression algorithms to predict their final grades (`G3`).

It uses two student cohorts from the UCI Student Performance Dataset: Mathematics and Portuguese. The workflow covers data exploration, preprocessing, model training, evaluation, hyperparameter tuning, and feature-importance analysis.

The project aims to explore how predictive analytics can help identify academic performance patterns and support educational interventions.

## 🎯 Project Objectives

- Explore academic, demographic, social, and behavioral factors related to student performance.
- Analyze relationships between study habits, previous grades, and final academic results.
- Develop and compare multiple regression models.
- Evaluate model performance using standard regression metrics.
- Optimize Random Forest models using GridSearchCV.
- Examine influential features and consider responsible applications of predictive analytics in education.

## ✨ Key Features

- Automatic dataset downloading and extraction.
- Separate analysis of Mathematics and Portuguese student cohorts.
- Exploratory Data Analysis (EDA) and data visualization.
- Categorical feature encoding and numerical feature scaling.
- Training and comparison of five regression algorithms.
- Evaluation using MAE, MSE, RMSE, and R².
- Random Forest hyperparameter tuning with five-fold GridSearchCV.
- Feature-importance analysis.
- Prototype Streamlit interface for demonstrating student performance predictions.

## 📊 Dataset

**Source:** [UCI Machine Learning Repository – Student Performance Dataset](https://archive.ics.uci.edu/dataset/320/student+performance)

The dataset contains student achievement records and demographic, family, social, and school-related information.

| Dataset | Students | Columns |
|---|---:|---:|
| Mathematics (`student-mat.csv`) | 395 | 33 |
| Portuguese (`student-por.csv`) | 649 | 33 |

**Target Variable:** `G3` — Final grade, ranging from 0 to 20.

The dataset includes:

- **Demographic:** Age, gender, school, and address type.
- **Family:** Parents' education and occupation, family size, and family relationships.
- **Academic:** Previous grades (`G1`, `G2`), study time, failures, and school support.
- **Social and Behavioral:** Absences, free time, social activities, and alcohol consumption.

Both datasets contain 33 columns, with no missing values or duplicate rows in the inspected data.

## 🔍 Exploratory Data Analysis (EDA)

The project explores the datasets through statistical analysis and visualizations, including:

- Grade distributions for Mathematics and Portuguese.
- Relationships between study time and final grades.
- Correlations among numerical variables.
- Academic, family, social, and behavioral patterns.
- Comparisons between the two student cohorts.

Matplotlib and Seaborn are used for data visualization.

## ⚙️ Methodology

### 1. Data Collection and Exploration

- Download and extract the UCI Student Performance Dataset.
- Load both subject datasets using Pandas.
- Inspect dataset dimensions, feature types, missing values, and duplicates.
- Explore grade distributions and feature relationships.

### 2. Data Preprocessing

- Separate numerical and categorical features.
- Encode categorical variables.
- Scale numerical features.
- Transform the original features into 41 model input features after encoding.
- Split each dataset into 80% training and 20% testing data.

| Dataset | Training Samples | Testing Samples |
|---|---:|---:|
| Mathematics | 316 | 79 |
| Portuguese | 519 | 130 |

### 3. Model Development

Five regression algorithms are trained and compared independently for both datasets.

| Model | Description |
|---|---|
| Linear Regression | Establishes a baseline linear relationship between features and grades |
| Ridge Regression | Applies regularization to linear regression |
| Random Forest Regressor | Captures nonlinear patterns using multiple decision trees |
| Gradient Boosting Regressor | Builds an ensemble of sequentially trained decision trees |
| Support Vector Regression (SVR) | Uses support vectors to model regression relationships |

### 4. Model Evaluation

Model performance is measured using:

- **MAE:** Mean Absolute Error
- **MSE:** Mean Squared Error
- **RMSE:** Root Mean Squared Error
- **R²:** Coefficient of Determination

### 5. Hyperparameter Tuning

Random Forest models are optimized separately for both subject datasets using `GridSearchCV` with five-fold cross-validation.

The parameter search includes:

- Number of estimators.
- Maximum tree depth.
- Minimum samples required to split a node.
- Maximum features considered for splitting.

## 📈 Model Performance

The following tables show the initial test-set results of the five baseline regression models, before the separate Random Forest hyperparameter-tuning step.

### Mathematics Dataset

| Model | MAE | MSE | RMSE | R² |
|---|---:|---:|---:|---:|
| Linear Regression | 1.6467 | 5.6566 | 2.3784 | 0.7241 |
| Ridge Regression | 1.6351 | 5.6089 | 2.3683 | 0.7265 |
| Random Forest | 1.1791 | 3.8348 | 1.9583 | 0.8130 |
| Gradient Boosting | 1.1594 | 4.0187 | 2.0047 | 0.8040 |
| SVR | 1.4810 | 5.5867 | 2.3636 | 0.7275 |

### Portuguese Dataset

| Model | MAE | MSE | RMSE | R² |
|---|---:|---:|---:|---:|
| Linear Regression | 0.7651 | 1.4759 | 1.2149 | 0.8487 |
| Ridge Regression | 0.7639 | 1.4745 | 1.2143 | 0.8488 |
| Random Forest | 0.7473 | 1.5455 | 1.2432 | 0.8415 |
| Gradient Boosting | 0.7890 | 1.7888 | 1.3375 | 0.8166 |
| SVR | 0.9051 | 2.2941 | 1.5146 | 0.7647 |

### Key Observations

- Random Forest achieved the highest baseline R² score for Mathematics (0.8130).
- Ridge Regression achieved the highest baseline R² score for Portuguese (0.8488).
- Gradient Boosting achieved the lowest MAE for Mathematics (1.1594).
- Random Forest achieved the lowest MAE for Portuguese (0.7473).

These results represent the initial baseline evaluation. They should not be interpreted as the performance of the separately tuned Random Forest models.

## 🧠 Feature Importance and Explainability

The project examines feature importance to identify variables that contribute to the models' predictions.

This analysis helps explore the predictive relationships between previous academic grades, study habits, and other student characteristics.

Feature importance indicates associations used by a model; it does not establish that a particular factor causes changes in student performance.

## 🖥️ Streamlit Application

The notebook includes code for generating a prototype Streamlit interface named **Academic Progress & Early Intervention Engine**.

The interface demonstrates:

- Mathematics and Portuguese subject selection.
- Student information and academic input fields.
- Illustrative grade prediction.
- Model-performance information.
- Educational-support and responsible-AI messaging.

**Implementation Note:** The current interface uses a simplified, hand-weighted formula for demonstration rather than loading and using the trained regression models. It is a prototype, not a deployed application connected to the trained ML pipeline.

## ⚠️ Limitations

- **Previous grades:** `G1` and `G2` are included as input features and are strongly related to `G3`. This contributes to predictive performance; predicting final grades without previous grades would be a more challenging task.
- **Test-set size:** The test sets contain 79 Mathematics and 130 Portuguese records, so results may vary with a different data split.
- **Dataset scope:** The datasets represent students from schools in one region of Portugal and may not generalize to other populations.
- **Application integration:** The Streamlit prototype does not currently use the trained regression models.
- **Responsible use:** Predictions should support educational guidance, not be used to label, penalize, or limit students.

## 🚀 Future Improvements

- Evaluate model performance without `G1` and `G2` to examine prediction from other student characteristics.
- Apply repeated or cross-validation-based evaluation for more robust performance estimates.
- Evaluate and report the tuned Random Forest models on held-out test data.
- Connect the Streamlit interface to the trained models and preprocessing pipeline.
- Improve application deployment and model integration.

## 🛠️ Technologies & Tools

**Programming Language**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

**Data Analysis & Numerical Computing**

![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)

**Data Visualization**

![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=plotly&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logoColor=white)

**Machine Learning & Model Optimization**

![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)

**Application Development**

![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)

**Development Environment**

![Jupyter Notebook](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black)

## 📁 Project Structure

```text
Student-Performance/
│
├── README.md
├── .gitignore
├── Student_Performance_Prediction.ipynb
├── Student_Performance_Prediction (1).ipynb
├── student_performance_prediction.py
└── student_performance_prediction (1).py
```

The repository currently contains duplicate copies of the notebook and Python export with `(1)` in their filenames. These can be removed after confirming that they are identical.

The notebook downloads the dataset during execution and includes code for generating the Streamlit interface.

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/alishaarif500/Student-Performance.git
cd Student-Performance
```

### 2. Install Dependencies

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

### 3. Run the Notebook

**Google Colab (recommended):**

Open or upload `Student_Performance_Prediction.ipynb` in Google Colab and run the notebook cells in sequence.

**Run locally:**

```bash
jupyter notebook Student_Performance_Prediction.ipynb
```

The notebook downloads the dataset from the UCI repository during execution.

## 📚 Learning Outcomes

Through this project, I gained practical experience in:

- Working with real-world educational datasets.
- Performing exploratory data analysis and visualization.
- Preprocessing numerical and categorical features.
- Training and comparing multiple regression algorithms.
- Evaluating models using regression metrics.
- Applying cross-validation and hyperparameter tuning.
- Exploring feature importance and model interpretability.
- Considering responsible applications of Machine Learning in education.

## 👩‍💻 Author

**Alisha Arif**

- GitHub: [alishaarif500](https://github.com/alishaarif500)
- LinkedIn: [Alisha Arif](https://linkedin.com/in/alisha-arif-22aa42386/)
- Email: [alishaarif500@gmail.com](mailto:alishaarif500@gmail.com)

---

*Developed as a practical Machine Learning project to explore student performance prediction and educational data analysis.*
