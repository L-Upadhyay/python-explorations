# Logistic Regression: Theory and Application

Two parts: mathematical analysis of the sigmoid function, then an applied binary classification task on a hearing study dataset.

## Part 1 — Sigmoid Function Properties

Mathematical proofs + numerical verification for:
- **Range**: $f(x) \in (0,1)$ for all $x \in \mathbb{R}$
- **Monotonicity**: $f'(x) > 0$ everywhere (strictly increasing)
- **Limits**: $\lim_{x\to+\infty} f(x) = 1$, $\lim_{x\to-\infty} f(x) = 0$

**Adapting to {+1, −1} labels** — two equivalent approaches:
- Via `tanh(z/2) = 2σ(z) − 1` with threshold at 0
- Via unchanged sigmoid with modified label mapping (≥ 0.5 → +1, else −1)

Both produce identical decision boundaries at z = 0.

## Part 2 — Hearing Test Classification

| Step | Detail |
|---|---|
| Dataset | 5,000 participants: age + physical score → hearing test pass/fail |
| Class balance | 60% pass (3,000), 40% fail (2,000) — stratified split used |
| Visualisation | 2D scatter, pairplot, 3D scatter |
| Preprocessing | StandardScaler fit on train only |
| Model | Logistic Regression |

### Results

| Metric | Value |
|---|---|
| Test accuracy | **91.7%** |
| Class 1 recall | 0.947 |
| Class 0 recall | 0.872 |

### Key findings
- `physical_score` coefficient ≈ +3.55 — dominant predictor
- `age` coefficient ≈ −0.86 — moderate negative effect
- 4:1 magnitude ratio confirms EDA observation that physical fitness separates classes more clearly than age

## How to run

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
jupyter notebook logistic-regression-hearing.ipynb
```

> **Data file:** `hearing_test.csv` is included in this folder (5,000 rows, 3 columns).

## Dataset
Hearing study: 5,000 participants evaluated on age and physical fitness, tested for high-frequency tone perception.
