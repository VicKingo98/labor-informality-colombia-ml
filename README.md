# Predicting Labor Informality in Colombia — Machine Learning Project

Supervised ML model to predict labor informality in Colombia using GEIH 2023 microdata. Random Forest classifier with AUC ≈ 0.86.

---

## Overview

This project applies supervised machine learning techniques to predict the probability of labor informality among employed workers in Colombia, using microdata from the Gran Encuesta Integrada de Hogares (GEIH) 2023, published by DANE.

The goal is to identify workers most likely to be informal based on observable employment characteristics, contributing to a better understanding of informality patterns in the Colombian labor market.

---

## Problem Definition

- **Type:** Binary supervised classification
- **Target variable:** `informal` (1 = informal worker, 0 = formal worker)
- **Key features:** Company size, hours worked, and workplace location
- **Justification:** Relationships between these variables and informality are potentially non-linear, motivating the evaluation of models with varying levels of flexibility.

---

## Dataset

**Source:** Gran Encuesta Integrada de Hogares (GEIH) 2023 — DANE  
**Download:** [DANE official microdata portal](https://microdatos.dane.gov.co/index.php/catalog/ENChogares)

The dataset consists of monthly files covering the full year 2023. Due to file size, the raw data is not included in this repository. Download the monthly CSV files from the link above and place them in the `data/raw/` folder before running the notebook.

---

## Methodology

### 1. Data Preparation
- Integration of 12 monthly GEIH files into a single unified dataset
- Missing value imputation using median strategy via `SimpleImputer` (mainly affecting company size variable `P1800S1`)

### 2. Models Evaluated
Four supervised learning models were trained and compared:

| Model | AUC |
|---|---|
| Random Forest | 0.86 |
| Gradient Boosting | 0.86 |
| Support Vector Machine | 0.83 |
| Logistic Regression | 0.83 |

Tree-based models outperformed linear approaches, suggesting non-linear relationships between the features and the target variable.

### 3. Hyperparameter Tuning
- Cross-validation on a random subsample to reduce computational cost
- Grid search for optimal hyperparameters on Random Forest and Gradient Boosting

### 4. Model Selection
Random Forest was selected as the final model based on:
- Best AUC after calibration: **0.8598**
- Easier interpretability through feature importance analysis

---

## Results

### Model Performance
- **AUC:** 0.86
- **Correct classifications:** 28,493 formal workers and 22,632 informal workers identified correctly

### Feature Importance
The three most predictive variables were:
1. **Workplace location** (`P6880`) — highest importance
2. **Hours worked** (`P6800`)
3. **Company size** (`P1800S1`)

These results suggest that job characteristics and the context in which productive activity takes place are key determinants of informality probability.

---

## Key Findings

- Employment characteristics contain meaningful signal for approximating labor informality
- Informality is strongly linked to working conditions and workplace context
- The model achieves good discrimination between formal and informal workers, with an AUC of ~0.86

---

## Limitations & Future Work

- Informality was defined through an operational approximation
- Company size appears both in the informality definition and as a predictor variable
- The model was built with a limited set of features
- Future improvements: incorporate additional GEIH variables and extend the analysis to multiple years

---

## Project Structure

```
📁 labor-informality-colombia-ml/
│
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md        ← Download instructions for GEIH dataset
└── Proyecto_ML_G14.ipynb
```

---

## Requirements

```
pandas
numpy
scikit-learn
matplotlib
seaborn
jupyter
```

Install all dependencies with:
```bash
pip install -r requirements.txt
```

---

## Authors

Developed as part of the Introduction to Machine Learning course —  
Master's in Data Analytics, Universidad de los Andes (2025).

- Javier Cañarte
- Julián Botero
- Sebastian Palomino
- Victor Osorio
