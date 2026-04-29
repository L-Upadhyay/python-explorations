# California Housing Price Prediction

End-to-end regression pipeline on the 1990 California Census housing dataset — from raw data loading through EDA, feature engineering, and linear regression evaluation.

## Pipeline

| Step | What happens |
|---|---|
| Data loading | Fetched directly from scikit-learn (`fetch_california_housing`) — no CSV needed |
| EDA | Null checks, feature descriptions, geographic diversity (862 unique latitudes, 844 longitudes) |
| Feature engineering | Merges external `ocean_proximity` column; label-encodes 5 categories for regression |
| Visualization | Boxplot (ocean proximity vs price), hexbin jointplot (income vs price) |
| Modelling | Linear regression, 80/20 train/test split, MAE + RMSE evaluation, actual vs predicted scatter |

## Results

| Metric | Value | Interpretation |
|---|---|---|
| MAE | 0.5334 | ~$53,000 average prediction error |
| RMSE | 0.7454 | Larger errors exist — likely top-coded $500K values |

## Key observations
- Ocean proximity is a strong price predictor — island/coastal blocks are ~2× inland prices
- Median income has the strongest linear correlation with house value
- A hard cap at $500,000 in the data (census top-coding) causes visible prediction artifacts
- Linear regression captures the trend but a non-linear model (e.g. Random Forest) would reduce error further

## How to run

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
jupyter notebook california-housing-regression.ipynb
```

> **Note on `Ocean_Proximity.csv`:** This file is not included in the repo (raw data). It contains a single `ocean_proximity` column aligned by row index to the California Housing dataset. You can recreate it by downloading the full dataset from [Kaggle](https://www.kaggle.com/datasets/camnugent/california-housing-prices) and extracting that column.

## Dataset
1990 California Census — 20,640 block groups, 9 features.  
Source: Pace, R. Kelley, and Ronald Barry. *Sparse spatial autoregressions.* Statistics & Probability Letters 33.3 (1997).
