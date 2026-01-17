# Forecasting Customer Behavior Using Segment-Wise Time Series Analysis 📈

This repository contains a replication and implementation of the methodology proposed in the study: **"Forecasting of Customer Behavior Using Time Series Analysis"**. The project focuses on predicting future customer behavior (Monetary value) by combining **Time Series Clustering** with **Segment-Wise-Customer-Wise (SWCW) Forecasting (Segment Bazlı-Müşteri Bazlı Tahminleme)**.

---

## 1. Project Overview 🎯
The goal of this study is to move beyond aggregate baseline models to provide granular, high-accuracy forecasts for customer segments. By treating customer transaction history as individual time series, we can capture unique behavioral patterns (**Davranışsal Kalıplar**) that are often lost in global models.

## 2. Dataset Specification 📊
We utilize the **Online Retail II** dataset from the UCI Machine Learning Repository.

* **Source:** [UCI Machine Learning Repository - Online Retail II](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)
* **Contents:** Transactions occurring between 01/12/2009 and 09/12/2011 for a UK-based, non-store online retail.
* **Key Attributes:** Customer ID, InvoiceDate, Quantity, Price.
* **Target Feature:** **Monetary (M) value**, calculated as $Quantity \times Price$ aggregated over weekly intervals.

---

## 3. Methodology & Workflow 🛠️
The implementation follows a rigorous structured methodology illustrated in the study's framework:



### Phase A: Preprocessing
1.  **Temporal Splitting:** Transactional data is aggregated into weekly time intervals to form consistent time series data.
2.  **Target Selection:** Filtering for "active customers" who have transactions across all time points to ensure data continuity.
3.  **Outlier Removal:** Utilizing standard deviation-based anomaly detection (**Standart Sapma Tabanlı Anomali Tespiti**) to mitigate the impact of extreme values.
4.  **Normalization:** Applying Min-Max normalization to bring all customer series into a comparable range $[0, 1]$.

### Phase B: Time Series Clustering
To handle behavioral diversity, customers are grouped using **Complexity-Invariant Distance (CID)**.

* **CID Measure:** Adjusts standard Euclidean distance by a complexity correction factor to better account for temporal fluctuations.
* **Algorithm:** Agglomerative Hierarchical Clustering  using **Ward’s Method** to minimize within-cluster variance.
* Neden Önemli?: İki müşteri aynı toplam harcamayı yapmış olabilir, ancak biri düzenli aralıklarla harcama yaparken diğeri düzensiz (stokastik) harcama yapıyor olabilir. CID bu farkı algılayarak, sadece "miktar" bazlı değil, "davranış biçimi" bazlı bir kümeleme yapmanıza olanak tanır.

### Phase C: Segment-Wise-Customer-Wise (SWCW) Forecasting
Unlike standard aggregate methods, the SWCW approach follows these steps:
1.  **Individual Modeling:** An optimal **ARIMA** $(p, d, q) \times (P, D, Q)_m$ model is fitted for every individual customer within a cluster.
2.  **Individual Prediction:** Each model generates a forecast for the test period.
3.  **Segment Aggregation:** The final segment forecast is the mean of all individual customer predictions within that specific cluster.

---

## 4. Performance Evaluation 📈
Models are evaluated using two primary metrics to ensure robustness against different scales of data:

### Root Mean Square Error (RMSE)
Used to measure the magnitude of the error.

$$RMSE = \sqrt{\frac{1}{n}\sum_{t=1}^{n}(\hat{y}_{t}-y_{t})^{2}}$$

### Symmetric Mean Absolute Percentage Error (SMAPE)
Used for relative error analysis, providing a percentage-based evaluation.

$$SMAPE = \frac{1}{n}\sum_{t=1}^{n}\frac{|\hat{y}_{t}-y_{t}|}{\frac{|\hat{y}_{t}|+|y_{t}|}{2}}$$

---

## 5. Comparative Analysis of Methodology 🔍

| Analysis Area | Problems & Components | Technical Detail & Importance | Solution Methods | Tools & Tests |
| :--- | :--- | :--- | :--- | :--- |
| **Data Aggregation** | Sparsity (Seyreklik) | Consistent intervals are needed for ARIMA | Weekly Resampling | Pandas `resample()` |
| **Clustering** | Pattern Overlap | Traditional Euclidean distance ignores complexity | Complexity-Invariant Distance (CID) | `tslearn.metrics` |
| **Forecasting** | Heterogeneity | One-size-fits-all models fail on diverse behavior | SWCW (Individual ARIMA) | `pmdarima` Auto-ARIMA |

---

## 6. Executive Summary
Bu çalışma, müşteri davranışlarını tek bir blok olarak tahmin etmek yerine, benzer harcama kalıplarına sahip müşterileri **Karmaşıklık Değişmezliğine Sahip Mesafe (CID)** yöntemiyle gruplandırır. Her müşteri için özel bir **ARIMA** modeli oluşturularak yapılan tahminler, segment bazında birleştirilir. Bu yaklaşım, genel modellerin kaçırdığı mikro trendleri yakalayarak perakende stratejilerinde daha isabetli finansal öngörüler (Monetary Value Forecasting) sağlar.

---

## 7. Technical Stack 💻
* **Language:** Python 3.x
* **Data Handling:** `pandas`, `numpy`
* **Time Series Analysis:** `pmdarima` (Auto-ARIMA), `statsmodels`
* **Clustering:** `tslearn` (for CID/DTW support), `scikit-learn`
* **Visualization:** `matplotlib`, `seaborn`
