# Pima Indians Diabetes Prediction - KNN & Statistical Imputation Analysis

**Proje İsmi:** Pima Indians Diabetes Veri Analizi ve Sınıflandırma

**Projenin Amacı:**
Bu projenin amacı, Pima Kızılderilileri Diyabet Veri Seti'ni kullanarak bir hastanın tıbbi verilerine dayanarak diyabet olup olmadığını tahmin edebilen bir makine öğrenmesi modeli geliştirmektir. Proje, özellikle veri setindeki eksik değerlerin (0 değerleri) doldurulması aşamasında farklı stratejilerin modelin tahmin başarısı üzerindeki etkisini ölçmeyi ve en yüksek doğruluğa sahip modeli belirlemeyi hedefler.

**Yapılan İşlemler:**
*   **Veri Keşfi ve Ön İşleme:** Veri setindeki değişkenlerin dağılımı görselleştirildi ve mantıksız 0 değerleri (Glucose, BloodPressure, Insulin vb.) tespit edildi. Şüpheli veriler (örneğin diyabetik olmayan hastalardaki anormal derecede yüksek insülin değerleri) temizlendi.
*   **Farklı İmpute Yöntemlerinin Karşılaştırılması:**
    *   **İstatistiksel Impute (`IndianDataset.ipynb`):** Değişkenlerin çarpıklık (skewness) değerlerine bakılarak; çarpıklık düşükse **Ortalama (Mean)**, yüksekse **Medyan (Median)** ile doldurma işlemi gerçekleştirilmiştir.
    *   **KNN Impute (`IndianDatasetKNNImpute.ipynb`):** Eksik verilerin tamamlanması için daha gelişmiş bir yöntem olan **KNNImputer** algoritması kullanılmıştır.
*   **Ölçeklendirme:** Özellikle KNN tabanlı modelde aykırı değerlerin olumsuz etkisini minimize etmek için **RobustScaler** kullanılarak veriler ölçeklendirilmiştir.
*   **Model Eğitimi ve Optimizasyon:** `KNeighborsClassifier` algoritması temel alınmıştır. **GridSearchCV** tekniği kullanılarak en iyi k-komşu sayısı, mesafe metrikleri ve algoritma türleri gibi hiperparametreler optimize edilmiştir.
*   **Model Değerlendirme:** Karmaşıklık Matrisi (Confusion Matrix) ve Sınıflandırma Raporu (Precision, Recall, F1-Score) kullanılarak modeller test setinde değerlendirilmiştir.

**Sonuçlar:**
Modellerin performansı Accuracy, Precision, Recall ve F1-Score metrikleri ile değerlendirilmiştir. Bu bir sınıflandırma (classification) çalışması olduğu için başarı kriteri olarak bu metrikler baz alınmıştır. Projede elde edilen en yüksek başarı değerleri aşağıdadır:

*   **En İyi Doğruluk (Accuracy):** %77.13 (0.7712)
*   **Karmaşıklık Matrisi (Confusion Matrix):**
    ```
    [[103  18]
     [ 25  42]]
    ```
*   **Sınıflandırma Raporu:**
    *   **Diyabet Olmayan (Sınıf 0):** Precision: 0.80, Recall: 0.85, F1-Score: 0.83
    *   **Diyabetik (Sınıf 1):** Precision: 0.70, Recall: 0.63, F1-Score: 0.66
    *   **Genel Ortalama (Weighted Avg):** Precision: 0.77, Recall: 0.77, F1-Score: 0.77

İstatistiksel (Mean/Median) impute yöntemi ile yapılan çalışmalarda doğruluk oranı %71 gibi daha düşük seviyelerde kalırken, KNN Impute yönteminin eksik verileri tamamlamada ve model başarısını artırmada daha etkili olduğu görülmüştür.

**Kullanılan Dataset:**
https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database/data
