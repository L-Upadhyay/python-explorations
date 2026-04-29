# Pandas and Seaborn — Hotel Bookings and Credit Applications

Two notebooks: structured data analysis with Pandas on hotel booking data, and visualisation with Seaborn on credit application data.

## Notebooks

### `pandas-hotel-analysis.ipynb` — Hotel Booking Data

12 practical Pandas operations on 119,390 hotel bookings (2015–2017).

| Question | Technique |
|---|---|
| Load + inspect | `read_csv`, `head`, `shape`, `info` |
| Missing data | `isnull().sum()`, sorted by severity |
| Drop columns | `drop()` — removes `company` (94% null) and `agent` |
| Multi-condition filter | Boolean `&` with 3 simultaneous conditions |
| Top countries | `value_counts().head(5)` — one-liner |
| Mean ADR | `mean()` on numeric column |
| Derived column | `total_nights` = weekend + weekday nights |
| Total cost | `adr × total_nights` — vectorised element-wise multiply |
| Special requests | `loc[]` with boolean filter |
| Last name extraction | `str.split().str[-1].value_counts()` — chained string ops |
| Date range filter | `query()` vs boolean mask — both shown |

**Data:** `data/hotel_booking_data.csv` — included in repo.

---

### `seaborn-credit-applications.ipynb` — Credit Application Data

Four visualisation tasks demonstrating when to use each Seaborn plot type.

| Plot | Key technique |
|---|---|
| Age vs employment scatter | Filter `DAYS_EMPLOYED < 0`; convert negative days to years |
| Age distribution | `histplot` + `kde=True` |
| Income by family status | `catplot(kind='box')` ordered by median income |
| Correlation heatmap | Drop near-constant column; `corr()` + annotated heatmap |

**Data:** `application_record.csv` is **not included** (54MB — over GitHub's limit).  
Download from [Kaggle](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction) and place in `data/`.

## How to run

```bash
pip install pandas seaborn matplotlib jupyter
jupyter notebook
```
