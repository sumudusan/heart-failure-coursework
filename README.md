# Heart Failure Mortality Prediction – Phase 2

## Project Overview

This project implements and evaluates baseline Random Forest models to predict mortality among patients with heart failure using the Heart Failure Clinical Records dataset. It builds on the research by Chicco and Jurman (2020), which investigated whether serum creatinine and ejection fraction could predict patient survival.

The main objective is to compare a model using 11 clinical features with a reduced model using only serum creatinine and ejection fraction.

## Dataset

The Heart Failure Clinical Records dataset was obtained from the UCI Machine Learning Repository.

- **Number of records:** 299
- **Original number of columns:** 13
- **Target variable:** `DEATH_EVENT`
- **Target classes:** 0 = survived, 1 = died
- **Features used:** 11 clinical predictors for Model A and 2 predictors for Model B

The `time` feature was excluded from the input features.

Dataset source: https://doi.org/10.24432/C5Z89R

## Models Implemented

Two Random Forest classifiers were developed:

- **Model A:** Uses all 11 clinical predictors, excluding `time`.
- **Model B:** Uses only `serum_creatinine` and `ejection_fraction`.

Both models use 200 trees, a fixed random seed of 42, and balanced class weights.

## Methodology

The implementation includes:

1. Loading and validating the dataset.
2. Checking for missing values and duplicate records.
3. Excluding the `time` feature from the predictors.
4. Splitting the data into training and testing sets using an 80:20 stratified split.
5. Training both Random Forest models.
6. Evaluating model performance using multiple metrics.
7. Generating confusion matrices, ROC curves and Precision–Recall curves.
8. Comparing baseline results with the published findings.

## Evaluation Metrics

The models were evaluated using:

- Accuracy
- Sensitivity (Recall)
- Specificity
- Precision
- F1-score
- Matthews correlation coefficient (MCC)
- ROC-AUC
- Average Precision (AP)

## Baseline Results

| Metric | Model A: 11 Features | Model B: 2 Features |
|---|---:|---:|
| Accuracy | 0.700 | 0.717 |
| Sensitivity | 0.316 | 0.421 |
| Specificity | 0.878 | 0.854 |
| Precision | 0.545 | 0.571 |
| F1-score | 0.400 | 0.485 |
| MCC | 0.233 | 0.302 |
| ROC-AUC | 0.800 | 0.731 |
| Average Precision | 0.581 | 0.650 |

The two-feature model achieved better results for accuracy, sensitivity, precision, F1-score, MCC and Average Precision. However, the 11-feature model achieved higher specificity and ROC-AUC.

These results are based on one train/test split and should not be treated as evidence that either model will perform better in every evaluation.

## Project Files

The repository contains the Python implementation, saved evaluation results, visualisations and supporting documentation.

- `PHASE_2.ipynb` or the relevant Python script
- `results/` — saved plots and evaluation outputs
- `baseline_model_comparison.csv`
- `paper_vs_baseline_comparison.csv`
- `README.md`

*The filenames above should be checked against the actual files in the repository before submission.*

## Limitations

The dataset contains only 299 records, and the models were evaluated using a single test split. Both models also missed some patients who died. Further evaluation using repeated stratified cross-validation and additional patient data would be needed to assess the consistency and reliability of the results.

These models are developed for academic purposes and are not intended for clinical decision-making.

## Original Research

Chicco, D. and Jurman, G. (2020) ‘Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone’, *BMC Medical Informatics and Decision Making*, 20, article 16. https://doi.org/10.1186/s12911-020-1023-5

## Author

Developed as part of a university machine learning coursework project.