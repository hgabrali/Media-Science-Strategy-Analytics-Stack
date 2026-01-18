












----
## TURKISH VERSION:

# Proje Revizyonu: Sinyal İşleme ve Yoğunluk Temelli Filtreleme Yoluyla Tahmin Sağlamlığının Artırılması (Project Revision: Enhancing Forecasting Robustness through Improved Signal Processing and Density-Based Filtering)

## 📈 Yönetici Özeti (Executive Summary)

Bu teknik revizyon, **Online Retail II** veri setinde doğal olarak bulunan yüksek **Rastlantısallığı (Stochasticity)** azaltmak için tasarlanmış sağlam bir mühendislik çerçevesini tanımlar. Standart bir toplu yaklaşımdan **Segment Bazlı-Müşteri Bazlı (Segment-Wise-Customer-Wise - SWCW)** metodolojisine geçiş yaparak, mevsimsel "Pazar Statikliğinden" **"Örtük Davranışsal Sinyali" (Latent Behavioral Signal)** izole etmeyi hedefliyoruz.

### Temel İş Değeri İtici Güçleri (Key Business Value Drivers):
* **Hassas Hedefleme (Precision Targeting):** Hacim odaklı metriklerin ötesine geçerek **Alışkanlık Yoğunluğuna (Habitual Density)** odaklanmak, pazarlama ve tedarik zinciri kaynaklarının öngörülebilir ve yüksek değerli kohortlara ayrılmasını sağlar.
* **Operasyonel Bütünlük (Operational Integrity):** Gelişmiş sinyal sanitasyonu (**Winsorizasyon (Winsorization)** ve **Lineer İnterpolasyon (Linear Interpolation)**), uç değerlerin (outliers) neden olduğu yapay finansal projeksiyon şişkinliklerini önler.
* **Tahmin Güvenilirliği (Predictive Reliability):** Gürültülü verilerdeki **Ölçek Uyumsuzluğunu (Scale-Mismatch)** çözerek, doğrudan optimize edilmiş envanter devir hızına dönüşen daha düşük bir **SMAPE** değerine ulaşırız.

---

## 🏗️ Teknik Mimari: Uçtan Uca Boru Hattı (The End-to-End Pipeline)

### Aşama 1: Veri Alımı ve Altyapı Başlatma (Data Ingestion & Infrastructure Initialization - Obtain)
* **Ortam Orkestrasyonu (Environment Orchestration):** Yüksek performanslı hesaplama kaynaklarının (GPU/CPU) konfigürasyonu ve özel bağımlılıkların (**pmdarima**, **statsmodels**) konuşlandırılması.
* **Kütüphane Senkronizasyonu (Library Synchronization):** Sinyal işleme (**scipy.signal**), istatistiksel modelleme (**statsmodels**) ve makine öğrenmesi (**sklearn**) için temel hesaplama çerçevelerinin yüklenmesi.
* **Veri Edinimi ve Ön İnceleme (Data Acquisition & Preliminary Inspection):** İlk veri alımının gerçekleştirilmesi ve açıklayıcı istatistiksel özetler (**`.describe()`**) ve yapısal meta veri analizi (**`.info()`**) yoluyla veri şeması bütünlüğünün doğrulanması.

### Aşama 2: Gelişmiş Veri Temizleme ve Özellik Düzeltme (Advanced Data Sanitation & Feature Rectification - Scrub)
* **Veri Sanitasyonu (Data Sanitization):**
    * **Tekilleştirme (Deduplication):** Otokorelasyon sapmasını (**Autocorrelation bias**) önlemek için Fatura, Stok Kodu ve Müşteri Kimliğine dayalı yinelenen girişlerin kaldırılması.
    * **Net Gelir Mantığı (Net Revenue Logic):** Toplam Tutarın (**TotalAmount**) $Quantity \times Price$ olarak hesaplandığı bir "İade Stratejisi" uygulanarak, kredi notlarının ve iadelerin izole gürültü yerine eklemeli sinyal düzeltmeleri olarak ele alınması.
* **Aykırı Değer Azaltma (Outlier Mitigation):** Ağır kuyruklu dağılımların (**Heavy-tailed distributions**) ve anormal kurumsal toplu alımların etkisini nötralize etmek için **Winsorizasyon (Winsorization)** (%95 persentil sınırı) uygulaması.
* **Temizlik Sonrası Dağılım Analizi (Post-Scrub Distribution Analysis):** Temizlenmiş özelliklerin istatistiksel doğrulaması. Veri setinin normalleşmesini ve modellemeye hazır olduğunu teyit etmek için **"Harcama Dağılımı" (Spending Distribution)** ve **"İade Oranı" (Return Ratio)** görsellerinin oluşturulması.



### Aşama 3: Stokastik Sinyal Filtreleme (Stochastic Signal Filtering - Engineering Part 1)
* **Alışkanlık Yoğunluğu Eşikleme (Habitual Density Thresholding):** İşlem yoğunluğu $\ge \%70$ olan müşteriler için filtreleme.
* **Mühendislik Mantığı (Engineering Logic):** Bu adım, sonraki istatistiksel testlerin yalnızca "modellenebilir" sinyaller üzerinde yürütülmesini sağlamak ve **Sinyal-Gürültü Oranını (Signal-to-Noise Ratio - SNR)** önemli ölçüde artırmak için önceliklendirilmiştir.

