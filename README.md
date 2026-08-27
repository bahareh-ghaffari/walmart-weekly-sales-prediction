# Walmart Weekly Sales Prediction

An end-to-end machine-learning project that analyzes historical weekly sales from 45 Walmart stores and compares regression models for predicting future store-level sales.

## Project Overview

Accurate weekly sales predictions can support inventory planning, staffing, budgeting, and promotional decisions. This project explores store, calendar, holiday, weather, and economic variables before testing several regression approaches using time-aware validation.

## Key Results

| Model | Test MAE | Test RMSE | Test R² |
|---|---:|---:|---:|
| Tuned Decision Tree | **$72,798** | **$102,746** | **0.963** |
| Tuned Gradient Boosting | $78,500 | $119,966 | 0.950 |
| Tuned Random Forest | $79,513 | $114,721 | 0.954 |
| Linear Regression | $92,751 | $124,413 | 0.946 |

The Tuned Decision Tree delivered the strongest holdout-period performance. Compared with Linear Regression, it reduced MAE by approximately **21.5%** and RMSE by approximately **17.4%**.

![Model MAE comparison](assets/model_mae_comparison.png)

## Business Insights

- Holiday weeks averaged approximately **7.84% higher sales** than regular weeks.
- The strongest sales spikes occurred around **Thanksgiving and Christmas**.
- Store performance varied substantially: the highest-selling store averaged about **8.1 times** the weekly sales of the lowest-selling store.
- Store identity and seasonal patterns were more informative than any single economic variable.
- High-sales observations were retained because they represented meaningful seasonal demand, not obvious data-entry errors.

## Methodology

1. Loaded and inspected 6,435 observations from 45 stores.
2. Checked data types, missing values, duplicates, descriptive statistics, and potential outliers.
3. Explored sales distributions, store differences, holiday effects, seasonality, and correlations.
4. Engineered year, month, and week-of-year features.
5. Used the first 80% of weekly dates for training and the final 20% for testing.
6. Applied time-series cross-validation during hyperparameter tuning.
7. Compared Linear Regression, Decision Tree, Random Forest, and Gradient Boosting using MAE, RMSE, and R².

The chronological split is important because randomly shuffling time-based data could allow future information to influence model training.

## Repository Structure

```text
.
├── walmart_weekly_sales_prediction.ipynb  # Complete analysis and modeling workflow
├── assets/
│   └── model_mae_comparison.png           # Model comparison used in this README
├── requirements.txt                       # Python dependencies
└── README.md                           # Project summary
```

## Tools and Technologies

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- KaggleHub
- Jupyter Notebook and Google Colab

## How to Run

1. Clone or download this repository.
2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open `walmart_weekly_sales_prediction.ipynb` in Jupyter Notebook or Google Colab.
4. Run the cells from top to bottom. The notebook downloads the public dataset through KaggleHub.

Dataset: [Walmart Dataset on Kaggle](https://www.kaggle.com/datasets/yasserh/walmart-dataset)

## Limitations and Next Steps

- The dataset ends in October 2012, so the test period does not include the major year-end holiday peak.
- Store identifiers capture location-level differences but do not explain the operational reasons behind them.
- Additional features such as promotions, markdowns, store size, departments, local events, and lagged sales could improve predictions.
- Future work could compare the current models with dedicated time-series methods and use rolling-origin backtesting across several prediction windows.

## Author

**Bahareh Ghaffari**  
Data Analytics and Business Intelligence
