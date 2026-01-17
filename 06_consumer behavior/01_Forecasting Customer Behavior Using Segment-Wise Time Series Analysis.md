# Forecasting Customer Behavior Using Segment-Wise Time Series Analysis 

---

## About the Project & Motivation 🎯
This project is born out of a commitment to bridge the gap between **Theory** and **Practice**. I aimed to conduct a hands-on **Replication** of the methodology inspired by [the original research paper](https://github.com/hgabrali/Media-Science-Strategy-Analytics-Stack/blob/main/06_consumer%20behavior/Articals/01_Forecasting%20of%20Customer%20Behavior%20Using%20Time%20Series%20Analysis.pdf), reflecting theoretical frameworks into a functional, real-world **Implementation**. 

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

----
----


# 📊 Technical Final Report: Enhancing Customer Behavior Forecasting via Segment-Wise Time Series Analysis

## 📝 Executive Summary (Yönetici Özeti)
This project focuses on developing a high-precision forecasting methodology (Yüksek hassasiyetli tahminleme metodolojisi) for customer behavior, specifically targeting the **Monetary (M)** attribute of the RFM model. 

By integrating **Time Series Clustering (Zaman Serisi Kümeleme)** using **Complexity-Invariant Distance (CID)** and a specialized **Segment-Wise-Customer-Wise (SWCW) ARIMA** approach, we have created a system that significantly outperforms traditional aggregate forecasting methods. This approach allows businesses to move beyond "one-size-fits-all" models, providing granular insights into individual customer spending patterns and enabling more efficient resource allocation.

---

## 1. Introduction (Giriş)
Forecasting customer behavior is a critical component of **Business Intelligence (BI - İş Zekası)**. While traditional models focus on aggregate data (toplulaştırılmış veri), this project addresses the challenge of managing diverse customer populations by segmenting them based on past transactional time series.

## 2. Dataset Specification (Veri Kümesi Özellikleri)
* **Source:** Online Retail II Dataset (UCI Machine Learning Repository).
* **Raw Data:** Over 525,000 records of transactions including Customer ID, InvoiceDate, Price, and Quantity.
* **Target Metric:** The **Monetary (M)** attribute, calculated as the total purchase amount per customer within a specific time interval.

## 3. Methodology (Metodoloji)

### 3.1. Preprocessing (Ön İşleme)
The raw transactional data underwent rigorous engineering steps:
* **Temporal Aggregation (Zamansal Toplulaştırma):** Data was split into weekly intervals to reduce daily noise and create a manageable 44-point time series.
* **Target Selection:** Focused on active customers who exhibited transactions across all time points.
* **Outlier Removal (Aykırı Değer Temizleme):** Applied standard deviation-based clipping to eliminate anomalies and incorrect data points.
* **Normalization (Normalizasyon):** Employed Min-Max Normalization to scale values between $0$ and $1$ for consistent comparison across different customer tiers.

### 3.2. Time Series Clustering (Zaman Serisi Kümeleme)
To group similar behaviors, we implemented **Hierarchical Agglomerative Clustering (Hiyerarşik Kümeleme)** with Ward's Method.



* **Similarity Measure:** Complexity-Invariant Distance (CID). Unlike standard Euclidean distance, CID incorporates a complexity correction factor $CF$:
  $$d_{CID}(X,Y) = CF(X,Y) \cdot d_{L2}(X,Y)$$
* **Optimal Segments:** Based on the **Silhouette Index**, customers were divided into $K=4$ distinct clusters.

### 3.3. Modelling Strategy: SWCW vs. SWA
The project implemented and compared three approaches:
1.  **Aggregate Forecasting:** Predicts the global mean of all customers.
2.  **Segment-Wise-Aggregate (SWA):** Predicts the mean time series for each cluster.
3.  **Segment-Wise-Customer-Wise (SWCW):** The proposed superior method.
    * Finds the best **ARIMA $(p,d,q)$** model for each individual customer.
    * Aggregates individual forecasts to generate a cluster-level prediction.

---

## 4. Experimental Results & Analysis (Deneysel Sonuçlar ve Analiz)

### 4.1. Evaluation Metrics (Değerlendirme Metrikleri)
Success was measured using **RMSE** and **SMAPE**:
* **RMSE (Kök Ortalama Kare Hata):** Measures the deviation of forecast values from actual values.
* **SMAPE (Simetrik Ortalama Mutlak Yüzde Hata):** Provides a symmetric percentage error, useful for scale-independent comparison.

### 4.2. Comparative Performance (Karşılaştırmalı Performans)
| Forecasting Method | RMSE | SMAPE |
| :--- | :--- | :--- |
| **Aggregate Forecasting** | 0.0450 | 0.5900 |
| **Segment-Wise-Aggregate (SWA)** | 0.0468 | 0.8584 |
| **Segment-Wise-Customer-Wise (SWCW)** | **0.0344** | **0.3818** |

### 4.3. Visualization (Actual vs. Predicted)
Visual analysis across the 4 segments confirms that the **SWCW model** tracks peaks and volatility much more effectively than the SWA method.

## 5. Conclusion (Sonuç)
The implementation confirms that behavioral segmentation combined with individual-level time series modeling (SWCW) provides a higher level of accuracy than baseline models. This methodology is highly generalizable to other domains requiring effective future behavior forecasting for diverse groups.

---

## 📂 Appendix (Ekler)

### Technical Stack (Teknoloji Yığını)
* **Language:** Python 3.10+
* **Libraries:** * `pandas`, `numpy` (Processing)
    * `tslearn`, `scipy` (Clustering)
    * `pmdarima` (ARIMA Modeling)
    * `matplotlib`, `seaborn` (Visualization)

### Business Insights (İş Analizleri)
* **The "So What?":** By using SWCW, the marketing department can predict the future "Monetary" value of a specific segment with ~35% more accuracy than general averages. This allows for hyper-personalized discount campaigns.
* **Scalability:** The model uses individual ARIMA parameters, meaning as the customer base grows, the segments remain distinct and manageable.
