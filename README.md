# python-explorations

A growing collection of Python notebooks — each one focused on a specific concept or technique, written to understand it deeply rather than just make it work.

## Notebooks

| # | Topic | Key concepts | Data |
|---|---|---|---|
| [01](./01-python-core-patterns/) | Python Core Patterns | Comprehensions, `map`/`filter`, text processing, OOP | Gettysburg Address (text) |
| [02](./02-numpy-matplotlib/) | NumPy + Matplotlib | Array ops, matrix inverse, 3,654× speedup benchmark, 4 plot types | — |
| [03](./03-pandas-seaborn/) | Pandas + Seaborn | 12 EDA operations on hotel bookings, 4 Seaborn visualisation types | Hotel bookings (119K rows) |
| [04](./04-california-housing-regression/) | Linear Regression | EDA, feature engineering, `ocean_proximity` encoding, MAE/RMSE | California Housing (sklearn) |
| [05](./05-wine-quality-elasticnet/) | ElasticNet Regression | Regularisation, `ElasticNetCV`, 40% MSE reduction via cross-validation | Wine Quality (UCI, URL) |
| [06](./06-logistic-regression-hearing/) | Logistic Regression | Sigmoid proofs, tanh adaptation, binary classification, 91.7% accuracy | Hearing test (5K rows) |
| [07](./07-decision-tree-impurity-recursion/) | Decision Tree Theory | Misclassification / Gini / Entropy from scratch, Gini proof, recursion | — |
| [08](./08-decision-trees/) | Decision Trees (Applied) | Classification + regression trees, hyperparameter tuning, cost-complexity pruning | Penguins + Hitters |

---

## Highlights

**02 — NumPy speedup benchmark**  
Loop vs `np.dot()` on 700×700 matrices, averaged over 30 runs: **~3,654× speedup**. Explains why — BLAS, SIMD, cache locality.

**05 — ElasticNet cross-validation**  
Baseline MSE 0.657 → tuned MSE 0.393 after `ElasticNetCV`. Also proves why minimising regularised loss directly always gives λ* = 0.

**06 — Logistic regression theory + application**  
Proves sigmoid range, monotonicity, and limits analytically, then applies the model to predict hearing test outcomes (91.7% accuracy, 5K participants).

**08 — Cost-complexity pruning**  
Full unpruned tree: 178 leaves, train MSE ≈ 0.001, test MSE ≈ 0.48 (severe overfitting). Optimal pruned tree T(α*): **6 leaves**, test R² ≈ 0.61 — 172 leaves removed.

---

## Structure

Each subfolder is self-contained:
```
XX-topic-name/
├── notebook.ipynb      ← main work
├── README.md           ← what it covers + results
└── data/               ← local data files (if any)
```

## Running any notebook

```bash
git clone https://github.com/L-Upadhyay/python-explorations.git
cd python-explorations/XX-topic-name
pip install -r requirements.txt   # or see notebook README for dependencies
jupyter notebook
```

Common dependencies: `numpy pandas matplotlib seaborn scikit-learn jupyter`
