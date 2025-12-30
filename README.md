# ⚡ Hourly Energy Consumption Forecasting — Intermediate Time Series Project

Forecasting hourly electricity demand for the **PJM East (PJME) region** using machine learning. Unlike basic time-series models that rely only on historical trends, this project integrates **meteorological variables** and **cyclical temporal features** to better capture the real-world drivers of grid load.

---

## 🎯 Project Overview

This project predicts **hourly regional energy consumption** using:

- Historical PJME load data  
- Weather variables (Temperature & Humidity)  
- Lag features + rolling statistics  
- Cyclical date-time encodings  
- Walk-forward time series validation

### ✅ Key Results

| Metric | Value |
|------|------|
| **Final Model Accuracy** | **95.97%** |
| **MAPE** | **4.03%** |
| **Improvement vs Baseline** | **55.6% reduction in error** |

---

## 🛠️ Tech Stack

- **Language:** Python 3.x  
- **Libraries:** Pandas, NumPy, XGBoost, Scikit-Learn, Meteostat, Matplotlib  
- **Validation:** Walk-Forward (TimeSeriesSplit)

---

## 🧬 Feature Engineering — *“The Secret Sauce”*

To go beyond beginner-level forecasting, several advanced features were engineered:

- **Cyclical Encoding**  
  Converts hour & month into sine/cosine to preserve time continuity  
  (e.g., hour 23 ≈ hour 0)

- **Lag Features**  
  24-hour & 7-day lags capture short-term consumption memory

- **Exogenous Weather Inputs**  
  Temperature & humidity merged via **Meteostat API (Philadelphia region)**

- **Rolling Window Statistics**  
  24-hour temperature averages capture *thermal inertia effects*

---

## 📊 Evaluation & Validation

Standard K-Fold is **not appropriate** for time-series — instead:

- **Validation Strategy:** Walk-Forward (Expanding Window)
- **Baseline:** 24-hour Persistence (`t = t-24`)
- **Metric:** Mean Absolute Percentage Error (MAPE)

### 📌 Performance Comparison

| Model | MAPE | Improvement |
|------|------|------------|
| Naive Persistence | 9.09% | — |
| **XGBoost (Final)** | **4.03%** | **55.60% ↓** |

---

## 📈 Visualizations

The model accurately tracks:

- Daily demand peaks & valleys  
- Weather-driven volatility periods  

*(You may add exported plots inside a `plots/` folder and reference them here.)*

---

## 🚀 How to Reproduce

```bash
# Clone repository
git clone https://github.com/sawvikk/Energy-Forecasting-Project.git
cd pjme-energy-forecasting

# Install dependencies
pip install -r requirements.txt
```

### 📂 Dataset

Download **PJME_hourly.csv** from Kaggle and place it in:

```
data/archive/
```

### ▶️ Run the Notebook

Open and execute:

```
notebooks/PJME_Energy_Forecasting_Analysis.ipynb
```

---

## 🔮 Future Improvements

- [ ] Integrate **U.S. public holiday effects**
- [ ] Implement **probabilistic forecasting (quantile regression)**
- [ ] Add **prediction confidence bands** for operators
- [ ] Explore **Deep Learning models**:
  - N-BEATS  
  - Temporal Fusion Transformer (TFT)

---

## 📌 Project Status

This project demonstrates an **intermediate-level ML workflow** for practical grid-load forecasting with strong real-world relevance.

Feel free to star ⭐ the repo or submit improvements!

