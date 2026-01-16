# Forecasting of Meteorological Parameters Specific for Aviation  
### A Case Study of Nouasseur Airport

##  Overview
This project was conducted as part of my internship at the **Direction Générale de la Météorologie (DGM)** (Jul–Aug 2025).  
It focuses on **forecasting aviation-critical meteorological parameters** using data-driven and deep-learning approaches.  
The case study centers on **Nouasseur Airport (Morocco)**, with the goal of improving short- and medium-term weather predictions to support aviation safety.

##  Objectives
- Build a **reproducible forecasting pipeline** using **ERA5 hourly reanalysis data** (2016–2024).  
- Compare **classical statistical methods** with **deep learning architectures**.  
- Evaluate predictive performance for **temperature (T2M)** and **CAPE** on a held-out test year (2024).  
- Assess model robustness and operational potential for real-time applications.

##  Methods & Models
### Theoretical Exploration
Studied the mathematical foundations and predictive behavior of:
> ARIMA · SARIMAX · Holt’s Winter · Theta · k-NN · SVR · Random Forest · CNN · LSTM · Encoder–Decoder LSTM · Attention-based Encoder–Decoder

### Implemented Models
Only the most relevant models were implemented, tuned, and evaluated:
- **SARIMAX** — baseline statistical model (statsmodels)  
- **Univariate LSTM** — short-term temperature forecasting  
- **Encoder–Decoder LSTM** — 24-hour multi-step forecasting  
- **Attention-based Multivariate LSTM** — 24-hour CAPE forecasting  

All models were trained on **2020–2023** and tested on **2024** data.

##  Results Summary
| Model | Variable | Forecast Horizon | MAE | Key Insight |
|--------|-----------|------------------|-----|--------------|
| SARIMAX | T2M | 1-hour | ~6.3 °C | Baseline statistical performance |
| LSTM | T2M | 1-hour | **0.71 °C** | ~88.8% reduction in MAE vs SARIMA |
| Encoder–Decoder LSTM | T2M | 24-hour | ~2.42 °C | Maintains diurnal pattern |
| Attention LSTM | CAPE | 24-hour | 32.5 → 76.3 J/kg | Captures instability trends |

 **Deep learning models significantly outperformed statistical baselines**, particularly for short-term temperature forecasting.

##  Data
- **Source:** ERA5 Reanalysis (ECMWF)  
- **Coordinates:** Nouasseur Airport (33.37°N, −7.58°W)  
- **Variables:**  
  - 2-meter Temperature (`t2m`)  
  - Convective Available Potential Energy (`cape`)  
  - Total Column Water (`tcw`)  
  - Total Column Ozone (`tco3`)  
- **Temporal Resolution:** Hourly  
- **Period:** 2016–2024  

> Data can be downloaded via the [Copernicus Climate Data Store (CDS)](https://cds.climate.copernicus.eu/).

##  Technologies Used
- **Python**  
- **TensorFlow / Keras** — LSTM & attention models  
- **Statsmodels** — SARIMAX  
- **Pandas, NumPy, Matplotlib, Scikit-learn** — preprocessing and analysis  

 *If you find this repository useful, consider starring it — it helps others discover applied deep learning work in meteorology!*
