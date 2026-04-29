# python-explorations

A growing collection of Python notebooks — each one focused on a specific concept or technique, written to understand it deeply rather than just make it work.

---

## Notebooks

### [01 · Python Core Patterns](./01-python-core-patterns/)

Four fundamental Python patterns in one notebook:

| Section | What it covers |
|---|---|
| Comprehensions | List and dict comprehensions, from simple transforms to nested structures |
| Functional tools | `map()`, `filter()`, `lambda` — binary conversion, palindrome detection, prime filtering |
| Text processing | Tokenization, punctuation stripping, and vocabulary analysis on the Gettysburg Address |
| OOP | A generic n-dimensional `Vector` class with Euclidean distance, addition, and 2-norm |

**Highlights:**
- `is_prime` checks divisors only up to √n — O(√n) vs O(n)
- `unique_words()` uses a `set` for O(1) deduplication, then sorts for determinism
- `Vector` uses `None` default instead of mutable list default (avoids the classic Python gotcha)
- The 5D worked example shows `__str__()` doing its job — printing an object without touching its attributes directly

---

## Setup

```bash
git clone https://github.com/YOUR_USERNAME/python-explorations.git
cd python-explorations
pip install jupyter
jupyter notebook
```

No external dependencies — all notebooks use Python standard library only unless noted.

---

## Structure

```
python-explorations/
└── 01-python-core-patterns/
    ├── notebook.ipynb
    └── gettysburg.txt
```

More notebooks coming as new topics are explored.
