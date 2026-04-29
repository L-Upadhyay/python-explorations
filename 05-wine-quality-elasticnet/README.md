# Wine Quality Prediction with ElasticNet Regression

Predicting wine quality scores from physicochemical properties using regularized regression, with hyperparameter tuning via cross-validation.

## Pipeline

| Step | Details |
|---|---|
| Data loading | Directly from UCI ML Repository — no local file needed |
| EDA | Summary stats, null checks, key distributions |
| Visualization | Quality vs SO₂, quality vs pH (alcohol as hue) |
| Preprocessing | `StandardScaler` fit on train only — prevents data leakage |
| Baseline model | `ElasticNet(alpha=1.0, l1_ratio=0.5)` |
| Tuned model | `ElasticNetCV` with 5-fold CV across 4×5 parameter grid |

## Results

| Model | MSE | R² |
|---|---|---|
| Baseline (`alpha=1.0`, `l1_ratio=0.5`) | 0.657 | ~0.00 |
| Tuned (`alpha=0.01`, `l1_ratio=0.9`) | 0.393 | ~0.40 |
| **Improvement** | **40% MSE reduction** | **+0.40 R²** |

## Key concepts demonstrated

- **ElasticNet** — combines L1 (Lasso) and L2 (Ridge) penalties; useful when features are correlated
- **`alpha`** — overall regularization strength; higher = more shrinkage
- **`l1_ratio`** — L1/L2 mix; 0 = pure Ridge, 1 = pure Lasso
- **Data leakage prevention** — scaler fit only on training set, transform applied to test
- **Why λ* = 0 when minimising training loss directly** — the regularization term is always non-negative, so the loss function is minimised by eliminating it; cross-validation is needed to select λ using generalisation error instead

## How to run

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
jupyter notebook wine-quality-elasticnet.ipynb
```

No local data files needed — dataset loads from URL.

## Dataset
UCI ML Repository — Wine Quality (Red Wine, Vinho Verde).  
Source: Cortez et al., *Modeling wine preferences by data mining from physicochemical properties.* Decision Support Systems, 2009.
