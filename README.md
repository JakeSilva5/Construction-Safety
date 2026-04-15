# Construction Safety Novel Implementations
This is our DS340W Final Project repository. We remodel the injury severity predictions for Construction and also add 2 novel implementations.
This repository contains our parent paper, the **Construction Safety Dataset** and the codebase accompanying a paper accepted to the **CIKM 2025 Resource Track**. This work introduces a large-scale, multi-level, multi-modal dataset for construction safety research, and provides strong experimental benchmarks for both **predictive** and **causal** modeling tasks.

---

## 🏗️ Dataset Overview

Our dataset integrates three critical levels of construction safety data, collected from OSHA's official records:
...


The dataset combines:

- **Tabular features**: weather conditions, job titles, inspection type, time/location
- **Textual features**: incident abstracts, violation descriptions

---

## 🔬 Experiments

We evaluate the dataset on two key tasks to demonstrate its benchmarking potential:

### Injury Severity Prediction
We noticed that the authors' data had duplicate rows, we got rid of those and retrained thier baselines first.
**Objective**: Predict the severity (1 to 4) of an injury using structured and unstructured features.

#### Models Evaluated:

- Traditional ML: Logistic Regression (L1/L2), SVM, Random Forest, XGBoost, MLP

#### Results:
*plug in our results* vs authors results*
| Model            | Accuracy | Macro-F1 |
|------------------|----------|----------|
| Random Forest    | 0.8239   | 0.8132   |
| MLP              | 0.8220   | 0.8114   |
| XGBoost          | 0.8190   | 0.8089   |

LLMs outperformed traditional models due to their ability to leverage narrative context and model cross-level relationships between violations, inspections, and incidents.

---

This experiment showcases the dataset's ability to support **causal modeling**, **temporal inference**, and **policy evaluation** through rich cross-level linkages.
