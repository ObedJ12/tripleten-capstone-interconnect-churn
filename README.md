# Interconnect Customer Churn Prediction (TripleTen Capstone)

Interconnect, a telecom operator, wants to predict which customers will churn so it can offer them retention promotions. This is my final project for the TripleTen Data Science bootcamp.

## Approach
- I merged four source tables (`contract`, `personal`, `internet`, `phone`) on `customerID`, for a total of 7,043 customers.
- In EDA, the churn rate came out to 26.54%. Churn is much higher on month-to-month contracts (42.71%) than on one-year (11.27%) or two-year (2.83%) contracts, and churners tend to pay more per month and have shorter tenure.
- I used a stratified train/test split (5,634 / 1,409) and a scikit-learn pipeline for imputation, encoding, and scaling.
- The primary metric is AUC-ROC, with accuracy as a secondary metric.

## Results
| Model | AUC-ROC | Accuracy |
|---|---|---|
| Dummy (most_frequent) | 0.5000 | 0.7346 |
| **Logistic Regression (class-balanced)** | **0.8518** | **0.7509** |

I chose the class-balanced Logistic Regression model. Its scores can be used to flag high-risk customers for retention campaigns.

## Repo layout
```
notebooks/01-work-plan.ipynb      EDA and work plan
notebooks/02-solution-code.ipynb  modeling code
reports/solution-report.ipynb     final written report
data/                             put the datasets here (not committed)
```

## Data
The data isn't included in this repo. Put `contract.csv`, `personal.csv`, `internet.csv`, and `phone.csv` in `data/`. The notebooks originally read them from `/datasets/final_provider/`, so update that path to `data/`.

## How to run
```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```
## Tools
Python, pandas, NumPy, Matplotlib, seaborn, scikit-learn, and Jupyter.

_The notebooks keep their TripleTen reviewer comments._
