# NumPy Fundamentals and Matplotlib Visualisation

Two notebooks: NumPy array operations + a benchmark that quantifies vectorisation speedup, and core Matplotlib plotting techniques.

## Notebooks

### `numpy-matrix-benchmark.ipynb`

| Topic | Detail |
|---|---|
| Array creation | `arange` + `reshape`, `linspace`, custom `matrix_round()` |
| Matrix inverse | `np.linalg.inv()`, identity verification $V V^{-1} = I$ |
| Loop benchmark | 700×700 matrix multiply with nested Python loops |
| NumPy benchmark | Same operation with `np.dot()` |
| **Speedup** | **~3,654×** (avg of 30 runs: 39.68s loops vs 0.011s NumPy) |

Why 3,654×? NumPy delegates to BLAS — compiled Fortran/C routines that exploit CPU SIMD instructions and cache-optimised memory layouts. Python loops pay per-operation interpreter overhead that BLAS eliminates entirely.

---

### `matplotlib-visualisation.ipynb`

| Plot | Technique |
|---|---|
| E = mc² (linear) | `fig, ax` OO API, labels, axis limits, grid |
| E = mc² (log scale) | `set_yscale('log')`, `grid(axis='y')` |
| Treasury yield curves | Dual y-axis with `twinx()` — 2007 vs 2020 rates |
| subplot2grid layout | Asymmetric 2×2 grid with `rowspan=2` |

## How to run

```bash
pip install numpy matplotlib tqdm jupyter
jupyter notebook
```

> **Note:** The 30-run loop benchmark in `numpy-matrix-benchmark.ipynb` takes ~20 minutes. Pre-measured results are hardcoded for the speedup calculation — re-running is optional.
