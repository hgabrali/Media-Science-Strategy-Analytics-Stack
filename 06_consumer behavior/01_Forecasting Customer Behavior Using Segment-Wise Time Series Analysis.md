# Forecasting Customer Behavior Using Segment-Wise Time Series Analysis 

---

## About the Project & Motivation 🎯
This project is born out of a commitment to bridge the gap between **Theory** and **Practice**. I aimed to conduct a hands-on **Replication** of the methodology inspired by [the original research paper](https://github.com/hgabrali/Media-Science-Strategy-Analytics-Stack/blob/main/06_consumer%20behavior/Articals/01_Forecasting%20of%20Customer%20Behavior%20Using%20Time%20Series%20Analysis.pdf), reflecting theoretical frameworks into a functional, real-world **Implementation**. 

<img width="1024" height="597" alt="image" src="https://github.com/user-attachments/assets/3390d8b2-0aeb-4b63-a8c7-102b9ff45c7f" />


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


---

# Technical Comparative Analysis: Dataset Structural Discrepancy

<img width="731" height="701" alt="image" src="https://github.com/user-attachments/assets/e0f5418b-a2f5-4afa-a564-8141c48f7568" />

<img width="665" height="484" alt="image" src="https://github.com/user-attachments/assets/61559271-9441-4a9d-9909-066e54e57730" />

<img width="1414" height="525" alt="image" src="https://github.com/user-attachments/assets/94cde0db-79cf-4134-9659-f08f35243ede" />

<img width="1405" height="498" alt="image" src="https://github.com/user-attachments/assets/7f7ae873-5297-4d07-9ecb-98520319f65b" />


## 📝 Executive Summary 
This analysis delineates the fundamental engineering and statistical drivers behind the structural differences between the **"Actual"** data presented in the reference paper (Bank POS transactions) and the **Online Retail II** dataset. The divergence is primarily attributed to sectoral stability, sample size effects, and specific mathematical filtering.

* In the Bank POS study, the "Actual" line is essentially a **low-pass filtered** version of consumer behavior due to the sheer volume of transactions. In Online Retail, we are dealing with **high-entropy data** where individual event-driven impulses dominate the signal.

Bu analiz, referans makaledeki (Banka POS işlemleri) "Gerçek" (Actual) veriler ile "Online Retail II" veri seti arasındaki yapısal farklılıkların temel mühendislik ve istatistiksel itici güçlerini ana hatlarıyla belirtmektedir. Farklılık temel olarak **Sektörel Kararlılık (Sectoral Stability)**, **Büyük Sayılar Kanunu (Law of Large Numbers)** etkileri ve **Aktif Müşteriler (Active Customers)** üzerinde uygulanan spesifik matematiksel filtrelemeden kaynaklanmaktadır.

---

## 🔍 Detailed Technical Analysis 

### 1. Sectoral Divergence 
The paper utilizes bank POS transaction data, specifically filtering for a **"specific guild"** rather than analyzing the entire bank portfolio.

* **Paper Data :** They likely selected a sector with routine consumption (e.g., supermarket chains or pharmacies) where weekly spending habits are highly stable.
* **Online Retail II:** This dataset primarily consists of giftware and general retail. These sectors are highly sensitive to promotions, seasonal events (Mother’s Day, Christmas), and stock availability, which creates significant spikes and **Volatility ** in the time series.

### 2. The Law of Large Numbers 
The "Actual" line in the visualizations represents the **Centroid (Merkez/Ortalama)** of all customers within that specific cluster.

* **Paper Data :** The study includes 123,000 active customers with continuous transactions over 44 weeks. With such a large **Sample Size (Örneklem Büyüklüğü)**, individual **Outlier Behaviors (Aykırı Davranışlar)** neutralize each other, making the "average" curve significantly smoother.
* **Your Data (Sizin Veriniz):** In the Online Retail II set, the number of customers purchasing every single week for 44 weeks is likely much lower. As the sample size decreases, a single large order from one customer can disproportionately pull the cluster average upward, resulting in an **Irregular (Düzensiz)** appearance.

### 3. Rigidity of the "Active Customer" Definition 
The paper constructs its methodology exclusively on "customers who have transactions at all time points."

* This strict filtering eliminates **Temporal Gaps** in the data.
* If your dataset includes customers with **"Silent Weeks"**, these appear as sudden drops or irregularities in the time series, making the overall trend harder to model.

### 4. Impact of Complexity-Invariant Distance 
The paper employs **Complexity-Invariant Distance (CID)** as the primary metric for clustering, which is more robust than traditional **Euclidean Distance**.

* **Metric Characteristic:** CID evaluates the complexity (fluctuation pattern) of the series rather than just the magnitude of values.
* **Mathematical Representation:**
* 
$$d_{CID}(X,Y) = CF(X,Y) \cdot d_{L2}(X,Y)$$

* **Result (Sonuç):** This allows the authors to sharply isolate "regular spenders" into one cluster and "irregular spenders" into another. If the distance metric used does not capture these **Complexity Nuances**, clustering results may remain heterogeneous.



---

## 📈 Comparative Analysis Table 

| Analysis Area | Problems & Components | Technical Detail & Importance | Solution Methods | Tools & Tests |
| :--- | :--- | :--- | :--- | :--- |
| **Data Source** | Sectoral Volatility  | Retail vs. POS Necessity; dictates baseline noise. | Feature Engineering / Seasonal Adjustment | Pandas / Statsmodels |
| **Sampling** | Law of Large Numbers ) | Small samples lead to erratic mean curves. | Increasing N or Weighted Averaging | SciPy Stats / NumPy |
| **Filtering** | Zero-Transaction Gaps  | "Silent weeks" break ARIMA linearity. | Rigid "Active Customer" Thresholding | Boolean Indexing |
| **Similarity** | Magnitude vs. Shape  | Euclidean distance ignores temporal complexity. | Complexity-Invariant Distance (CID) | tslearn / CID Implementation |

---

## 💡 Business Insights 

* **The "So What?":** The "irregularity" in your dataset is not necessarily a failure of the model but a reflection of the **Retail Sector's Stochasticity**. While the paper deals with **"Predictable Habits"** (Bank POS), you are dealing with **"Impulse/Event-Driven Habits"** (Online Retail).
* **Actionable Strategy:** To achieve a "smoother" actual line for your report, consider applying a **Moving Average (MA - Hareketli Ortalama)** filter or a **Savitzky-Golay Filter** to the centroids to highlight the underlying trend over the noise, or further segmenting customers by **"Shopping Frequency Tiers"**.

---



