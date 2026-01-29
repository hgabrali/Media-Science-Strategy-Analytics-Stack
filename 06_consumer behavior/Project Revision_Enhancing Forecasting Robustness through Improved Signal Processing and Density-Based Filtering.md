# Project Revision: Enhancing Forecasting Robustness through Improved Signal Processing and Density-Based Filtering

## **Research Methodology (Image 1):**

<img width="1141" height="633" alt="image" src="https://github.com/user-attachments/assets/1e33ed1c-0bc9-4709-b6ab-a13249da51e3" />



## **SWCW Forecasting Framework (Image 2):** 

<img width="1122" height="626" alt="image" src="https://github.com/user-attachments/assets/c4a0cd71-be24-46d7-a015-033df3bf5fcc" />




# Comparative Analysis: Research Methodology vs. SWCW Forecasting Framework

This provides a technical comparison between the general research methodology (Image 1) and the specialized SWCW (Segment-Wise-Customer-Wise) Forecasting Framework (Image 2). The following analysis highlights the evolution from standard procedural workflows to high-precision engineering frameworks.

---

##  Comparative Technical Analysis

| Analysis Area | Research Methodology (Image 1) | SWCW Forecasting Framework (Image 2) |
| :--- | :--- | :--- |
| **Diagram Type & Purpose** | **Process Flowchart:** Designed to visualize sequential experimental steps and compare three distinct forecasting paths. | **Conceptual Infographic:** Designed to illustrate the engineering of robustness and the delivery of strategic business value. |
| **Scope & Focus** | **Comparative Methodology:** Emphasizes the workflow differences between Aggregate, Segment-Wise-Aggregate, and SWCW paths. | **Technical Value Proposition:** Focuses on the transformation of "Raw Signals" into "Strategic Drivers" through specialized refinement. |
| **Preprocessing & Signal Processing** | **General Operations:** Includes basic data splitting, target selection, RFM extraction, outlier removal, and normalization. | **Advanced Sanitation:** Employs **Winsorization**, **Linear Interpolation**, **Habitual Density Filtering ($\ge 70\%$)**, and **Savitzky-Golay Filters**. |
| **Modeling Approach** | **Standard Procedural:** Involves time-series clustering and finding the best ARIMA model based on mean cluster/global series. | **Granular Iteration:** Utilizes **Iterative ARIMA Loops** for every individual customer, optimizing hyperparameters at the micro-level. |
| **Outcome & Performance** | **Procedural Validation:** Ends with a general "performance comparison" and visualization of the best results. | **Business Synthesis:** Explicitly contrasts "Noisy sMAPE" vs. "Optimized sMAPE" and maps results to **Inventory Turnover** and **Resource Allocation**. |

---

##  Structural Breakdown

### 1. Methodology Evolution
While Image 1 provides the structural skeleton for a scientific experiment, Image 2 acts as the **robustness layer**. It replaces standard "Outlier Removal" with "Advanced Signal Sanitation" to ensure that the integration of credit notes and returns are treated as corrective signals rather than disruptive noise.



### 2. Signal-to-Noise Ratio (SNR) Optimization
The transition from Image 1 to Image 2 represents a shift toward higher **Signal-to-Noise Ratio (SNR)**. Image 2 introduces specific thresholds—such as the **Habitual Density Threshold ($\ge 70\%$)**—to filter out "Impulse" noise, ensuring the model only processes predictable, habit-based behavior.

### 3. Performance Shift Summary
The following table summarizes the performance outcomes as defined in the framework comparison:

| Metric / Feature | Aggregate Forecasting (Baseline) | SWCW Methodology (Proposed) |
| :--- | :--- | :--- |
| **Error Rate** | High (Noisy sMAPE) | **Optimized (Low sMAPE)** |
| **Signal Quality** | Raw / Unfiltered | **Sanitized & Smoothed** |
| **Granularity** | Macro-Level Aggregation | **Micro-Level (Individual) Optimization** |
| **Business Impact** | Static Projections | **Dynamic Resource Allocation** |

---

> **Technical Note:** The implementation of the **Savitzky-Golay Filter** in the SWCW framework is critical for reconstructing the trend line without the phase shift typically introduced by moving averages, preserving the temporal integrity of retail signals.



------

