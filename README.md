# DuckDB Data Warehousing Training

A hands-on training course for building analytical data pipelines with DuckDB.
No database server required — everything runs inside GitHub Codespaces.

## Getting Started

### Option 1: Open in GitHub Codespaces (recommended)

Click **Code → Codespaces → Create codespace on main** in GitHub.
The environment will install all dependencies automatically.

Once the Codespace is ready, open the notebooks from the file explorer and select **Python 3** as the kernel.

### Option 2: Run locally

```bash
pip install -r requirements.txt
jupyter notebook
```

---

## Notebooks

### `intro_to_duckdb.ipynb`

**Start here.** Covers:
- What DuckDB is and why we're using it
- How to connect and run SQL from a notebook
- Creating tables and inserting data
- Exploring your database with `SHOW TABLES` and `information_schema`
- Running analytical queries and reading directly from CSV files

No prior Python knowledge required.

---

### `exercise_01_jaffle_shop.ipynb`

Build a data warehouse for **The Jaffle Shop** using a dbt-style layered architecture.

**You'll build:**

```
Raw CSVs → Staging layer → Marts layer
              stg_customers    fct_orders
              stg_orders       dim_customers
              stg_payments     monthly_jaffle_metrics
```

**Skills:** `CREATE TABLE AS SELECT`, `JOIN`, `GROUP BY`, `CASE WHEN`, `SUM`, `COUNT DISTINCT`

---

### `exercise_02_constraints.ipynb`

Design a schema for an HR system, applying all six SQL constraint types.

**You'll build:**
- A `company` schema
- `company.departments` table
- `company.employees` table (with a foreign key to departments)

**Constraints covered:** `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `NOT NULL`, `CHECK`, `DEFAULT`

---

### `exercise_03_scd.ipynb`

Implement a **Slowly Changing Dimension Type 2** pipeline from scratch — the same pattern used by dbt's `snapshot` block.

**You'll build:**
- `dim_students` — current state dimension table
- `snapshot_students` — full history table with SCD tracking columns

**You'll implement:** initial load → detect changes → close old records → insert new versions

---

## Data

| File | Description |
|---|---|
| `data/raw_customers.csv` | 100 Jaffle Shop customers |
| `data/raw_orders.csv` | 99 orders |
| `data/raw_payments.csv` | 120 payment attempts |
| `data/scd/students_old.csv` | 6 students — initial state |
| `data/scd/students_new.csv` | 6 students — updated state (4 have changed) |
