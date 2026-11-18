# HepatoXAI-RF: Explainable Hepatitis B Detection Framework

This repository contains the analysis notebook and supporting dataset for **HepatoXAI-RF**, an explainable Random Forest framework for Hepatitis B detection using clinical biomarkers and Shapley Additive Explanations (SHAP).

The revised workflow includes fold-wise preprocessing and SMOTE, SHAP-guided feature selection, comparable tuning of baseline classifiers, validation-based threshold selection, multi-seed evaluation, calibration assessment, and patient-level explanations.

## Repository Contents

- `HepatoXAI_RF_FINAL_Revised_Analysis.ipynb` — Final revised analysis used for the manuscript
- `RF_SHAP_Framework.ipynb` — Original analysis notebook retained for reference
- `HBV_Dataset.xlsx` — De-identified clinical dataset used in the study

> The final revised results reported in the manuscript were generated using `HepatoXAI_RF_FINAL_Revised_Analysis.ipynb`. The original notebook is retained only to document the development history.

## Dataset Information

The dataset contains 216 de-identified clinical records collected from hospital records. It includes demographic, symptomatic, and biochemical variables relevant to Hepatitis B screening.

### Recorded variables

- Age
- Gender
- Jaundice
- Dark Urine
- Abdominal Pain
- Vomiting Frequency
- Loss of Appetite
- HBV DNA
- ALT/SGPT
- AST/SGOT
- Bilirubin
- Albumin
- HBV diagnosis status

The target variable is the physician-recorded HBV diagnosis status:

- `Positive`
- `Negative`

No direct personal identifiers are included in the dataset.

## Revised Analysis Workflow

The final notebook implements the following stages:

1. Data loading and inspection
2. Missing-value handling
3. Parsing and validation of HBV DNA values
4. Encoding of categorical variables
5. Transformation of skewed numerical variables
6. Standardization of numerical variables
7. Outer stratified train–test partitioning
8. Development-training and validation partitioning
9. Fold-wise preprocessing and SMOTE during model tuning
10. SHAP-based feature ranking and top-k feature selection
11. Comparable hyperparameter tuning of the proposed and baseline models
12. Validation-based decision-threshold selection
13. Evaluation on the untouched outer test set
14. Multi-seed performance evaluation
15. Sensitivity analysis using:
    - the complete seven-feature model;
    - HBV DNA alone; and
    - the selected features excluding HBV DNA
16. Global and patient-level SHAP analysis
17. Confusion-matrix and calibration assessment

## Evaluated Models

The following classifiers are evaluated using comparable tuning procedures:

- HepatoXAI-RF
- Random Forest
- Logistic Regression
- Decision Tree
- Linear Support Vector Machine
- Gaussian Naive Bayes
- K-Nearest Neighbors
- Gradient Boosting

The revised analysis emphasizes clinically relevant measures including sensitivity, specificity, ROC-AUC, and Brier score, in addition to accuracy, precision, and F1-score.

## Selected Features

The final seven-feature configuration contains:

- HBV DNA
- ALT level
- AST level
- Loss of Appetite
- Abdominal Pain
- Age
- Vomiting Frequency

## Running the Notebook

The notebook is designed for Google Colab.

1. Upload the notebook to Google Colab or open it from GitHub.
2. Upload or mount the dataset at the path specified in the data-loading cell.
3. Run the cells sequentially from the beginning.
4. Review the generated tables and figures in the output directory defined in the notebook.

Install the principal dependencies with:

```python
!pip install shap imbalanced-learn openpyxl