## Executive Summary

This technical revision delineates a robust engineering framework designed to mitigate the high **Stochasticity**  inherent in the Online Retail II dataset. By transitioning from a standard aggregate approach to a **Segment-Wise-Customer-Wise (SWCW)** methodology, we aim to isolate the **"Latent Behavioral Signal"** from seasonal **"Market Static."**

### Key Business Value Drivers:

* 🎯 **Precision Targeting:** Moving beyond volume-based metrics to **Habitual Density** ensures that marketing and supply chain resources are allocated to predictable, high-value cohorts.
* 🛡️ **Operational Integrity:** Advanced signal sanitation (**Winsorization** and **Linear Interpolation**) prevents the artificial inflation of financial projections caused by extreme outliers.
* 📊 **Predictive Reliability:** By resolving the **Scale-Mismatch** in noisy data, we achieve a lower **sMAPE**, directly translating to optimized inventory turnover.

---

## Technical Architecture: The End-to-End Pipeline

### Phase 1: Data Ingestion & Infrastructure Initialization (Obtain) 
* **Environment Orchestration:** Configuration of high-performance compute resources (GPU/CPU) and deployment of specialized dependencies (e.g., `pmdarima`, `statsmodels`).
* **Library Synchronization:** Loading core computational frameworks for signal processing (`scipy.signal`), statistical modeling (`statsmodels`), and machine learning (`sklearn`).
* **Data Acquisition & Preliminary Inspection:** Executing initial ingestion and verifying data schema integrity via descriptive statistical summaries (`.describe()`) and structural metadata analysis (`.info()`).

![Data Pipeline Overview]

### Phase 2: Advanced Data Sanitation & Feature Rectification (Scrub) 
* **Data Sanitization (Advanced):**
    * **Deduplication:** Removal of redundant entries based on Invoice, StockCode, and Customer ID to prevent autocorrelation bias.
    * **Net Revenue Logic:** Implementation of a **"Return Strategy"** where $TotalAmount$ is calculated as $Quantity \times Price$, ensuring that credit notes and returns are treated as additive signal corrections rather than isolated noise.
    * **Outlier Mitigation:** Application of **Winsorization** (95th percentile limit) to neutralize the influence of heavy-tailed distributions and anomalous corporate bulk purchases.
 
<img width="736" height="410" alt="image" src="https://github.com/user-attachments/assets/b169af7f-f98f-4ba4-9b9a-6479b0cc748d" />

   
* **Post-Scrub Distribution Analysis:** Statistical validation of the sanitized features. Visualizing the **"Spending Distribution"** and **"Return Ratio"** to confirm the normalization of the dataset and readiness for modeling.

### Phase 3: Stochastic Signal Filtering (Engineering - Part 1) 

* **Habitual Density Thresholding:** Filtering for customers with a transaction density $\ge 70\%$.

  <img width="763" height="474" alt="image" src="https://github.com/user-attachments/assets/cc2ea763-b71f-40c9-87b9-50c539e7b43d" />


* **Engineering Logic:** This step is prioritized to ensure that subsequent statistical tests are executed only on "model-able" signals, significantly increasing the **Signal-to-Noise Ratio (SNR)**.

<img width="920" height="558" alt="image" src="https://github.com/user-attachments/assets/3677817f-d316-49de-a851-a848984d665f" />


### Phase 4: Temporal Exploratory Data Analysis (Explore) 
* **Deep Temporal EDA (T-EDA):**
    * **Stationarity Assessment:** Execution of the **Augmented Dickey-Fuller (ADF)** Test to determine the integration order ($d$ parameter).
    * **Order Selection:** Analysis of **ACF/PACF** (Autocorrelation and Partial Autocorrelation) plots to identify the $p$ (Auto-regressive) and $q$ (Moving Average) components.
    * **Time-Series Decomposition:** Isolating Trend, Seasonality ($m, S$), and Residuals to inform the hyperparameter tuning of the seasonal ARIMA model.

<img width="1302" height="390" alt="image" src="https://github.com/user-attachments/assets/df1ea141-4501-47c4-a23a-14d07fb3ef65" />

<img width="1276" height="325" alt="image" src="https://github.com/user-attachments/assets/a6fa602b-b232-450f-86dc-f26377defd30" />

