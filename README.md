Customer Churn Prediction

A machine learning project for predicting whether a customer will churn
based on demographic, service, contract, and payment information.

Overview

Customer churn is an important problem for subscription-based
businesses. Identifying customers who are likely to churn can help
businesses better understand customer behavior and support customer
retention strategies.
\
This project develops a binary classification model using XGBoost and
evaluates its performance using F1-score, precision, recall, and
accuracy.

Dataset

The dataset is from the Kaggle competition Playground Series S6E3.

The training dataset contains 594,194 observations and 21 columns,
including demographic information, service-related features, contract
and payment information, and the target variable Churn.

The raw CSV files are not included in this repository.

Before running the notebook, download the competition dataset from
Kaggle and place train.csv and test.csv in the data/ directory.

See data/README.md for more information.

Project Structure

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
Workflow

1.  Exploratory Data Analysis
2.  Data Preprocessing
3.  Train / Validation Split
4.  XGBoost Model Training
5.  Hyperparameter Tuning with GridSearchCV
6.  Model Evaluation
7.  Final Model Training
8.  Prediction on the Test Set

Exploratory Data Analysis

The dataset is examined to understand:

-   Dataset dimensions
-   Sample observations
-   Missing values
-   Number of unique values
-   Data types
-   Categorical and numerical features

The training data contains no missing values in the available columns.

Data Preprocessing

The preprocessing stage includes:

-   Encoding binary categorical features into numerical values
-   One-hot encoding multi-class categorical features
-   Separating the target variable Churn from the input features
-   Splitting the data into training and validation sets

The target variable is encoded as:

Yes -> 1 No -> 0

Model

XGBoost

XGBoost is used as the primary classification model for predicting
customer churn.

The model uses customer demographic, service, contract, and
payment-related features to predict whether a customer is likely to
churn.

Hyperparameter Tuning

GridSearchCV is used to systematically evaluate different combinations
of XGBoost hyperparameters using 5-fold cross-validation.

The following hyperparameters are explored:

-   max_depth
-   min_child_weight
-   learning_rate
-   n_estimators

The grid contains 81 hyperparameter combinations, resulting in 405 model
fits with 5-fold cross-validation.

F1-score is used as the primary optimization metric because it balances
precision and recall.

Evaluation

The tuned model is evaluated on a held-out validation set using:

-   Accuracy: proportion of correctly classified observations
-   Precision: proportion of predicted churners that actually churned
-   Recall: proportion of actual churners correctly identified
-   F1-score: harmonic mean of precision and recall

The detailed evaluation results are available in the Jupyter notebook.

Final Model and Prediction

After selecting the best hyperparameters through GridSearchCV, the final
XGBoost model is trained using the available training data.

The trained model is then used to generate churn predictions for the
test dataset.

The predictions are formatted into a submission file containing id and
Churn.

How to Run

1.  Clone the repository.
2.  Create and activate a virtual environment:

python3 -m venv .venv source .venv/bin/activate

3.  Install dependencies:

pip install -r requirements.txt

4.  Download the Kaggle dataset and place train.csv and test.csv inside
    the data/ directory.
5.  Open notebooks/customer_churn_analysis.ipynb and run the notebook
    from beginning to end.

Future Improvements

Potential improvements include:

-   Feature engineering
-   More extensive hyperparameter tuning
-   Comparison with other tree-based models
-   Classification threshold tuning
-   Additional model interpretability analysis