### Aşama 4: Zamansal Keşifçi Veri Analizi (Temporal Exploratory Data Analysis - Explore)
* **Derin Zamansal EDA (Deep Temporal EDA):**
    * **Durağanlık Değerlendirmesi (Stationarity Assessment):** Entegrasyon sırasını (**$d$ parametresi**) belirlemek için **Genişletilmiş Dickey-Fuller (ADF) Testi** uygulaması.
    * **Derece Seçimi (Order Selection):** **$p$ (Oto-regresif)** ve **$q$ (Hareketli Ortalama)** bileşenlerini tanımlamak için **ACF/PACF** grafiklerinin analizi.
    * **Zaman Serisi Ayrıştırma (Time-Series Decomposition):** Mevsimsel ARIMA modelinin hiperparametre ayarlarını bilgilendirmek için **Trend, Mevsimsellik ($m, S$) ve Artıkları (Residuals)** izole etme.

### Aşama 5: Hibrit Davranışsal Kümeleme ve Çok Görünümlü Hizalama (Hybrid Behavioral Clustering - Engineering Part 2)
* **"RFM Köprüsü" (The RFM Bridge):**
    * İş mantığı katmanı sağlamak için **RFM (Recency, Frequency, Monetary)** metriklerinin hesaplanması.
    * Zamansal şekil benzerliğini yakalamak için **Karmaşıklık-Değişmez Mesafe (Complexity-Invariant Distance - CID)** matrisinin hesaplanması.
    * **Özellik Ölçeklendirme (Feature Scaling):** Boyutsal eşitliği sağlamak için **MinMaxScaler** veya **StandardScaler** yoluyla farklı metrik ölçeklerinin birleştirilmesi.
* **Hiyerarşik Kümeleme Derinliği (Hierarchical Clustering Depth):**
    * Optimal $k$-küme sayısını belirlemek için **Dirsek Yöntemi (Elbow Method)** ve **Silüet Analizi (Silhouette Analysis)** kullanımı.
    * Müşteri davranış segmentlerini tanımlamak için **K-Means++** veya **Ward Hiyerarşik Kümeleme** uygulaması.

### Aşama 6: SWCW Tahminleme ve Doğrulama (SWCW Predictive Modeling & Validation - Model & Evaluate)
* **Segment Bazlı-Müşteri Bazlı Tahminleme (SWCW Forecasting):**
    * Her segmentteki her bir müşteri için yerel hiperparametre optimizasyonuna izin veren **auto_arima** döngülerinin iteratif yürütülmesi.
* **Çok Metrikli Değerlendirme (Multi-Metric Evaluation):** Segment düzeyinde **SMAPE, MAE ve RMSE** kullanarak performans kıyaslaması (**Benchmarking**).
* **Kök Neden Hata Analizi (Root Cause Error Analysis):** Gelecekteki iterasyonları iyileştirmek için segmente özgü başarısızlıkların (örneğin, Küme X'in neden ARIMA lineerliğinden saptığı) belirlenmesi.

### Aşama 7: Sinyal Yeniden Yapılandırma ve Görsel Sentez (Interpret)
* **Rafine Sinyal Yumuşatma (Refined Signal Smoothing):** Faz kayması yaratmadan yüksek frekanslı perakende gürültüsünü gidererek "Gerçek" trend çizgisini yeniden oluşturmak için **Savitzky-Golay Filtresi** uygulaması.
* **Yorumlayıcı Görselleştirme (Interpretive Visualization):** Çeşitli davranış segmentlerinde tahmin sapmasını vurgulayan, yayın standartlarında **"Gerçek vs. Tahmin"** grafiklerinin sunumu.

---

## 📊 Karşılaştırmalı Analiz Tablosu (Comparative Analysis Table)

| Analiz Alanı | Problemler & Bileşenler | Teknik Detay & Önem | Çözüm Yöntemleri | Araçlar & Testler |
| :--- | :--- | :--- | :--- | :--- |
| **Veri Kalitesi** | Gürültü ve Aykırı Değerler | Tahmin sapmasını (bias) azaltır | Winsorization, Net Revenue Logic | Scipy, Pandas |
| **Sinyal Gücü** | Düşük SNR (Signal-to-Noise) | Modellenebilir veriyi ayırır | Habitual Density Thresholding | Custom Filters, ADF Test |
| **Segmentasyon** | Davranışsal Homojenlik | Tahmin doğruluğunu artırır | RFM & CID Matrix Hybrid | K-Means++, Silhouette |
| **Modelleme** | Ölçek Uyumsuzluğu | Yerel paternleri yakalar | SWCW (Segment-Wise) | Auto-ARIMA, Statsmodels |

---

## 💡 İş İçgörüleri (Business Insights)

1.  **"So What?" (Peki ya Sonra?):** Rastlantısallığı %70 yoğunluk eşiğiyle filtreleyerek, pazarlama bütçesinin boşa harcandığı "gürültülü" müşteri grubundan kaçınılmıştır. Bu, **Müşteri Edinme Maliyeti (CAC)** verimliliğini doğrudan artırır.
2.  **Stratejik Stok Yönetimi:** Savitzky-Golay filtresi ile temizlenen trendler, ani talep sıçramalarına (anomaliler) karşı aşırı stok (overstocking) yapılmasını önleyerek depo maliyetlerini düşürür.
3.  **Kişiselleştirilmiş Tahmin:** Her segmentin kendi ARIMA parametrelerine sahip olması, "herkese uyan tek model" yaklaşımının getirdiği genel hata payını minimize eder.

---

## 📁 Ekler (Appendix)

Bu projenin teknik detayları, kullanılan matematiksel formüller ve hiperparametre optimizasyon süreçleri kod blokları içerisinde `technical-appendix.md` dosyasında saklanmaktadır.
