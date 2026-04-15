# DS340W Final Project Submission: Construction Injury Severity

This submission is organized so the grader can run our **novel implementation** directly from a fresh clone.

## TA Quick Start (Primary Grading Path)

1. Clone repo and open:
- `Construction_Injury_Novel_Implementation.ipynb`

2. In Jupyter, run:
- `Kernel -> Restart & Run All`

3. The first cell in the notebook installs required Python packages automatically.

### If you are on macOS

If XGBoost fails with a `libomp.dylib` error, run once in terminal:

```bash
brew install libomp
```

Then restart kernel and run all cells again.

## What To Expect From The Novel Notebook

The notebook runs our cleaned-data workflow and model comparison, including:
- Author-style model families on cleaned splits
- Novel model: **CatBoost**
- Novel model: **Soft Voting Ensemble**

Recorded test summary values in the notebook include:

| Model | Accuracy | F1-score |
|---|---:|---:|
| CatBoost | 0.847618 | 0.816403 |
| MLP | 0.815268 | 0.794519 |
| Soft Voting Ensemble | 0.825821 | 0.791723 |
| XGBoost | 0.817043 | 0.774582 |
| Random Forest | 0.807279 | 0.767334 |

## Included Data Files Used By Novel Notebook

- `construction_training_set_cleaned.csv`
- `construction_validation_set_cleaned.csv`
- `construction_test_set_cleaned.csv`
- `Injury Severity_cleaned.xlsx`

## Optional Replication Note (Not Required For TA Grading Path)

If someone wants to inspect the original-author replication artifacts:

- `Construction_Injury_Severity.py` (author-style baseline script)
- `Injury Severity.xlsx` (author data file)
- `Authors_Results_Check.ipynb` (replication check notebook)

These are included for transparency/reference, but the primary grading workflow is the novel notebook above.
