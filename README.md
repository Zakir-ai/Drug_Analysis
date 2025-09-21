# Drugs Analysis & Rating Prediction

## Technologies & Official Links
🐍 **Python (3.9+)** → [Download Python](https://www.python.org/downloads/)  
📓 **Jupyter Notebook** → [Install Jupyter](https://jupyter.org/install)  
📘 **scikit-learn** → [scikit-learn Documentation](https://scikit-learn.org/stable/)  
💻 **Flask** → [Flask Documentation](https://flask.palletsprojects.com/)  
🔍 **Libraries:** pandas, numpy, joblib, matplotlib, seaborn (optional), nltk (optional)

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
End-to-end data science and machine learning pipeline to **predict drug ratings** and classify them into **Low / Medium / High** categories.  
Includes:
- Data cleaning and feature engineering  
- Exploratory analysis of side-effects and conditions  
- Regression & classification models  
- A Flask web application for real-time prediction.

---

## Dataset
**File:** `drugs_side_effects_drugs_com.csv`  
Key Columns:
- `generic_name`, `medical_condition`, `drug_classes`, `rx_otc`, `pregnancy_category`, `csa`
- `side_effects` (free text)
- `activity`, `alcohol`, `no_of_reviews` (numeric)

Missing values are handled safely in preprocessing.

---

## Objectives
- Clean and normalize drug and side-effect data.
- Engineer predictive features from text and numeric fields.
- Train a regression model to predict average ratings (0–10).
- Classify predicted ratings into **Low / Medium / High**.
- Provide a Flask web interface for interactive predictions.

---

## Approach & Methods
- **Preprocessing:** Handle missing values, feature engineering (length of side-effects text, keyword flags such as `has_hives`, `has_rash`, etc.), label encoding for categorical features.
- **Modeling:**  
  - Regression to predict numeric rating.  
  - Classification into rating classes (High ≥ 7, Medium ≥ 4, Low < 4).
- **Deployment:** Flask app loads trained `.joblib` models and encoders to serve predictions.

---

## Results
- Regression model shows strong correlation with actual ratings.
- Classification achieves robust accuracy across Low/Medium/High categories.
- Feature importance highlights number of reviews and side-effect indicators as key predictors.

---

## Repository Structure
```
.
├─ Drugs_Analysis.ipynb         # EDA, feature engineering, model training
├─ drugs_side_effects_drugs_com.csv
├─ app.py                       # Flask application
├─ artifacts/                   # Saved models and encoders
│   ├─ model_regression.joblib
│   ├─ model_classification.joblib
│   └─ label_encoders.json
├─ templates/
│   ├─ index.html               # Input form UI
│   └─ result.html              # Prediction result UI
└─ README.md                    # This file
```

---

## Setup & Usage

### Clone the Repository
```bash
git clone https://github.com/your-username/Drugs-Analysis.git
cd Drugs-Analysis
```

### Create and Activate Environment
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
```

### Install Requirements
```bash
pip install -r requirements.txt
```
*(See inline requirements below if you prefer not to use a file.)*

### Run Jupyter Notebook
```bash
jupyter notebook Drugs_Analysis.ipynb
```
Walks through EDA, feature engineering, model training, and artifact generation.

### Launch the Flask App
Ensure the `artifacts/` folder contains trained models, then:
```bash
python app.py
```
Open your browser to **http://127.0.0.1:5000/** to interact with the prediction interface.

---

## Requirements (inline)
If you prefer not to maintain a separate requirements.txt, minimal dependencies are:
```
flask
pandas
numpy
scikit-learn
joblib
```
Optional (for extended EDA/plots):
```
matplotlib
seaborn
nltk
```

---

## Reproducibility Notes
- `random_state=42` used wherever applicable (train/test splits, model training).
- Save model artifacts (`.joblib`) to `artifacts/` for consistent predictions.
- Use identical library versions for exact replication of results.

---

## Visualizations
Typical outputs from the notebook:
- Rating distribution histograms
- Feature correlation heatmaps
- Bar plots of top side-effect keywords
- Scatter plots of predicted vs actual ratings

---

## Limitations
- Keyword-based feature engineering may miss nuanced text patterns.
- Dataset may contain bias (user-submitted reviews).
- Model performance is limited by dataset quality and size.

---

## Future Work
- Integrate deep learning NLP (transformers) for richer text semantics.
- Hyperparameter tuning and ensemble methods for improved accuracy.
- Add authentication and database logging to the Flask app.
- Deploy on cloud platforms (Heroku, AWS, GCP) for public access.

---

## Acknowledgements
Open-source libraries: pandas, scikit-learn, Flask, joblib, matplotlib, seaborn.  
Dataset inspired by public drug review and side-effect data.

---
