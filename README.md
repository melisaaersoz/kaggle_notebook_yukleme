# kaggle_notebook_yukleme
## Derin Öğrenme ile Balık Türlerini Sınıflandırma
Bu repo, görüntü verisi kullanarak balık türlerini sınıflandıran bir derin öğrenme projesini içerir. Projede, büyük ölçekli bir balık veri seti kullanılmış, veri artırma teknikleri uygulanmış ve TensorFlow ile Keras kullanılarak bir Yapay Sinir Ağı (ANN) modeli oluşturulmuştur.

## Veri Seti
Bu projede kullanılan veri seti, çeşitli balık türlerine ait görüntülerden oluşmaktadır. Veri seti Kaggle'dan alınmıştır:

## Veri seti linki: A Large Scale Fish Dataset
Veri seti, her balık türü için ayrı klasörler içermekte olup .png formatında görüntülerden oluşmaktadır. Bazı ekstra dosyalar (README.txt vb.), ön işleme aşamasında dahil edilmemiştir.

## Adımlar
### 1. Veri Yükleme ve Ön İşleme
Tüm görüntüler yüklendi ve boyutları 224x224 piksel olacak şekilde yeniden boyutlandırıldı.
Veri seti eğitim (%80), doğrulama (%10) ve test (%10) olmak üzere üçe bölündü.
Etiketler (balık türleri), model eğitimi için one-hot encoding yöntemiyle dönüştürüldü.
TensorFlow'un ImageDataGenerator sınıfı ile eğitim setine veri artırma (rotation, width shift, height shift, horizontal flip) teknikleri uygulandı.

### 2. Model Mimarisi
Model, aşağıdaki katmanlardan oluşan basit bir yapay sinir ağıdır:

Giriş Katmanı: Giriş görüntüsünü 1D bir diziye dönüştürür.
Yoğun (Dense) Katmanlar: Üç adet ReLU aktivasyon fonksiyonuna sahip yoğun katman, aşırı öğrenmeyi önlemek için Dropout katmanları ile birlikte.
Çıkış Katmanı: Softmax aktivasyon fonksiyonu ile çok sınıflı sınıflandırma (9 sınıf, balık türleri).
Optimizer: Adam, öğrenme oranı 0.0001
Kayıp Fonksiyonu: Categorical Crossentropy
Değerlendirme Metrikleri: Accuracy

### 3. Eğitim
Model 20 epoch boyunca, batch size 128 ile eğitildi. Doğrulama kaybını izleyerek erken durdurma (early stopping) uygulandı.

### 4. Değerlendirme ve Sonuçlar
Model, eğitim sonrası test verisinde değerlendirildi. Kullanılan temel metrikler:

Test Kayıp Değeri (Loss)
Test Doğruluğu (Accuracy)
Karmaşıklık Matrisi (Confusion Matrix)
Sınıflandırma Raporu (Precision, Recall, F1-Score)

### 5. Görselleştirme
Veri setindeki balık türlerinin dağılımını görselleştirmek için Seaborn ile bir countplot çizildi.
Modelin eğitim ve doğrulama doğruluğu/kayıp eğrileri, eğitim sonrası çizildi.
Sonuçlar:
Test Doğruluğu: 0,9444
Test Kayıp Değeri: 0.1707

## Teşekkür
Veri seti Kaggle tarafından sağlanmıştır.
Derin öğrenme çerçevesi: TensorFlow/Keras.
Görüntü işleme: OpenCV.

# Kaggle notebook linki
https://www.kaggle.com/code/melisaersoz/fish-dataset-deeplearning
