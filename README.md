# DS340W Final Project: Construction Injury Severity

This repository is our final project submission for DS340W. It has two parts:

1. Replication of the author baseline pipeline.
2. Our novel implementation on cleaned data (deduplicated split workflow, plus CatBoost and a soft-voting ensemble).

## What Each File Is

| File | Purpose | Type |
|---|---|---|
| `Construction_Injury_Severity.py` | Original author-style baseline script we replicated. | Author code |
| `Injury Severity.xlsx` | Original dataset used by the author script/check notebook. | Author data |
| `Authors_Results_Check.ipynb` | Notebook copy of author-style training/evaluation used to confirm replication runs. | Replication check |
| `Construction_Injury_Novel_Implementation.ipynb` | Our main notebook: cleaned split pipeline + novel models + comparison tables. | Main project work |
| `Injury Severity_cleaned.xlsx` | Cleaned version of source data used in our novel workflow prep. | Project data |
| `construction_training_set_cleaned.csv` | Cleaned training split used by the novel notebook. | Project data |
| `construction_validation_set_cleaned.csv` | Cleaned validation split used by the novel notebook. | Project data |
| `construction_test_set_cleaned.csv` | Cleaned test split used by the novel notebook. | Project data |
| `Parent Paper.pdf` | Reference paper. | Reference |

## Reproducibility Status (Important)

As of April 15, 2026: this repo is **not fully run-ready on a fresh machine without environment setup**.

Fresh-machine checks showed:
- `python3 Construction_Injury_Severity.py` fails immediately if dependencies are not installed (`ModuleNotFoundError: pandas`).
- Even after pip installs, macOS commonly fails on XGBoost unless `libomp` is installed.
- `Authors_Results_Check.ipynb` imports XGBoost directly and will fail if XGBoost cannot load.

So the setup steps below must be followed exactly for TA reproducibility.

## Clean-Machine Setup (TA Runbook)

Run from repo root after clone:

```bash
git clone <your-repo-url>
cd Construction-Safety
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install pandas numpy scikit-learn xgboost catboost seaborn matplotlib jupyter openpyxl
```

### macOS only (required for XGBoost)

```bash
brew install libomp
```

### Quick environment sanity check

```bash
python - <<'PY'
import pandas, numpy, sklearn, matplotlib, seaborn, openpyxl
from xgboost import XGBClassifier
from catboost import CatBoostClassifier
print("Environment OK")
PY
```

If this command fails, do not continue to notebook execution yet.

## Execution Order

### 1) Replication check (author baseline)

```bash
jupyter notebook Authors_Results_Check.ipynb
```

In Jupyter: `Kernel -> Restart & Run All`.

Alternative CLI run (same baseline family set):

```bash
python Construction_Injury_Severity.py
```

### 2) Main project notebook (novel implementation)

```bash
jupyter notebook Construction_Injury_Novel_Implementation.ipynb
```

In Jupyter: `Kernel -> Restart & Run All` and execute cells in order.

Notes:
- The notebook is Colab-compatible but also runs locally.
- It searches for cleaned CSVs in the current repo root first (already included in this submission).
- Local artifacts are saved under `outputs/literal_author_style_cleaned/`.

## Expected Recorded Results

These are the recorded summary results currently embedded in the notebooks.

### Author results check (`Authors_Results_Check.ipynb`)

| Model | Accuracy | F1-score |
|---|---:|---:|
| MLP | 0.820915 | 0.806212 |
| Random Forest | 0.823249 | 0.797262 |
| XGBoost | 0.821008 | 0.792196 |
| Logistic Regression (L2) | 0.808590 | 0.784726 |
| Logistic Regression (L1) | 0.800280 | 0.774959 |
| SVM | 0.809991 | 0.771798 |

### Novel implementation test summary (`Construction_Injury_Novel_Implementation.ipynb`)

| Model | Accuracy | F1-score |
|---|---:|---:|
| CatBoost | 0.847618 | 0.816403 |
| MLP | 0.815268 | 0.794519 |
| Soft Voting Ensemble | 0.825821 | 0.791723 |
| XGBoost | 0.817043 | 0.774582 |
| Random Forest | 0.807279 | 0.767334 |

## Common Failure Modes

1. `ModuleNotFoundError` for pandas/sklearn/etc.
- Cause: dependencies not installed in active environment.
- Fix: activate `.venv` and rerun the pip install block.

2. `XGBoostError ... libomp.dylib could not be loaded` (macOS)
- Cause: OpenMP runtime missing.
- Fix: `brew install libomp` and rerun.

3. Notebook runs but results differ significantly
- Cause: skipped cells, wrong kernel, or package/version differences.
- Fix: restart kernel, run all cells in order, confirm imports in the same `.venv`.

## Submission Notes

- `Construction_Injury_Severity.py`, `Injury Severity.xlsx`, and `Authors_Results_Check.ipynb` are the author replication references.
- The main project contribution for grading is `Construction_Injury_Novel_Implementation.ipynb` and the cleaned split data files.
