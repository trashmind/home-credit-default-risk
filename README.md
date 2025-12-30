# Home Credit Default Risk Prediction 📊

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-LightGBM%20%7C%20ScikitLearn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📖 Project Overview
This project is a Capstone Project for the **Home Credit Indonesia Virtual Internship Experience**. The primary objective is to build a robust Machine Learning model to predict the probability of a client's repayment ability (Default Risk).

By analyzing clients' historical data from **7 relational tables**, we developed a comprehensive scoring engine that helps the company minimize credit default risk while maximizing financial inclusion for unbanked populations.

## 🚀 Key Features & Highlights
* **End-to-End Modular Pipeline:** The code is structured into modular functions (Data Loading, Aggregation, Preprocessing, Modeling, Visualization) for reproducibility and easy debugging.
* **Complex Data Integration:** Merged 7 different tables (Bureau, Previous Applications, POS Cash, Installments, etc.) to create a **360-degree Customer View**.
* **Robust Error Handling:** Implemented safety checks for file loading, memory management (`gc.collect`), and empty dataframes to prevent crashes during execution.
* **Advanced Modeling:** Utilized **LightGBM** (Gradient Boosting) with `early_stopping` and `class_weight` balancing to handle the imbalanced dataset effectively.

## 🛠️ Technical Approach

### 1. Data Strategy
* **Aggregations:** Transformed transactional history (one-to-many) into statistical features (Mean, Max, Sum, Variance) per customer.
* **Feature Engineering:** Created domain-specific financial ratios (e.g., `Credit-to-Income Ratio`, `Annuity-to-Income Ratio`).
* **Memory Optimization:** Reduced memory usage by ~50% using automatic type downcasting (Float64 -> Float32).

### 2. Preprocessing
* **Imputation:** Used **Median Strategy** to handle missing values, ensuring robustness against outliers.
* **Encoding:** One-Hot Encoding for categorical variables.
* **Scaling:** MinMaxScaler applied specifically for Logistic Regression (Baseline).

### 3. Model Evaluation
We used **ROC-AUC (Area Under the Receiver Operating Characteristic Curve)** as the primary metric due to the highly imbalanced nature of the target variable (~8% default rate).

| Model | ROC-AUC Score | Status |
| :--- | :--- | :--- |
| Logistic Regression | ~0.60 - 0.68 | Baseline |
| **LightGBM** | **0.78** | **Champion Model** |

## 📈 Business Insights (Visualized)
The notebook generates 4 key business visualizations automatically:
1.  **Feature Importance:** Identified `EXT_SOURCE` (External Credit Scores) and `DAYS_BIRTH` (Age) as the top risk drivers.
2.  **External Source Correlation:** Heatmap showing a strong negative correlation between external scores and default risk.
3.  **Age Risk Profile:** Bar chart revealing that younger clients (< 25 years) have a significantly higher default rate compared to older segments.
4.  **ROC Curve:** Visual confirmation of the model's discrimination power.

## 📂 Repository Structure
```text
.
├── notebooks/
│   └── home_credit_end_to_end.ipynb  # The main modular notebook
├── data/                             # Dataset folder (not uploaded)
├── .gitignore                        # Git configuration
├── requirements.txt                  # Dependencies
└── README.md                         # Project documentation
```


## 💻 How to Run

1. **Clone the repository:**

git clone [https://github.com/trashmind/home-credit-default-risk.git](https://github.com/trashmind/home-credit-default-risk.git)

2. **Install dependencies:**

pip install -r requirements.txt

3. **Run the Notebook:** Open notebooks/home_credit_end_to_end.ipynb in Jupyter Notebook or Google Colab. Ensure you have the dataset files (application_train.csv, etc.) in the correct directory.


## 🤝 **Acknowledgements**
Home Credit Indonesia for the challenging dataset and internship opportunity.
Rakamin Academy for the learning platform.

Created by Syahrul
