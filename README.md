#  Zero-Shot Time Series Forecasting using Chronos-2

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Model](https://img.shields.io/badge/Model-Chronos--2-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

##  Overview

This project demonstrates **zero-shot forecasting**, where a pre-trained time series foundation model (**Chronos-2**) is used to generate forecasts **without any training or parameter tuning** on the dataset.

Unlike traditional econometric or ML models, this approach directly leverages **learned representations of time series patterns**.


<img width="1902" height="744" alt="code" src="https://github.com/user-attachments/assets/10426387-19e0-4935-8bee-f6db93b00389" />


---

##  What is Zero-Shot Forecasting?

Zero-shot forecasting means:

> The model does **not learn from your dataset explicitly**, but instead uses prior knowledge gained during large-scale pretraining.

In this project:
- Input → historical inflation data  
- Output → future forecast (next 4 months)  
- No model fitting step involved  

---

##  About Chronos-2

Chronos-2 is a **Transformer-based time series foundation model** developed by Amazon.

- ~120M parameters  
- Encoder-only architecture  
- Supports:
  - Univariate forecasting  
  - Multivariate forecasting  
  - Covariate-aware predictions  

The model exposes a **Pandas-based API**, making it easy to integrate into data workflows.

---

##  How Chronos Works Internally

Unlike ARIMA or traditional econometric models, Chronos does **not model values directly**.

Instead, it:

1. **Normalizes** the time series  
2. **Discretizes** values into tokens  
3. Converts the series into a **sequence of tokens**  
4. Uses a Transformer to predict future tokens  

 Essentially, it treats time series like a **language modeling problem**, similar to how GPT predicts the next word.

---

##  Forecast Output

### 🔹 Historical vs Forecast Plot

<img width="844" height="470" alt="image" src="https://github.com/user-attachments/assets/7043b0ef-21f1-4d18-832d-24b2f1348a28" />


##  Installation

```bash
pip install chronos-forecasting pandas matplotlib
```

##  Usage

```python
from chronos import Chronos2Pipeline

pipeline = Chronos2Pipeline.from_pretrained("amazon/chronos-2")

pred_df = pipeline.predict_df(
    df,
    prediction_length=4
)
```
### Dataset Used
Monthly WPI Inflation Data (attached in repository) (Taken from the database on Indian Economy RBI estimation)
Period: March 2025 – February 2026