<img width="1287" height="326" alt="image" src="https://github.com/user-attachments/assets/320b3751-b603-4a4f-91b8-bede4c7f4172" />


<img width="1173" height="391" alt="image" src="https://github.com/user-attachments/assets/a2d9487c-cce5-4d2c-962c-0767853fc6bc" />


### Phase 5: Hybrid Behavioral Clustering & Multi-View Alignment (Engineering - Part 2) 🧩
* **The "RFM Bridge" (Hybrid Feature Engineering):**
    * Calculation of **RFM (Recency, Frequency, Monetary)** metrics to provide a business-logic layer.
    * Computation of the **Complexity-Invariant Distance (CID)** Matrix to capture temporal shape similarity.
      
 
<img width="765" height="468" alt="image" src="https://github.com/user-attachments/assets/28d9c66d-980e-4a57-be62-2b8e13efa216" />


**Feature Scaling:** Unification of diverse metric scales through `MinMaxScaler` or `StandardScaler` to ensure dimensional parity.
    
* **Hierarchical Clustering Depth:**
  
    * Deployment of the **Elbow Method** and **Silhouette Analysis** to determine the optimal $k$-clusters.
 
      <img width="645" height="369" alt="image" src="https://github.com/user-attachments/assets/a4612e4f-1bb0-496b-8e75-eb20d6d4f91e" />

    * Application of **K-Means++** or **Ward’s Hierarchical Clustering** to define customer behavioral segments.
 
  <img width="506" height="367" alt="image" src="https://github.com/user-attachments/assets/2ef4087c-e8bd-402d-ac8c-39cabba6cf66" />


### Phase 6: SWCW Predictive Modeling & Validation (Model & Evaluate) 🤖

<img width="1104" height="387" alt="image" src="https://github.com/user-attachments/assets/320d7efa-ecbd-4fac-a360-d58c3ff720cf" />

<img width="1082" height="392" alt="image" src="https://github.com/user-attachments/assets/5a5d3d60-eda2-4b49-9d63-d2dd773d7373" />

* **Segment-Wise-Customer-Wise (SWCW) Forecasting:**
    * Iterative execution of `auto_arima` loops for every individual customer within each segment, allowing for local hyperparameter optimization.
* **Multi-Metric Evaluation:** Benchmarking performance using **sMAPE**, **MAE**, and **RMSE** at the segment level.
* **Root Cause Error Analysis:** Identifying segment-specific failures (e.g., why Cluster X deviates from the ARIMA linearity) to refine future iterations.



### Phase 7: Signal Reconstruction & Visual Synthesis (Interpret) 📈
* **Refined Signal Smoothing:** Implementation of the **Savitzky-Golay Filter** to reconstruct the "Actual" trend line by removing high-frequency retail noise without introducing phase shift.
* **Interpretive Visualization:** Final presentation of **"Actual vs. Forecast"** plots in a publication-standard format, highlighting the predictive delta across diverse behavioral segments.


---

## Technical Update: Comparison of Improvements

| Analysis Area | Problem Identified | Engineering Solution | Expected Outcome |
| :--- | :--- | :--- | :--- |
| **Data Imputation** | Zero-filling creating extreme gradients. | **Linear Interpolation** | Prevention of biased CID clustering. |
| **Stochasticity** | High-frequency "spikes" in retail data. | **Savitzky-Golay Smoothing** | Stabilization of the input signal for ARIMA. |
| **Customer Selection** | Simple activity thresholds were too loose. | **Habitual Density Filtering** | Elimination of "Impulse" noise from habit-based models. |
| **Metric Precision** | Scale-mismatch in noisy segments. | **Segment-Specific ARIMA** | Lowered sMAPE and higher forecasting precision. |


<img width="1216" height="447" alt="image" src="https://github.com/user-attachments/assets/2c577d1a-e406-4b4e-936d-746f549d2ffd" />

<img width="1195" height="389" alt="image" src="https://github.com/user-attachments/assets/509b27f9-f98b-4cda-8861-ea0db27a4303" />

<img width="731" height="363" alt="image" src="https://github.com/user-attachments/assets/ae3f80fb-6053-49e9-acd8-733317e85117" />


# Business Insights: Strategic Interpretation of Reconstructed Customer Signals


