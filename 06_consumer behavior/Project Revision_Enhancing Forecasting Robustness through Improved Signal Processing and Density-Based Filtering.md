# Project Revision: Enhancing Forecasting Robustness through Improved Signal Processing and Density-Based Filtering

## **Research Methodology (Image 1):**
<img width="1024" height="597" alt="image" src="https://github.com/user-attachments/assets/865f851f-7e02-4fd4-aaae-dbe1e49a8ca1" />


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

## 📈 Executive Summary

This technical revision delineates a robust engineering framework designed to mitigate the high **Stochasticity** (rastlantısallık) inherent in the Online Retail II dataset. By transitioning from a standard aggregate approach to a **Segment-Wise-Customer-Wise (SWCW)** methodology, we aim to isolate the **"Latent Behavioral Signal"** from seasonal **"Market Static."**

### Key Business Value Drivers:

* 🎯 **Precision Targeting:** Moving beyond volume-based metrics to **Habitual Density** ensures that marketing and supply chain resources are allocated to predictable, high-value cohorts.
* 🛡️ **Operational Integrity:** Advanced signal sanitation (**Winsorization** and **Linear Interpolation**) prevents the artificial inflation of financial projections caused by extreme outliers.
* 📊 **Predictive Reliability:** By resolving the **Scale-Mismatch** in noisy data, we achieve a lower **sMAPE**, directly translating to optimized inventory turnover.

---

## 🏗️ Technical Architecture: The End-to-End Pipeline

### Phase 1: Data Ingestion & Infrastructure Initialization (Obtain) 📥
* **Environment Orchestration:** Configuration of high-performance compute resources (GPU/CPU) and deployment of specialized dependencies (e.g., `pmdarima`, `statsmodels`).
* **Library Synchronization:** Loading core computational frameworks for signal processing (`scipy.signal`), statistical modeling (`statsmodels`), and machine learning (`sklearn`).
* **Data Acquisition & Preliminary Inspection:** Executing initial ingestion and verifying data schema integrity via descriptive statistical summaries (`.describe()`) and structural metadata analysis (`.info()`).

![Data Pipeline Overview]

### Phase 2: Advanced Data Sanitation & Feature Rectification (Scrub) 🧹
* **Data Sanitization (Advanced):**
    * **Deduplication:** Removal of redundant entries based on Invoice, StockCode, and Customer ID to prevent autocorrelation bias.
    * **Net Revenue Logic:** Implementation of a **"Return Strategy"** where $TotalAmount$ is calculated as $Quantity \times Price$, ensuring that credit notes and returns are treated as additive signal corrections rather than isolated noise.
    * **Outlier Mitigation:** Application of **Winsorization** (95th percentile limit) to neutralize the influence of heavy-tailed distributions and anomalous corporate bulk purchases.
* **Post-Scrub Distribution Analysis:** Statistical validation of the sanitized features. Visualizing the **"Spending Distribution"** and **"Return Ratio"** to confirm the normalization of the dataset and readiness for modeling.

### Phase 3: Stochastic Signal Filtering (Engineering - Part 1) 🔍
* **Habitual Density Thresholding:** Filtering for customers with a transaction density $\ge 70\%$.

  <img width="763" height="474" alt="image" src="https://github.com/user-attachments/assets/cc2ea763-b71f-40c9-87b9-50c539e7b43d" />


* **Engineering Logic:** This step is prioritized to ensure that subsequent statistical tests are executed only on "model-able" signals, significantly increasing the **Signal-to-Noise Ratio (SNR)**.

<img width="920" height="558" alt="image" src="https://github.com/user-attachments/assets/3677817f-d316-49de-a851-a848984d665f" />


### Phase 4: Temporal Exploratory Data Analysis (Explore) 🕰️
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
    * 
 
<img width="765" height="468" alt="image" src="https://github.com/user-attachments/assets/28d9c66d-980e-4a57-be62-2b8e13efa216" />


**Feature Scaling:** Unification of diverse metric scales through `MinMaxScaler` or `StandardScaler` to ensure dimensional parity.
    
* **Hierarchical Clustering Depth:**
  
    * Deployment of the **Elbow Method** and **Silhouette Analysis** to determine the optimal $k$-clusters.
 
      <img width="645" height="369" alt="image" src="https://github.com/user-attachments/assets/a4612e4f-1bb0-496b-8e75-eb20d6d4f91e" />

    * Application of **K-Means++** or **Ward’s Hierarchical Clustering** to define customer behavioral segments.

### Phase 6: SWCW Predictive Modeling & Validation (Model & Evaluate) 🤖
* **Segment-Wise-Customer-Wise (SWCW) Forecasting:**
    * Iterative execution of `auto_arima` loops for every individual customer within each segment, allowing for local hyperparameter optimization.
* **Multi-Metric Evaluation:** Benchmarking performance using **sMAPE**, **MAE**, and **RMSE** at the segment level.
* **Root Cause Error Analysis:** Identifying segment-specific failures (e.g., why Cluster X deviates from the ARIMA linearity) to refine future iterations.

### Phase 7: Signal Reconstruction & Visual Synthesis (Interpret) 📈
* **Refined Signal Smoothing:** Implementation of the **Savitzky-Golay Filter** to reconstruct the "Actual" trend line by removing high-frequency retail noise without introducing phase shift.
* **Interpretive Visualization:** Final presentation of **"Actual vs. Forecast"** plots in a publication-standard format, highlighting the predictive delta across diverse behavioral segments.

---

## 🔬 Technical Update: Comparison of Improvements

| Analysis Area | Problem Identified | Engineering Solution | Expected Outcome |
| :--- | :--- | :--- | :--- |
| **Data Imputation** | Zero-filling creating extreme gradients. | **Linear Interpolation** | Prevention of biased CID clustering. |
| **Stochasticity** | High-frequency "spikes" in retail data. | **Savitzky-Golay Smoothing** | Stabilization of the input signal for ARIMA. |
| **Customer Selection** | Simple activity thresholds were too loose. | **Habitual Density Filtering** | Elimination of "Impulse" noise from habit-based models. |
| **Metric Precision** | Scale-mismatch in noisy segments. | **Segment-Specific ARIMA** | Lowered sMAPE and higher forecasting precision. |

![Forecast Comparison Plot]




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

## 🏗️ Teknik Mimari: Uçtan Uca Boru Hattı 

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

## 📁 Ekler (Appendix)

Bu projenin teknik detayları, kullanılan matematiksel formüller ve hiperparametre optimizasyon süreçleri kod blokları içerisinde `technical-appendix.md` dosyasında saklanmaktadır.
