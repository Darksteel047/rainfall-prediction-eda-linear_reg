## 🌧️ Rainfall Prediction EDA — Guwahati Daily Weather (1973 – 2025)

This project performs an in-depth Exploratory Data Analysis (EDA) on long-term daily weather data for Guwahati, Assam (India), spanning January 1973 – February 2025.
The goal is to explore climatic patterns, visualize correlations, and identify the key features that influence rainfall prediction in the region.

---

## 🗺️ Project Overview

- Dataset compiled from multiple annual weather CSV files (1973 – 2025)
- Contains 19,000 + daily entries with 30 + weather attributes
- Region: Guwahati (26.14° N, 91.74° E), Northeast India
- Focus: Relationship between temperature, humidity, pressure, cloud cover & rainfall
- Output: Insights, correlations, and features for future ML rainfall prediction models

---

## 📦 Dataset

📍 Source: Guwahati Daily Weather Data (1972–2025) — Kaggle

🗂️ Type: Raw merged CSV (unprocessed)
🕒 Coverage: 1973-01-01 → 2025-02-01
📍 Location: Guwahati, Assam (India)

A cleaned subset of this dataset was used for the analysis in this notebook.
Missing values were handled via linear interpolation, and non-relevant metadata columns were dropped.

---

## 🧹 Data Preparation

- Merge yearly CSVs → single continuous dataset
- Convert datetime to proper date format; extract year, month, day
- Interpolate missing values in temperature, humidity, and pressure
- Drop redundant metadata columns
- Explore variable distributions and relationships through visualization

---

## 📈 Exploratory Analysis

Variable	Relationship with Rainfall	Type
- tempmax	Nonlinear – moderate temps (25–30 °C) favor rainfall	Nonlinear
- tempmin	Positive – warmer nights → more rain	Linear
- dew	Strong positive – high dew = high moisture = rain	Linear
- humidity	Positive – higher humidity → more rainfall	Linear
- sealevelpressure	Negative – low pressure → rainfall likely	Linear
- windspeed	Negative – calm air → rain	Inverse
- cloudcover	Strong positive – more clouds → more rain	Linear

---

## 🧠 Key Insights

- Rainfall strongly depends on humidity, dew point, and cloud cover
- Low-pressure systems coincide with most rainfall events
- Temperature–rainfall relationship is nonlinear (moderate temps = highest rain)

Identified 5 core predictive features:

['dew', 'humidity', 'cloudcover', 'sealevelpressure', 'tempmin']

---

## 📊 Visualizations

- Below are sample outputs from the EDA:
  
<p align="center">
  <img src="images/rainfall_distribution.png" alt="Ratings Distribution" width="500">
  </p>
<p align="center">
  <img src="images/Monthly rainfall variation.png" alt="Ratings Distribution" width="500">
  </p>
<p align="center">
  <img src="images/output.png" alt="Ratings Distribution" width="500">
  </p>
<p align="center">
  <img src="images/heatmap.png" alt="Ratings Distribution" width="500">
  </p>

---

## 🌧️ Phase 2: Rainfall Prediction using Linear Regression

After performing EDA, a baseline Linear Regression model was developed to predict daily rainfall (precip) using key weather variables:

['tempmin', 'humidity', 'sealevelpressure', 'cloudcover']

## ⚙️ Model Pipeline

- Selected 4 meteorologically significant features
- Log-transformed target (log1p(precip)) to reduce skew
- Scaled features using StandardScaler
- Trained and evaluated Linear Regression on an 80–20 split

## 📈 Model Performance

Metric|	Value
|---|---|
R² Score|	0.03
MAE|	4.73 mm
RMSE|	15.03 mm

## 💡 Insights

- Linear regression captures weak linear trends but struggles with rainfall’s nonlinear patterns.
- High humidity and cloud cover correlate positively with rainfall, while pressure correlates negatively — consistent with EDA findings.
- This serves as a baseline model for comparison with more complex algorithms (Random Forest, XGBoost, etc.).

---

## 🧩 Future scopes

- Build classification model → predict Rain / No Rain using logistic regression and random forest
- Add time-series features → month, rolling mean, lag precipitation
- Deploy interactive dashboards or Streamlit app for rainfall visualization

---

## 🛠️ Tech Stack

|Category|Tools|
|---|---|
Language|	Python 3
Libraries|	pandas, numpy, matplotlib, seaborn
Environment|	Jupyter Notebook / VS Code
Version Control|	Git & GitHub
Dataset Hosting|	Kaggle Datasets

---

## 🪪 License

MIT License — you’re free to use and adapt this project with proper credit.
