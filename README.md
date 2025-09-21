# Drugs Analysis & Rating Prediction

## Technologies & Official Links
🐍 **Python (3.9+)** → [Download Python](https://www.python.org/downloads/)  
📓 **Jupyter Notebook** → [Install Jupyter](https://jupyter.org/install)  
📘 **scikit-learn** → [scikit-learn Documentation](https://scikit-learn.org/stable/)  
💻 **Flask** → [Flask Documentation](https://flask.palletsprojects.com/)  
🔍 **NLP / Text Processing Libraries**  
- pandas  
- numpy  
- joblib  
- NLTK (optional if you extend text processing)

---

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Objectives](#objectives)
- [Approach & Methods](#approach--methods)
- [Results](#results)
- [Repository Structure](#repository-structure)
- [Setup & Usage](#setup--usage)
- [Requirements (inline)](#requirements-inline)
- [Reproducibility Notes](#reproducibility-notes)
- [Visualizations](#visualizations)
- [Limitations](#limitations)
- [Future Work](#future-work)
- [Acknowledgements](#acknowledgements)
- [License](#license)
- [Contact](#contact)

---

## Overview
This project performs end-to-end data science and machine learning to **predict drug ratings** and classify them as **Low / Medium / High** based on a combination of categorical, numerical, and text-derived features.  
It includes:
- Data cleaning and feature engineering  
- Exploratory analysis of side-effects and medical conditions  
- Training of **regression** and **classification** models  
- A **Flask web application** for real-time prediction

Deliverables include a reproducible Jupyter workflow and a ready-to-run web app.

---

## Dataset
**File:** `drugs_side_effects_drugs_com.csv`  
**Rows × Columns:** ~ (as provided)  
Key Columns:
- `generic_name` (drug generic name)
- `medical_condition`
- `drug_classes`
- `rx_otc` (prescription/over-the-counter)
- `pregnancy_category`
- `csa` (controlled substance category)
- `side_effects` (free-text description)
- `activity`, `alcohol`, `no_of_reviews` (numeric attributes)

Missing values are handled safely in preprocessing.

Intended use: Build models to estimate the average rating and risk classification of drugs based on available metadata and reported side effects.

---

## Objectives
- Clean and normalize drug and side-effect data for analysis.
- Engineer predictive features from text length and keyword patterns.
- Train a regression model to predict numeric ratings (0–10 scale).
- Derive a classification of **Low / Medium / High** rating categories.
- Provide a Flask web interface for interactive predictions.

---

## Approach & Methods
### Preprocessing
- Handle missing values and type conversions.
- Feature engineering:
  - Length of side_effects text (`side_effects_len`).
  - Length of medical_condition description (`mc_desc_len`).
  - Boolean flags for key symptoms (e.g., `has_hives`, `has_rash`, `has_dizziness`).
- Label Encoding for categorical features.

### Modeling
- **Regression:** Predict average user rating using scikit-learn regression model.
- **Classification:** Map predicted rating to classes:
  - `High` ≥ 7
  - `Medium` ≥ 4 and < 7
  - `Low` < 4

### Deployment
- Flask app (`app.py`) loads trained models (`model_regression.joblib`, `model_classification.joblib`) and encoders (`label_encoders.json`).
- User inputs through web form → Preprocessing → Prediction → Result page.

---

## Results
- Regression model achieves strong correlation with actual ratings (see notebook for metrics).
- Classification accuracy shows robust performance across Low/Medium/High categories.
- Feature importance highlights number of reviews and side-effect indicators as top predictors.

---

## Repository Structure
