# Customer Churn Prediction

A machine learning project for predicting whether a customer is likely to churn based on demographic, service, contract, and payment information.

## Overview

Customer churn is an important problem for subscription-based businesses. Predicting which customers are likely to leave can help businesses better understand customer behavior and support customer retention strategies.

This project builds a **binary classification model using XGBoost** to predict customer churn. The model is evaluated using **accuracy, precision, recall, and F1-score**, with F1-score used as the primary metric for model selection.

## Dataset

The dataset is from the Kaggle competition **Playground Series S6E3**.

The training dataset contains **594,194 observations and 21 columns**, including:

* Demographic information
* Service-related information
* Contract information
* Payment information
* Customer churn target

The raw CSV files are **not included in this repository**.

Before running the notebook, download the competition dataset from Kaggle and place the files in the `data/` directory:

```text
data/
├── train.csv
└── test.csv
```

## Project Structure

```text
customer_churn_prediction/
│
├── data/
│   └── README.md
│
├── notebooks/
│   └── customer_churn_analysis.ipynb
│
├── results/
│   └── README.md
│
├── .gitignore
├── requirements.txt
└── README.md
```

## Machine Learning Workflow

The project follows the following workflow:

1. Exploratory Data Analysis
2. Data Preprocessing
3. Train / Validation Split
4. XGBoost Model Training
5. Hyperparameter Tuning with GridSearchCV
6. Model Evaluation
7. Final Model Training
8. Prediction on the Test Set
9. Submission File Generation

## Exploratory Data Analysis

The dataset is examined to understand its structure and characteristics, including:

* Dataset dimensions
* Sample observations
* Missing values
* Number of unique values
* Data types
* Categorical features
* Numerical features
* Target variable distribution

The available training features contain **no missing values**, so no missing-value imputation is required during preprocessing.

## Data Preprocessing

Categorical features are converted into numerical representations before model training.

The preprocessing includes:

* Encoding binary categorical variables
* One-hot encoding multi-class categorical variables
* Separating the target variable `Churn` from the input features
* Converting the target variable into binary values
* Splitting the data into training and validation sets

The target variable is encoded as:

```text
Yes → 1
No  → 0
```

A stratified train/validation split is used to maintain the class distribution between the two subsets.

## Model

### XGBoost

**XGBoost (Extreme Gradient Boosting)** is used as the primary classification algorithm.

The model learns relationships between customer characteristics and churn behavior using features related to:

* Customer demographics
* Services
* Contracts
* Payment methods
* Other customer account information

XGBoost was selected because it is a strong tree-based algorithm for structured/tabular data and can capture nonlinear relationships between features.

## Hyperparameter Tuning

`GridSearchCV` is used to search for a suitable combination of XGBoost hyperparameters.

The following parameters are explored:

* `max_depth`
* `min_child_weight`
* `learning_rate`
* `n_estimators`

The original grid contains **81 hyperparameter combinations**.

With **5-fold cross-validation**, this results in:

```text
81 combinations × 5 folds = 405 model fits
```

The primary optimization metric is **F1-score**.

F1-score is used because it considers both precision and recall and is therefore useful when evaluating a churn classification problem where correctly identifying churners is important.

## Evaluation

The tuned model is evaluated on a held-out validation set using four classification metrics:

| Metric    | Description                                            |
| --------- | ------------------------------------------------------ |
| Accuracy  | Proportion of all observations classified correctly    |
| Precision | Proportion of predicted churners that actually churned |
| Recall    | Proportion of actual churners correctly identified     |
| F1-score  | Harmonic mean of precision and recall                  |

The detailed evaluation results and model performance can be found in the Jupyter notebook.

## Final Model and Prediction

After hyperparameter tuning, the best XGBoost configuration obtained from `GridSearchCV` is used for the final model.

The final model is then used to generate churn predictions for the Kaggle test dataset.

The prediction output contains:

```text
id
Churn
```

The generated prediction file can then be submitted to the Kaggle competition.

## How to Run

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
cd customer_churn_prediction
```

### 2. Create a virtual environment

```bash
python3 -m venv .venv
```

Activate the environment:

```bash
source .venv/bin/activate
```

On Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add the dataset

Download the dataset from the Kaggle competition and place the following files inside the `data/` directory:

```text
data/
├── train.csv
└── test.csv
```

### 5. Run the notebook

Open:

```text
notebooks/customer_churn_analysis.ipynb
```

Run the notebook from beginning to end.

## Future Improvements

Potential improvements for future versions of the project include:

* Feature engineering
* More extensive hyperparameter tuning
* Comparison with other tree-based models
* Classification threshold tuning
* Feature importance analysis
* Model interpretability using SHAP
* Further optimization of model training time

## Technologies

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Jupyter Notebook
* Kaggle

## Kaggle Results

This project was submitted to the Kaggle competition **Playground Series S6E3**.

- **Kaggle Competition:** [Playground Series S6E3](YOUR_COMPETITION_LINK)
- **Kaggle Submission:** [View my submission and score](YOUR_SUBMISSION_LINK)
- **Validation F1-score:** `YOUR_F1_SCORE`
