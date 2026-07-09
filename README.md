# 🥊 UFC Fight Outcome Prediction using XGBoost

## Overview

This project predicts the probability of a fighter winning a UFC bout using historical fight data and advanced machine learning techniques. Instead of simply predicting the winner, the model estimates calibrated win probabilities that can be compared with betting market odds and used for analytical decision-making.

The project follows an end-to-end machine learning workflow, including data preprocessing, feature engineering, exploratory data analysis, model development, probability calibration, and model interpretation.

---

## Project Objectives

* Predict the winner of UFC fights using historical data.
* Estimate well-calibrated win probabilities rather than binary outcomes.
* Prevent data leakage by using time-based validation.
* Engineer domain-specific features such as Elo ratings, fighter activity, and betting information.
* Build a reproducible machine learning pipeline suitable for future fight predictions.

---

## Dataset

The dataset consists of historical UFC fight records containing fighter statistics, physical attributes, fight outcomes, and betting odds.

Examples of available information include:

* Fighter age
* Height
* Reach
* Weight class
* Stance
* Win/Loss records
* Knockout wins
* Submission wins
* Decision wins
* Striking statistics
* Grappling statistics
* Betting odds
* Fight dates

---

## Feature Engineering

Extensive feature engineering was performed to capture fighter skill, experience, activity, and matchup dynamics.

### Fighter Experience

* Total wins
* Total losses
* UFC wins
* UFC losses
* Total fights
* Championship fights
* Main events

### Performance Metrics

* Significant strikes landed per minute
* Strike accuracy
* Strike defense
* Takedown accuracy
* Takedown defense
* Knockdowns
* Submission averages

### Activity Features

* Days since last fight
* Average time between fights
* Number of fights in previous year
* Recent fight frequency

### Physical Matchup Features

* Age difference
* Reach difference
* Height difference
* Weight difference

### Historical Performance

* Win percentage
* Finish rate
* Decision rate
* Knockout rate
* Submission rate

### Elo Rating System

A dynamic Elo rating was implemented to estimate fighter strength over time.

Each fighter's rating is updated after every bout using only information available before that fight, preventing future information from leaking into the training data.

### Betting Features

* Opening odds
* Closing odds
* Implied probabilities
* Favourite/Underdog indicators
* Betting market disagreement

---

## Exploratory Data Analysis

EDA was conducted to understand the data distribution and identify important relationships.

Analysis included:

* Missing value analysis
* Feature distributions
* Correlation analysis
* Class balance
* Win rate trends
* Fighter age distribution
* Finish type frequencies

---

## Model Development

Several machine learning models were evaluated:

* Logistic Regression
* Random Forest
* XGBoost

XGBoost was selected as the final model due to its superior predictive performance and ability to capture complex nonlinear relationships.

---

## Validation Strategy

Unlike traditional random train-test splits, this project uses **time-based validation**.

Example:

* Training: Historical fights
* Validation: Later fights
* Testing: Most recent fights

This prevents future information from influencing predictions and better reflects real-world deployment.

---

## Hyperparameter Optimization

Hyperparameters were optimized to maximize predictive performance while reducing overfitting.

Parameters tuned include:

* Learning rate
* Maximum tree depth
* Number of estimators
* Minimum child weight
* Gamma
* Subsample ratio
* Column sampling ratio

---

## Probability Calibration

Raw model probabilities were calibrated to improve their reliability.

Calibration techniques evaluated include:

* Platt Scaling
* Isotonic Regression

Calibration quality was measured using:

* Brier Score
* Calibration Curve

This produces probabilities that better reflect real-world winning chances.

---

## Model Interpretation

Model explainability was performed using SHAP (SHapley Additive exPlanations).

Feature importance analysis helps identify the factors that contribute most to fight predictions.

Examples include:

* Elo Rating Difference
* Reach Difference
* Fighter Age
* Win Percentage
* Strike Differential
* Betting Odds
* Activity Level

---

## Project Structure

```text
ufc-fight-prediction/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_eda.ipynb
│   ├── 04_model_training.ipynb
│   ├── 05_model_evaluation.ipynb
│   └── 06_prediction.ipynb
│
├── src/
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── elo.py
│   ├── train.py
│   ├── predict.py
│   └── utils.py
│
├── models/
├── reports/
├── README.md
├── requirements.txt
└── LICENSE
```

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* SHAP
* Matplotlib
* Optuna
* Joblib

---

## Results

The final XGBoost model generates calibrated probabilities for UFC fights while maintaining a realistic evaluation through time-based validation.

The project demonstrates:

* End-to-end machine learning workflow
* Advanced feature engineering
* Time-aware model validation
* Probability calibration
* Model interpretability
* Reproducible project structure

---

## Future Improvements

Potential enhancements include:

* TrueSkill or Glicko fighter rating systems
* Bayesian skill estimation
* Fighter style embeddings
* Sequence models using fight history
* Ensemble learning
* Live prediction dashboard
* Automated data updates
* API deployment

---

## How to Run

Clone the repository:

```bash
git clone https://github.com/yourusername/ufc-fight-prediction.git
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the notebooks in order:

1. Data Cleaning
2. Feature Engineering
3. Exploratory Data Analysis
4. Model Training
5. Model Evaluation
6. Prediction

---

## Author

**Syed Ayaan Ahmad**

MSc Business Analytics & Artificial Intelligence (Warwick Business School)

Interests: Machine Learning, Predictive Analytics, Sports Analytics, Business Intelligence, Data Science