<img width="1214" height="633" alt="image" src="https://github.com/user-attachments/assets/1b821954-b887-44a3-bdf0-5285e2344f8c" />


##  Executive Summary

The final synthesis of our **Segment-Wise-Customer-Wise (SWCW)** forecasting reveals a critical dichotomy within the Online Retail II portfolio. While the overall model successfully captures the **Latent Behavioral Trends** of stable segments (Clusters 3 & 4), it exposes high **Stochasticity** (randomness) in specific outlier segments (Clusters 1 & 2). 

By utilizing **Savitzky-Golay Signal Reconstruction**, we have successfully isolated the underlying customer habits from seasonal market noise, providing a higher-fidelity projection for **Customer Lifetime Value (CLV)**.

---

## Technical Analysis of Behavioral Segments

### 1. High-Precision Segments (Clusters 3 & 4) 
These segments represent the **"Core Revenue"** cohort. The alignment between the SWCW ARIMA forecast and the Reconstructed Actual Trend indicates a high **Signal-to-Noise Ratio (SNR)**.

* **Business Implication:** These customers exhibit **Predictable Consumption Cycles**. Supply chain and inventory allocation for these segments can be automated with high confidence.
* **Actionable Strategy:** Implement automated **Re-engagement Campaigns** and loyalty rewards, as their response to seasonal events ($m=52$) is mathematically consistent.

### 2. The Volatility Gap (Cluster 2) 
Cluster 2 displays a **Mean-Reverting Constant Forecast** against a highly volatile actual signal.

* **Technical Insight:** The model defaults to a "Mean Forecast" because the **Intra-week Variance** exceeds the linear capture capabilities of ARIMA. This suggests **"Event-Driven"** rather than **"Habit-Driven"** purchasing.
* **Business Implication:** This segment is highly reactive to external stimuli (promotions, stock-outs).
* **Actionable Strategy:** Avoid long-term inventory commitments for this cluster. Instead, use **Real-time Trigger Marketing** to capture the unpredictable spikes.

### 3. The "Silent" Outlier (Cluster 1 - $NaN$ sMAPE) 
The failure of sMAPE in Cluster 1 is a diagnostic signal of **Extreme Data Sparsity**.

* **Technical Insight:** When $Actual = 0$ and $Forecast = 0$, the mathematical representation of error becomes undefined. This customer has "flat-lined" or transitioned into a **Churn State**.
* **Business Implication:** Representing a single-customer cluster, this is an **Anomalous Outlier**.
* **Actionable Strategy:** Manual intervention or a **Win-back Campaign** is required to re-establish the transaction signal before further automated modeling is attempted.

---

## Reconstructed Trend vs. Raw Signal: The "Why"

The use of **Signal Reconstruction (Savitzky-Golay)** in Phase 7 is not merely for visualization; it is an engineering necessity to reveal **Latent Habitual Value**. 


$$d_{CID}(X,Y) = CF(X,Y) \cdot d_{L2}(X,Y)$$

By smoothing the "Actual" line, we prove that while the model cannot predict a specific high-frequency "spike" (noise), it accurately tracks the **Centroid of the Behavioral Trend**. This reduces the **Overfitting Risk** and ensures that CLV projections are not skewed by one-off bulk purchases.

---

##  Strategic Recommendations & Next Steps

| Segment Category | Forecasting Reliability | Recommended Business Action |
| :--- | :--- | :--- |
| **Stable Core (3 & 4)** | **High** (sMAPE < 40%) | Scale operations and automate procurement based on model outputs. |
| **Stochastic Pulse (2)** | **Medium** (Trend only) | Use as a "High-Volatility" alert; maintain safety stock buffers. |
| **At-Risk/Inactive (1)** | **Low** (Sparsity Failure) | Trigger immediate Churn-Prevention workflows; move to manual review. |

---

###  Final Engineering Takeaway
To further improve **Predictive Reliability** in the stochastic segments (1 & 2), we recommend moving beyond linear ARIMA in the next iteration. Potential upgrades include:
* Integrating **Exogenous Variables** (holidays, discount rates).
* Testing **Non-Linear Architectures** (e.g., LSTM or GRU) for high-variance clusters.







----
## TURKISH VERSION:

