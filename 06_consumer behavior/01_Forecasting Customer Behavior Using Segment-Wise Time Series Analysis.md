# Forecasting Customer Behavior Using Segment-Wise Time Series Analysis 

---

## About the Project & Motivation 🎯
This project is born out of a commitment to bridge the gap between **Theory** and **Practice**. I aimed to conduct a hands-on **Replication** of the methodology inspired by the original research paper, reflecting theoretical frameworks into a functional, real-world **Implementation**. 

By replicating the proposed **Segment-Wise-Customer-Wise (SWCW)** approach, this repository demonstrates how complex mathematical models can be translated into actionable **Business Insights** within the retail domain.

---



## 1. Project Overview 🚀
The goal of this study is to move beyond aggregate baseline models to provide granular, high-accuracy forecasts for customer segments. By treating customer transaction history as individual time series, we capture unique **Behavioral Patterns** often lost in global models.

## 2. Dataset Specification 📊
We utilize the **Online Retail II** dataset from the UCI Machine Learning Repository.

* **Source:** [UCI Machine Learning Repository - Online Retail II](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)
  
* **Contents:** Transactions (01/12/2009 - 09/12/2011) for a UK-based retail firm.
  
* **Target Feature:** **Monetary (M) value**, calculated as $Quantity \times Price$ aggregated over weekly intervals.

---

## 3. Methodology & Workflow 🛠️

### Phase A: Preprocessing
* **Temporal Splitting:** Transactional data is aggregated into weekly intervals.
* **Target Selection:** Filtering for "active customers" to ensure data continuity.
* **Outlier Removal:** Utilizing standard deviation-based anomaly detection.
* **Normalization (Normalizasyon):** Applying Min-Max scaling to a $[0, 1]$ range.

### Phase B: Time Series Clustering 
To handle **Behavioral Diversity**, customers are grouped using **Complexity-Invariant Distance (CID)**.
* **CID Measure:** Adjusts standard distance by a complexity correction factor.
* **Algorithm:** Agglomerative Hierarchical Clustering via **Ward’s Method**.

### Phase C: SWCW Forecasting 
1.  **Individual Modeling:** An optimal **ARIMA** $(p, d, q) \times (P, D, Q)_m$ model is fitted for every single customer.
2.  **Individual Prediction:** Each model generates a forecast for the test period.
3.  **Segment Aggregation:** The final segment forecast is the mean of all individual predictions.

---

## 4. Performance Evaluation 📈
Models are evaluated using:

* **Root Mean Square Error (RMSE):**
  
  
$$RMSE = \sqrt{\frac{1}{n}\sum_{t=1}^{n}(\hat{y}_{t}-y_{t})^{2}}$$
  
  
* **Symmetric Mean Absolute Percentage Error (SMAPE):**

$$SMAPE = \frac{1}{n}\sum_{t=1}^{n}\frac{|\hat{y}_{t}-y_{t}|}{\frac{|\hat{y}_{t}|+|y_{t}|}{2}}$$
  

---

## 5. Executive Summary 💼

This study transforms the academic SWCW framework into an operational system for real-world data. By leveraging CID and Individual ARIMA models, we preserve unique customer spending behaviors rather than using generalized models, resulting in superior precision and segment-focused financial forecasting in retail.

* Bu çalışma, akademik bir metodolojinin (SWCW) teorik çerçevesini alıp gerçek dünya verisi üzerinde çalışan bir sisteme dönüştürme motivasyonuyla hazırlanmıştır. **Karmaşıklık Değişmezliğine Sahip Mesafe (CID)** ve **Bireysel ARIMA** modelleri kullanılarak, genelleyici yaklaşımların aksine, her bir müşterinin özgün harcama karakteristiği korunmuştur. Bu sayede perakende sektörü için çok daha hassas ve segment odaklı finansal tahminler elde edilmiştir.

---

## 6. Technical Stack 💻
* **Language:** Python 3.x
* **Libraries:** `pandas`, `numpy`, `pmdarima`, `tslearn`, `scikit-learn`, `matplotlib`.
