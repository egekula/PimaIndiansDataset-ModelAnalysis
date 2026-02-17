# Pima Indians Diabetes Prediction - Model Analysis & Threshold Optimization

**Proje İsmi:** Pima Indians Diabetes Veri Analizi ve Sınıflandırma

**Projenin Amacı:**
Bu projenin amacı, Pima Kızılderilileri Diyabet Veri Seti'ni kullanarak çeşitli makine öğrenmesi algoritmalarını karşılaştırmak ve diyabet riskini tahmin eden en güçlü modeli geliştirmektir. Özellikle eksik verilerin (0 değerleri) istatistiksel yöntemlerle tamamlanması, veri sızıntısının (data leakage) önlenmesi ve tıbbi teşhislerde kritik öneme sahip olan "Recall" (duyarlılık) değerinin optimize edilmesi hedeflenmiştir.

**Yapılan İşlemler:**
*   **Veri Keşfi ve Ön İşleme:** Veri setindeki 0 değerlerinin (Glucose, Blood Pressure, BMI vb.) dağılımları incelendi. Değişkenlerin çarpıklık (skewness) değerlerine göre; çarpıklık düşükse **Mean (Ortalama)**, yüksekse **Median (Medyan)** ile doldurma işlemi, veri sızıntısını önlemek amacıyla eğitim ve test setlerinde ayrı ayrı uygulandı.
*   **Model Karşılaştırması:** Veri setinde Logistic Regression, KNN, SVC, Decision Tree, Random Forest ve AdaBoost modelleri eğitilerek performansları karşılaştırıldı.
*   **Özellik Seçimi ve Mühendisliği:** Eksik değeri en çok olan 'Insulin' sütununun veri setinden çıkarılmasının model doğruluğunu 0.75'ten 0.76-0.77 seviyelerine çıkardığı tespit edildi.
*   **Ölçeklendirme:** Aykırı değerlerin etkisini minimize etmek için **RobustScaler** kullanıldı.
*   **Hiperparametre ve Eşik Değer Optimizasyonu:** **GridSearchCV** ile optimize edilen AdaBoost modelinde, hastalık teşhis başarısını (Recall) artırmak amacıyla sınıflandırma eşik değeri **0.45** olarak güncellendi.
*   **Değerlendirme:** Model performansı Karmaşıklık Matrisi, Sınıflandırma Raporu ve ROC/AUC eğrisi ile analiz edildi.

**Sonuçlar:**
AdaBoost modeli, İnsülin sütunu çıkarılmış ve eşik değeri 0.45'e çekilmiş test setinde en iyi sonuçları vermiştir:

*   **Doğruluk (Accuracy):** %77 (0.77)
*   **Diyabetik (Sınıf 1) Recall:** %80 (Hastalığı yakalama başarısı)
*   **ROC AUC Skoru:** 0.8191
*   **Karmaşıklık Matrisi (Confusion Matrix):**
    ```
    [[75  25]
     [11  43]]
    ```
*   **Sınıflandırma Raporu:**
    *   **Diyabet Olmayan (Sınıf 0):** Precision: 0.87, Recall: 0.75, F1-Score: 0.81
    *   **Diyabetik (Sınıf 1):** Precision: 0.63, Recall: 0.80, F1-Score: 0.70

İstatistiksel impute ve özellik seçimi stratejileriyle birleşen AdaBoost modeli, özellikle diyabetik vakaları kaçırmama (Recall) konusunda yüksek başarı göstermiştir.

**Kullanılan Dataset:**
https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database/data
