# Data Quality Checks — Company Financial Data
### Statista Case Study

---

## Overview

This project implements automated data quality checks on company data extracted from external sources such as APIs and web scraping. The goal is to detect and flag potential data issues **before** the data is stored in the database.

Each check adds a flag column to the original dataset, making it easy to filter, review, and fix issues downstream.

---

## Repository Contents

| File | Description |
|------|-------------|
| `Data_Quality_checks.ipynb` | Main Jupyter notebook with all quality checks |
| `CaseStudy_Quality_sample25.xlsx` | Input dataset (372 rows, 10 columns) |
| `casestudy_quality_checked_output.xlsx` | Output dataset with flag columns added |
| `quality_issues.png` | Bar chart summarising issues found per check |

---

## Dataset

- **Source:** Company financial data extracted from APIs and web scraping
- **Size:** 372 rows × 10 columns

### Columns

| Column | Description |
|--------|-------------|
| `timevalue` | Fiscal year |
| `providerkey` | Unique company identifier |
| `companynameofficial` | Official company name |
| `fiscalperiodend` | Fiscal year end date (expected format: DD-Mon) |
| `operationstatustype` | e.g. ACTIVE |
| `ipostatustype` | e.g. PUBLIC |
| `geonameen` | Country name |
| `industrycode` | Industry code and description |
| `REVENUE` | Revenue value |
| `unit_REVENUE` | Currency unit of revenue |

---

## Quality Checks

Seven automated checks are implemented. The brief required at most 5 — checks 1–5 are the core submission; checks 6 and 7 are additional.

| # | Check | Flag Column | Issues Found | % of Rows |
|---|-------|-------------|:------------:|:---------:|
| 1 | **Completeness** | `flag_completeness` | 93 | 25.0% |
| 2 | **Consistency** | `flag_revenue_unit_consistency` | 15 | 4.0% |
| 3 | **Correctness** | `flag_revenue_correctness` | 3 | 0.8% |
| 4 | **Format Validity** | `flag_fiscalperiod_format` | 69 | 18.5% |
| 5 | **Outlier Detection** | `revenue_outlier_flag` | 117 | 31.5% |
| 6 | **LLM Validation** | `llm_companydata_check` | — | — |
| 7 | **Uniqueness**  | `duplicate_flag` | 0 | 0.0% |

---

## Setup

### Requirements

```bash
pip install pandas openpyxl matplotlib openai
```

### OpenAI API Key

The LLM check (Check 6) requires an OpenAI API key. Set it as an environment variable.

1. Clone the repository
```bash

### Running the Notebook

1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/data-quality-checks.git
cd data-quality-checks
```

2. Install dependencies
```bash
pip install pandas openpyxl matplotlib openai
```

3. Open the notebook
```bash
jupyter notebook Data_Quality_checks.ipynb
```

4. Run all cells (`Kernel → Restart & Run All`)

---



- **Python 3**
- **pandas** — data manipulation
- **re** — regex pattern matching
- **matplotlib** — results visualisation
- **openai** — GPT-4.1-mini API for LLM-based validation
