# Heart Disease Mortality Prediction | Kaggle Competition

A Machine Learning project developed for the **Heart Disease Prediction ShohojCoding MLB-2** Kaggle competition. This project explores clinical and cardiovascular health indicators to predict the `DEATH_EVENT` target using multiple classification algorithms and cross-validation.

## 📌 Project Overview

The goal of this project is to build and evaluate machine learning models that predict mortality events using clinical health data.

As my first Kaggle competition project, this work helped me practice data preparation, model comparison, feature engineering, hyperparameter experimentation, and generating predictions for a competition submission.

**Competition:** [Heart Disease Prediction ShohojCoding MLB-2](https://www.kaggle.com/competitions/heart-disease-prediction-shohoj-coding-mlb-2)

## 🎯 Objectives

- Understand and prepare the competition dataset.
- Separate input features from the target variable.
- Train and compare multiple classification models.
- Evaluate model performance using repeated stratified cross-validation.
- Experiment with feature engineering and hyperparameter tuning.
- Generate predictions in the required submission format.

## 🛠️ Technologies Used

- **Python**
- **Pandas** — data manipulation
- **NumPy** — numerical operations
- **Scikit-learn** — model training and evaluation
- **LightGBM** — gradient boosting
- **CatBoost** — gradient boosting
- **Kaggle Notebooks** — development environment

## 📂 Dataset

The competition provides three CSV files:

| File | Purpose |
|---|---|
| `train.csv` | Training data with features and target labels |
| `test.csv` | Data used to generate competition predictions |
| `sample_submission.csv` | Reference format for the submission file |

The dataset contains clinical features, including age, ejection fraction, serum creatinine, serum sodium, and other health indicators.

- Training data: 239 rows and 14 columns.
- Test data: 60 rows and 13 columns.
- Target variable: `DEATH_EVENT`.
- Input features: 12 columns after removing `id` and the target from the training data.

*Note: The dataset files are provided by the competition and are not included in this repository.*

## ⚙️ Project Workflow

### 1. Data Loading and Preparation
- Loaded the training, test, and sample submission CSV files.
- Separated the target variable (`DEATH_EVENT`) from the input features.
- Removed the identifier column from the model inputs.
- Verified that training and test feature columns matched.

### 2. Model Training and Comparison

The following classification approaches were evaluated:

- Logistic Regression
- Random Forest
- LightGBM
- CatBoost
- Soft-voting ensemble models
- Extra Trees
- Gradient Boosting

### 3. Cross-Validation

Used **Repeated Stratified 5-Fold Cross-Validation**, with three repeats and a fixed random seed, to compare model performance across multiple splits.

### 4. Feature Engineering

Experimented with additional features derived from existing clinical variables, including:

- Log transformations of selected laboratory measurements.
- Ratios involving serum creatinine and serum sodium.
- Ejection fraction relative to age.
- An interaction between time and ejection fraction.

The engineered features were evaluated against the original feature set.

### 5. Hyperparameter Experimentation

Tested different Random Forest configurations, including tree depth and minimum samples per leaf. Also experimented with prediction probability thresholds and ensemble models.

### 6. Prediction and Submission

Trained a final Random Forest classifier using the full training dataset, generated predictions for the test dataset, and saved them as `submission.csv` with the required `id` and `DEATH_EVENT` columns.

## 📊 Results

The following results are from the notebook's local cross-validation experiments, not verified Kaggle leaderboard scores.

| Model / Experiment | Mean Accuracy |
|---|---:|
| Logistic Regression | 83.14% |
| Random Forest — initial configuration | 85.66% |
| LightGBM | 82.87% |
| CatBoost | 84.82% |
| Soft-voting ensemble | 84.12% |
| Random Forest + CatBoost ensemble | 85.80% |
| Final Random Forest configuration | **86.35%** |

The final Random Forest model used 500 trees and `min_samples_leaf=5`.

- **Mean cross-validation accuracy:** 86.35%
- **Standard deviation:** approximately 5.06 percentage points
- **Validation method:** Repeated Stratified 5-Fold Cross-Validation with three repeats

These results represent validation performance on the training data. They do not establish the model's final competition score or clinical reliability.

## 🚀 How to Run

### Requirements

Install the required Python packages:

```bash
pip install numpy pandas scikit-learn lightgbm catboost jupyter
```

### Steps

1. Clone or download this repository.
2. Download the competition data from Kaggle after accepting the competition rules, if required.
3. Open the notebook in Kaggle or Jupyter.
4. Update the dataset path to match your environment.
5. Run the cells to compare models and generate predictions.
6. Verify that `submission.csv` contains the expected columns before submitting it to Kaggle.

**Important:** The notebook uses a Kaggle-specific input path. When running locally, update that path to the location of your downloaded CSV files.

## 📚 Key Learnings

Through this project, I practiced:

- Preparing tabular data for machine learning.
- Comparing baseline models with ensemble methods.
- Using stratified cross-validation to evaluate classifiers.
- Engineering additional features from clinical variables.
- Experimenting with Random Forest hyperparameters.
- Generating predictions in a competition submission format.

## 🔮 Future Improvements

- Perform more systematic hyperparameter optimization.
- Evaluate precision, recall, F1-score, ROC-AUC, and confusion matrices.
- Investigate class imbalance and probability calibration.
- Improve reproducibility with a clear experiment log.
- Validate the final submission on the Kaggle leaderboard.
- Explore model interpretability to understand which features influence predictions.

## ⚠️ Disclaimer

This project is for educational and machine learning practice purposes only. The model is not a clinically validated diagnostic or medical decision-making tool.

## 👩‍💻 Author

**Sabrin Alam**

Aspiring AI Engineer & AI Research Enthusiast

GitHub: [SabrinPro](https://github.com/SabrinPro)

---

*Learning, experimenting, and growing through hands-on machine learning projects.*
