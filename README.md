# DS340W Final Project Submission: Construction Injury Severity

This is our DS340W final project submission, where we replicate the parent injury-severity pipeline and present novel cleaned-data model improvements.

## TA Code Running Instructions

1. Clone repo and open:
- `Construction_Injury_Novel_Implementation.ipynb`

2. In Google Colab, run:
- `Kernel -> Restart & Run All`

3. The first cell in the notebook installs required Python packages automatically.
4. Continue running all cells top-to-bottom to train models and generate result tables.

### If you are on macOS

If XGBoost fails with a `libomp.dylib` error, run once in terminal:

```bash
brew install libomp
```

Then restart kernel and run all cells again.

## Model Training and Artifact Saving

- The notebook trains models from scratch by running the novel notebook.
- If run in Google Colab with Drive mounted, artifacts/checkpoints are saved to the runner's Google Drive path.
- If run locally (non-Colab), artifacts/checkpoints are saved under `outputs/literal_author_style_cleaned/` in this repo.

## What To Expect From The Novel Notebook

The notebook runs our cleaned-data workflow and model comparison, including:
- Author-style model families on cleaned splits
- Novel model: **CatBoost**
- Novel model: **Soft Voting Ensemble**


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