# Proje Revizyonu: Sinyal İşleme ve Yoğunluk Temelli Filtreleme Yoluyla Tahmin Sağlamlığının Artırılması 

## 📈 Yönetici Özeti 

Bu teknik revizyon, **Online Retail II** veri setinde doğal olarak bulunan yüksek **Rastlantısallığı (Stochasticity)** azaltmak için tasarlanmış sağlam bir mühendislik çerçevesini tanımlar. Standart bir toplu yaklaşımdan **Segment Bazlı-Müşteri Bazlı (Segment-Wise-Customer-Wise - SWCW)** metodolojisine geçiş yaparak, mevsimsel "Pazar Statikliğinden" **"Örtük Davranışsal Sinyali" (Latent Behavioral Signal)** izole etmeyi hedefliyoruz.

### Temel İş Değeri İtici Güçleri
* **Hassas Hedefleme (Precision Targeting):** Hacim odaklı metriklerin ötesine geçerek **Alışkanlık Yoğunluğuna (Habitual Density)** odaklanmak, pazarlama ve tedarik zinciri kaynaklarının öngörülebilir ve yüksek değerli kohortlara ayrılmasını sağlar.
* **Operasyonel Bütünlük (Operational Integrity):** Gelişmiş sinyal sanitasyonu (**Winsorizasyon (Winsorization)** ve **Lineer İnterpolasyon (Linear Interpolation)**), uç değerlerin (outliers) neden olduğu yapay finansal projeksiyon şişkinliklerini önler.
* **Tahmin Güvenilirliği (Predictive Reliability):** Gürültülü verilerdeki **Ölçek Uyumsuzluğunu (Scale-Mismatch)** çözerek, doğrudan optimize edilmiş envanter devir hızına dönüşen daha düşük bir **SMAPE** değerine ulaşırız.

---

## 🏗️ Teknik Mimari

### Aşama 1: Veri Alımı ve Altyapı Başlatma 
* **Ortam Orkestrasyonu (Environment Orchestration):** Yüksek performanslı hesaplama kaynaklarının (GPU/CPU) konfigürasyonu ve özel bağımlılıkların (**pmdarima**, **statsmodels**) konuşlandırılması.
* **Kütüphane Senkronizasyonu (Library Synchronization):** Sinyal işleme (**scipy.signal**), istatistiksel modelleme (**statsmodels**) ve makine öğrenmesi (**sklearn**) için temel hesaplama çerçevelerinin yüklenmesi.
* **Veri Edinimi ve Ön İnceleme (Data Acquisition & Preliminary Inspection):** İlk veri alımının gerçekleştirilmesi ve açıklayıcı istatistiksel özetler (**`.describe()`**) ve yapısal meta veri analizi (**`.info()`**) yoluyla veri şeması bütünlüğünün doğrulanması.

### Aşama 2: Gelişmiş Veri Temizleme ve Özellik Düzeltme 
* **Veri Sanitasyonu (Data Sanitization):**
    * **Tekilleştirme (Deduplication):** Otokorelasyon sapmasını (**Autocorrelation bias**) önlemek için Fatura, Stok Kodu ve Müşteri Kimliğine dayalı yinelenen girişlerin kaldırılması.
    * **Net Gelir Mantığı (Net Revenue Logic):** Toplam Tutarın (**TotalAmount**) $Quantity \times Price$ olarak hesaplandığı bir "İade Stratejisi" uygulanarak, kredi notlarının ve iadelerin izole gürültü yerine eklemeli sinyal düzeltmeleri olarak ele alınması.
* **Aykırı Değer Azaltma (Outlier Mitigation):** Ağır kuyruklu dağılımların (**Heavy-tailed distributions**) ve anormal kurumsal toplu alımların etkisini nötralize etmek için **Winsorizasyon (Winsorization)** (%95 persentil sınırı) uygulaması.
* **Temizlik Sonrası Dağılım Analizi (Post-Scrub Distribution Analysis):** Temizlenmiş özelliklerin istatistiksel doğrulaması. Veri setinin normalleşmesini ve modellemeye hazır olduğunu teyit etmek için **"Harcama Dağılımı" (Spending Distribution)** ve **"İade Oranı" (Return Ratio)** görsellerinin oluşturulması.



