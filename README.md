# RF-SHAP-Framework
This repository contains the Google Colab notebook and dataset for the HepatoXAI-RF framework for Hepatitis B diagnosis. It includes preprocessing, SMOTE balancing, SHAP-based feature selection, Random Forest modeling, calibration, robustness analysis, and explainable AI for reproducible clinical research.

# HepatoXAI-RF: Hepatitis B Prediction Framework

This repository contains the Google Colab notebook and dataset for the HepatoXAI-RF framework, an interpretable machine learning pipeline for Hepatitis B diagnosis using a real-world clinical dataset. The project focuses on building a reliable and explainable diagnostic framework by combining careful preprocessing, feature selection, Random Forest modeling, calibration analysis, robustness evaluation, and SHAP-based explainability.

## Repository Contents

- `RF_SHAP_Framework.ipynb` — Main Google Colab notebook containing the full implementation
- `HBV_Dataset.xlsx` — Clinical dataset used for model development and evaluation

## Project Overview

The notebook presents a complete end-to-end workflow for Hepatitis B prediction. It includes:

- Dataset loading and inspection
- Missing value handling
- HBV DNA value parsing and cleaning
- Categorical encoding
- Box-Cox transformation for skewed numerical variables
- Standardization of numerical features
- Train-validation-test splitting
- SMOTE-based class balancing
- SHAP-based feature ranking
- Top-k feature selection
- Random Forest hyperparameter tuning
- Threshold optimization
- Final model training and evaluation
- Confusion matrix generation
- Calibration curve analysis
- Multi-seed robustness testing
- SHAP global and local explainability
- Baseline model comparison

## Dataset Information

The dataset is an Excel file containing 216 clinical records with demographic, symptomatic, and biochemical features relevant to Hepatitis B prediction.

### Main Features
- Age
- Gender
- Jaundice
- DarkUrine
- AbdominalPain
- VomitingFrequency
- LossofAppetite
- HBVDNA
- ALTLevel
- ASTLevel
- Bilirubin
- Albumin
- Status

### Target Variable
- `Status`  
  - `Positive`
  - `Negative`

## Methodology

The implemented framework follows these major stages:

1. **Data Inspection and Cleaning**  
   The dataset is loaded, missing values are identified, and inconsistent entries such as HBV DNA textual values are cleaned.

2. **Preprocessing**  
   Numerical features are transformed and standardized, while categorical variables are encoded into model-ready form.

3. **Imbalance Handling**  
   SMOTE is applied on the training data to address class imbalance.

4. **Feature Selection**  
   SHAP values from a preliminary Random Forest model are used to rank features and select the most informative subset.

5. **Model Development**  
   A Random Forest classifier is tuned using randomized hyperparameter search.

6. **Threshold Optimization**  
   The classification threshold is optimized on the validation set rather than relying only on the default 0.5 cutoff.

7. **Final Evaluation**  
   The selected model is retrained on the full training data and evaluated on the untouched test set.

8. **Explainability and Reliability**  
   The notebook includes confusion matrix analysis, calibration curves, SHAP explainability, and multi-seed robustness testing.

## Requirements

The notebook is designed for Google Colab and uses Python libraries such as:

- numpy
- pandas
- matplotlib
- seaborn
- scipy
- scikit-learn
- imbalanced-learn
- shap
- openpyxl

Install the required packages in Colab using:

```python
!pip install shap imbalanced-learn openpyxl
