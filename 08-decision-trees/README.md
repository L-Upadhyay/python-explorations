# Decision Trees — Classification and Regression

Two notebooks covering the full decision tree workflow: classification on penguin species and regression on baseball salaries, including cost-complexity pruning.

## Notebooks

### `classification-trees.ipynb` — Palmer Penguins Species Classifier

| Step | Detail |
|---|---|
| Dataset | 344 penguins, 3 species (Adélie, Chinstrap, Gentoo), 7 features |
| Data cleaning | Sorted null table, 2.91% missing → dropna; remove ambiguous `'.'` sex entries |
| Feature engineering | One-hot encode `island` (3→2 dummies) and `sex` (2→1 dummy) — L−1 rule |
| Visualisation | Scatterplot, pairplot, categorical boxplot by sex |
| Model | `DecisionTreeClassifier`, 70/30 split, confusion matrix |
| Hyperparameters explored | `max_depth=2`, `max_leaf_nodes=3`, `criterion='entropy'` |

**Results:** ~95% test accuracy. Gentoo perfectly classified; main errors are Adélie↔Chinstrap (the two most similar species in feature space).

---

### `regression-trees.ipynb` — Hitters Salary Prediction + Pruning

| Step | Detail |
|---|---|
| Dataset | 322 MLB players, `Years` + `Hits` → `log(Salary)` |
| Log transform | Reduces right-skew; distribution closer to Gaussian |
| 5-leaf tree | Matches ISLP textbook Fig. 8.1; decision region plot |
| Full tree | 178 leaves, train MSE ≈ 0.001, test MSE ≈ 0.48 — clear overfitting |
| Cost-complexity pruning | Sweeps 137 α values; plots impurity and R² vs α |
| Optimal T(α*) | α* ≈ 0.022, **6 leaves**, test R² ≈ 0.61 — 172 leaves pruned |

**Key insight:** `Years ≤ 4.5` is the strongest single split — experienced players earn significantly more regardless of hitting stats.

## How to run

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
jupyter notebook
```

> **Data files** are in `data/` — `penguins_size.csv` and `Hitters.csv`.

## Dataset sources
- Palmer Penguins: Gorman KB, Williams TD, Fraser WR (2014). PLoS ONE 9(3): e90081.
- Hitters: ISLP textbook (James et al.), originally from the 1987 ASA Statistical Graphics Section.