### Aşama 3: Stokastik Sinyal Filtreleme ( Engineering Part 1)
* **Alışkanlık Yoğunluğu Eşikleme (Habitual Density Thresholding):** İşlem yoğunluğu $\ge \%70$ olan müşteriler için filtreleme.
* **Mühendislik Mantığı (Engineering Logic):** Bu adım, sonraki istatistiksel testlerin yalnızca "modellenebilir" sinyaller üzerinde yürütülmesini sağlamak ve **Sinyal-Gürültü Oranını (Signal-to-Noise Ratio - SNR)** önemli ölçüde artırmak için önceliklendirilmiştir.

### Aşama 4: Zamansal Keşifçi Veri Analizi 
* **Derin Zamansal EDA :**
    * **Durağanlık Değerlendirmesi (Stationarity Assessment):** Entegrasyon sırasını (**$d$ parametresi**) belirlemek için **Genişletilmiş Dickey-Fuller (ADF) Testi** uygulaması.
    * **Derece Seçimi (Order Selection):** **$p$ (Oto-regresif)** ve **$q$ (Hareketli Ortalama)** bileşenlerini tanımlamak için **ACF/PACF** grafiklerinin analizi.
    * **Zaman Serisi Ayrıştırma (Time-Series Decomposition):** Mevsimsel ARIMA modelinin hiperparametre ayarlarını bilgilendirmek için **Trend, Mevsimsellik ($m, S$) ve Artıkları (Residuals)** izole etme.

### Aşama 5: Hibrit Davranışsal Kümeleme ve Çok Görünümlü Hizalama ( Engineering Part 2)
* **"RFM Köprüsü" (The RFM Bridge):**
    * İş mantığı katmanı sağlamak için **RFM (Recency, Frequency, Monetary)** metriklerinin hesaplanması.
    * Zamansal şekil benzerliğini yakalamak için **Karmaşıklık-Değişmez Mesafe (Complexity-Invariant Distance - CID)** matrisinin hesaplanması.
    * **Özellik Ölçeklendirme (Feature Scaling):** Boyutsal eşitliği sağlamak için **MinMaxScaler** veya **StandardScaler** yoluyla farklı metrik ölçeklerinin birleştirilmesi.
* **Hiyerarşik Kümeleme Derinliği (Hierarchical Clustering Depth):**
    * Optimal $k$-küme sayısını belirlemek için **Dirsek Yöntemi (Elbow Method)** ve **Silüet Analizi (Silhouette Analysis)** kullanımı.
    * Müşteri davranış segmentlerini tanımlamak için **K-Means++** veya **Ward Hiyerarşik Kümeleme** uygulaması.

### Aşama 6: SWCW Tahminleme ve Doğrulama 
* **Segment Bazlı-Müşteri Bazlı Tahminleme (SWCW Forecasting):**
    * Her segmentteki her bir müşteri için yerel hiperparametre optimizasyonuna izin veren **auto_arima** döngülerinin iteratif yürütülmesi.
