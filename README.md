# Heart Disease Prediction with Bayesian Networks

**Comparing expert-specified and data-learned probabilistic graphical models for heart-disease risk assessment.**

## Overview

This project uses the **Cleveland heart disease dataset** to compare two Bayesian networks: one with a clinically motivated structure and one learned from training data. The aim is to understand how the choice of network structure affects prediction, probabilistic inference and interpretability.

This is an academic modelling exercise, **not a clinical diagnostic tool**.

## Methods

- Clean and examine **303 patient records**; encode the heart-disease outcome as a binary target.
- Use a stratified split of **242 training** and **61 test** patients.
- Fit an **expert-designed directed acyclic graph (DAG)** and a learned DAG using **hill climbing with the Bayesian Information Criterion (BIC)**.
- Estimate conditional probability tables, carry out forward and reverse inference, and examine the target's Markov blanket.
- Compare held-out accuracy, precision, recall, specificity, F1, ROC-AUC and uncertainty in the AUC difference.

## Key findings

- The expert network achieved **ROC-AUC 0.939**, compared with **0.918** for the learned network.
- The learned network achieved **86.9% accuracy**, compared with **85.2%** for the expert network, at a threshold of 0.50.
- A paired bootstrap interval for their ROC-AUC difference included zero: **neither model was shown to be conclusively superior**.
- Chest-pain type, thalassemia test results and affected-vessel count were influential, but learned edge directions should **not** be interpreted as causal relationships.

## Repository contents

- `Bayesian_Networks_Notebooks.ipynb` — complete data preparation, model training, inference and testing.
- `EDAB6808_Assignment 3 Report_Nhlapo L_Letwaba B.pdf` — technical report.
- `Lwazi_Nhlapo & Boipelo_Letwaba_Assignment 3.pptx` — presentation.
- `Model pkl files/` — fitted networks and preprocessing objects.

## Running the project

1. Obtain the authorised version of the Cleveland heart disease dataset. **The input dataset is not included in the uploaded ZIP.**
2. Install the primary dependencies:
   ```bash
   pip install pandas numpy matplotlib scikit-learn networkx bnlearn pgmpy jupyter
   ```
3. The notebook expects the source in a file named `diabetes.csv` (despite analysing **heart disease**). Place it at `Data/diabetes.csv` or change `DATA_PATH` in the notebook.
4. Execute the notebook in order. The original notebook records exact versions for the Bayesian-network packages; use those if reproducibility is affected by API changes.

**Security:** Python `.pkl` files must be loaded only from trusted sources. Do not unpickle unknown files.

## Limitations

The sample is small, and single-dataset test performance is not evidence of clinical generalisability. Some graph directions found by the structure-learning algorithm are not medically plausible. External validation would be needed before any practical deployment.

## Contributors

**Lwazi Nhlapo** and **Boipelo Letwaba** — collaborative academic project.
