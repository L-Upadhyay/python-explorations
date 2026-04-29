# Decision Tree Impurity Metrics and Recursion

Four topics implemented from scratch — no scikit-learn, just `math` and pure Python.

## Topics

### 1 & 2 — Impurity Metrics (2-class and k-class)

Three impurity measures implemented from first principles, generalised to any number of classes:

| Measure | Formula |
|---|---|
| Misclassification | $1 - \max_i(p_i)$ |
| Gini | $1 - \sum_i p_i^2$ |
| Entropy | $-\sum_i p_i \log_2 p_i$ |

**Impurity reduction** = parent impurity − weighted average of child impurities.

Results for parent node (60, 40):

| Split | Misclassification Δ | Gini Δ | Entropy Δ |
|---|---|---|---|
| (35,5) \| (25,35) | 0.1000 | 0.1008 | 0.1656 |
| (40,10) \| (20,30) | 0.1000 | 0.0800 | 0.1245 |
| (45,25) \| (15,15) | ~0 | 0.0086 | 0.0128 |

Split 1 is optimal. Entropy is the most sensitive discriminator between splits.

### 3 — Gini Index Proof

$L_{Gini} = 1 - \sum_i \hat{p}_i^2$ follows directly from $\sum_i \hat{p}_i(1-\hat{p}_i)$ using $\sum_i \hat{p}_i = 1$.

### 4 — Recursion

| Function | Base case(s) | Recursive step |
|---|---|---|
| `fib(n)` | F(0)=0, F(1)=1 | F(n) = F(n-1) + F(n-2) |
| `is_palindrome(s)` | len(s) ≤ 1 | s[0]==s[-1] and check s[1:-1] |

## How to run

```bash
jupyter notebook decision-tree-impurity-recursion.ipynb
```

No dependencies beyond Python stdlib (`math`).
