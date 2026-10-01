# Reproducing and Extending a Stacking Ensemble for Heart Disease Prediction

HD Task – Machine Learning Mini Research
Author: Khac Truong Kiet (TK) Tran
Student ID: 224874982
Date 28/9/2026

This repository reproduces the stacking ensemble of Bhagat et al. (2025),
"An efficient stacking-based ensemble technique for early heart attack prediction",
*Multimedia Tools and Applications*, 84, 36351–36375 (doi: 10.1007/s11042-024-19293-7),
and evaluates a leakage-free, duplicate-aware stacking pipeline.

## Contents

| File | Description |
|---|---|
| `307_HD_Task.ipynb` | All code: data verification, Part 1 reproduction, Part 2 proposed method, figures |
| `heart.csv` | Kaggle Heart Disease Dataset (johnsmith88), as used in the paper |
| `requirements.txt` | Python package versions used |
| `fig_*.png` | Figures used in the report |

## Dataset

Source: https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset

1025 records, 13 clinical features and a binary target (1 = disease, 0 = no disease).
The file is included in this repository, so no download is needed.

## How to run

1. Install Python 3.11 or later.
2. Install the packages:
   ```
   pip install -r requirements.txt
   ```
3. Start Jupyter from this folder:
   ```
   jupyter lab
   ```
4. Open `307_HD_Task.ipynb` and select **Kernel → Restart Kernel and Run All Cells**.

The notebook runs in a few minutes on a standard laptop. No GPU is needed.
The figures are saved as `fig_*.png` in the same folder.

## Reproducibility

All random processes use fixed seeds: `SEED = 42` for the main split, models,
imputer and cross-validation, and split seeds 0–29 for the multi-split experiment.
Re-running the notebook with the package versions in `requirements.txt`
reproduces the results in the report.

## Notebook structure

- **Setup:** imports and seed
- **Part 1 – Data verification:** shape, missing values, duplicates, invalid codes
- **Part 1 – Reproduction of Table 11:** six classifiers and stacking on an 80/20 split (paper setup)
- **Part 1 – Variation across 30 random splits:** mean ± std compared with the paper
- **Part 1 – Figures and seen/unseen analysis:** confusion matrices, ROC curves, feature importance, accuracy on seen vs unseen test records
- **Part 2 – Proposed pipeline:** deduplication, in-fold imputation and encoding, regularised stacking, repeated stratified CV, Wilcoxon and corrected t-tests
- **Part 2 – Stepwise ablation:** adds each model change to the paper's stacking one at a time, with corrected t-tests between steps (Table 8)
- **Part 2 – Figures:** fold-level boxplots and headline accuracy comparison
- **Environment:** package versions