* **Çok Metrikli Değerlendirme (Multi-Metric Evaluation):** Segment düzeyinde **SMAPE, MAE ve RMSE** kullanarak performans kıyaslaması (**Benchmarking**).
* **Kök Neden Hata Analizi (Root Cause Error Analysis):** Gelecekteki iterasyonları iyileştirmek için segmente özgü başarısızlıkların (örneğin, Küme X'in neden ARIMA lineerliğinden saptığı) belirlenmesi.

### Aşama 7: Sinyal Yeniden Yapılandırma ve Görsel Sentez 
* **Rafine Sinyal Yumuşatma (Refined Signal Smoothing):** Faz kayması yaratmadan yüksek frekanslı perakende gürültüsünü gidererek "Gerçek" trend çizgisini yeniden oluşturmak için **Savitzky-Golay Filtresi** uygulaması.
* **Yorumlayıcı Görselleştirme (Interpretive Visualization):** Çeşitli davranış segmentlerinde tahmin sapmasını vurgulayan, yayın standartlarında **"Gerçek vs. Tahmin"** grafiklerinin sunumu.

---

## 📊 Karşılaştırmalı Analiz Tablosu 

| Analiz Alanı | Problemler & Bileşenler | Teknik Detay & Önem | Çözüm Yöntemleri | Araçlar & Testler |
| :--- | :--- | :--- | :--- | :--- |
| **Veri Kalitesi** | Gürültü ve Aykırı Değerler | Tahmin sapmasını (bias) azaltır | Winsorization, Net Revenue Logic | Scipy, Pandas |
| **Sinyal Gücü** | Düşük SNR (Signal-to-Noise) | Modellenebilir veriyi ayırır | Habitual Density Thresholding | Custom Filters, ADF Test |
| **Segmentasyon** | Davranışsal Homojenlik | Tahmin doğruluğunu artırır | RFM & CID Matrix Hybrid | K-Means++, Silhouette |
| **Modelleme** | Ölçek Uyumsuzluğu | Yerel paternleri yakalar | SWCW (Segment-Wise) | Auto-ARIMA, Statsmodels |

---

## 💡 İş İçgörüleri

1.  **"So What?" (Peki ya Sonra?):** Rastlantısallığı %70 yoğunluk eşiğiyle filtreleyerek, pazarlama bütçesinin boşa harcandığı "gürültülü" müşteri grubundan kaçınılmıştır. Bu, **Müşteri Edinme Maliyeti (CAC)** verimliliğini doğrudan artırır.
2.  **Stratejik Stok Yönetimi:** Savitzky-Golay filtresi ile temizlenen trendler, ani talep sıçramalarına (anomaliler) karşı aşırı stok (overstocking) yapılmasını önleyerek depo maliyetlerini düşürür.
3.  **Kişiselleştirilmiş Tahmin:** Her segmentin kendi ARIMA parametrelerine sahip olması, "herkese uyan tek model" yaklaşımının getirdiği genel hata payını minimize eder.

---

# Technical Comparative Matrix: Research Baseline vs. Empirical Implementation

---

##  Overview
This document provides a detailed technical comparison between theoretical research baselines and the practical realities encountered during empirical implementation. It highlights the engineering resolutions required to bridge the gap between idealized datasets and volatile, real-world retail environments.


---

##  Comparative Analysis Table

| Technical Dimension | Research Baseline (Bank POS) | Project Reality (Online Retail II) | Engineering Resolution |
| :--- | :--- | :--- | :--- |
| **Stochastic Divergence** | Low **CV** (Coefficient of Variation); routine consumption patterns. | High-frequency noise; **promotion-driven** volatility and spikes. | Transition to **Signal-to-Noise Ratio (SNR)** optimization. |
| **Sampling Effects** | Large sample size (**N=123k**); stabilized by the **Law of Large Numbers**. | Small cluster cohorts; hypersensitive to **Outlier Behavior**. | Implementation of **Habitual Density** filtering. |
| **Metric Integrity** | **CID** (Complexity-Invariant Distance) on continuous data. | "Silent Weeks" creating **Artificial Complexity** in CID. | Deployment of **Linear Interpolation** as a prerequisite. |
| **Clustering Depth** | Unidimensional (**Shape-based** clustering only). | Disconnect between shape similarity and **Monetary Magnitude**. | Engineered a **Hybrid RFM Bridge** for multi-view alignment. |
| **Model Linearity** | Universal success using **SWCW ARIMA**. | Linear failure in sparse segments; **Constant Prediction** errors. | Validation of the need for **Non-linear Architectures** (LSTM/GARCH). |
| **Signal Processing** | Direct analysis on raw, aggregated time series. | **Latent Habitual Signal** obscured by market static. | Mandatory **Savitzky-Golay** Signal Reconstruction layer. |

---

##  Key Technical Definitions

* **Stochastic Divergence:** Measures the variance in data patterns. In retail, this is often exacerbated by seasonal promotions.
* **Sampling Effects:** Refers to how the volume of data affects the stability of statistical models.
* **Metric Integrity:** The reliability of distance metrics (like CID) when faced with missing or sparse data (e.g., "Silent Weeks").
* **Clustering Depth:** The dimensionality of customer segmentation, moving from simple shape analysis to multi-faceted behavioral models.
* **Model Linearity:** The determination of whether linear statistical models (ARIMA) or non-linear deep learning models (LSTM) are appropriate for the dataset.
* **Signal Processing:** The methods used to clean and reconstruct the underlying behavioral signals from noisy market data.

---


