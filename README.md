# Cats-Dogs-CNN-Transfer-Learning
# Cats & Dogs Small Dataset: Comparison of a Base CNN and Transfer Learning Models

Bu proje, Kaggle üzerinde yer alan mevcut [Cats & Dogs Small Dataset](https://www.kaggle.com/code/fatihhattatoglu/cat-dogs) çalışmasının genişletilmiş ve geliştirilmiş bir versiyonudur. 

Projenin temel amacı; özelleştirilmiş bir **Base CNN** mimarisi ile popüler transfer öğrenme (Transfer Learning) modellerinin (**VGG16, ResNet50 ve EfficientNetB0**) performanslarını aynı deneysel koşullar altında objektif olarak karşılaştırmaktır. Küçük veri setlerinde transfer öğrenmenin ezberlemeyi (overfitting) azaltmadaki ve doğruluğu artırmadaki rolü incelenmiştir.

---

## Proje Özeti
* **Orijinal Veri Seti Bölünmesi:** Çalışmanın tutarlılığı açısından orijinal `train/test` (eğitim/test) veri dağılımı tamamen korunmuştur.
* **Karşılaştırmalı Yaklaşım:** Tüm modeller aynı eğitim ve test verileriyle beslenerek derin öğrenme mimarilerinin küçük veri setleri üzerindeki başarısı analiz edilmiştir.
* **Donanım ve Altyapı:** Çalışma, TensorFlow 2.18.0 sürümü kullanılarak çift GPU (`GPU:0` ve `GPU:1`) mimarisi üzerinde optimize edilerek çalıştırılmıştır.

---

## Veri Seti Detayları
Projede kullanılan küçük veri seti (Small Dataset) sınıf bazında şu dağılıma sahiptir:

| Veri Bölümü (Split) | Kedi (Cat) | Köpek (Dog) | Toplam |
| :--- | :---: | :---: | :---: |
| **Eğitim (Train)** | 95 | 180 | 275 |
| **Test** | 24 | 46 | 70 |

---

## Kullanılan Modeller ve Mimari Yaklaşımlar

Proje kapsamında aşağıdaki mimarilerin sınıflandırma performansları karşılaştırılmıştır:

1. **Base CNN:** Sıfırdan (from scratch) eğitilen, ardışık konvolüsyon (Conv2D), havuzlama (MaxPooling2D) ve aşırı öğrenmeyi engellemek için Dropout katmanları içeren temel derin öğrenme modelidir.
2. **VGG16:** ImageNet ağırlıklarıyla önceden eğitilmiş, derin ve ardışık katman yapısıyla öne çıkan klasik transfer öğrenme modelidir. Üst katmanları dondurularak veri setine özel sınıflandırma başlığı eklenmiştir.
3. **ResNet50:** Derin ağlardaki kaybolan gradyan (vanishing gradient) problemini aşmak için artık bağlantılar (residual connections) kullanan güçlü bir mimaridir.
4. **EfficientNetB0:** Katman derinliği, genişliği ve çözünürlüğü dengeli bir şekilde ölçeklendiren (compound scaling), parametre verimliliği son derece yüksek modern bir transfer öğrenme modelidir.

---

##  Kurulum ve Gereksinimler

Projenin çalıştırılması ve modellerin eğitilmesi için gerekli temel kütüphaneler şunlardır:

* **TensorFlow / Keras (v2.18.0):** Model mimarilerinin kurulması, ağırlıkların yüklenmesi ve eğitim süreçleri.
* **NumPy & Pandas:** Veri ön işleme, matris manipülasyonları ve sonuçların tablo haline getirilmesi.
* **Matplotlib & Seaborn:** Modellerin eğitim/doğrulama grafiklerinin çizilmesi ve performans analizleri.

### Yerel Ortamda Çalıştırma

Projeyi yerel bilgisayarınızda veya başka bir sunucuda çalıştırmak için gerekli kütüphaneleri yükleyebilirsiniz:

'```bash
pip install tensorflow numpy pandas matplotlib seaborn ```'

---

## Veri Yolu Yapısı

Kaggle çalışma ortamında kullanılan ve kodun doğrudan okuduğu dosya dizin yapısı şu şekildedir:

'/kaggle/input/cats-and-dogs/
├── train/
│   ├── cat/
│   └── dog/
└── val/
    ├── cat/
    └── dog/'
------

## Performans ve Karşılaştırma Sonuçları
<img width="574" height="233" alt="image" src="https://github.com/user-attachments/assets/e93e1fe0-6747-4787-9c3e-503af3cb1b59" />

<img width="762" height="300" alt="image" src="https://github.com/user-attachments/assets/efe0dd3e-be13-4856-9691-1f3b2ea91ab3" />

------
## SONUÇ

Comparison of CNN Model Performance Scores Tablosu ve Comparison of CNN Models on the Test Set Grafik'te dört CNN modelinin test veri kümesi üzerindeki performansları karşılaştırılmıştır. Base CNN modeli, %47.14 doğruluk ve 0.9535 loss değeri ile en düşük performansı göstermiştir. Bu sonuç, modelin test verisi üzerinde yeterli genelleme yapamadığını göstermektedir.

Transfer öğrenme tabanlı modeller olan VGG16, ResNet50 ve EfficientNetB0, Base CNN modeline göre belirgin şekilde daha başarılı sonuçlar elde etmiştir. VGG16 ve ResNet50 modelleri aynı doğruluk oranına (%98.57) ulaşmasına rağmen, ResNet50 daha düşük loss değeri (0.0429) elde ederek VGG16'ya göre daha başarılı bir performans sergilemiştir.

Tüm modeller arasında EfficientNetB0, %100 test doğruluğu ve 0.0325 ile en düşük test loss değerini elde ederek en başarılı model olmuştur. Bu nedenle, çalışmanın sonraki aşamalarında kullanılmak üzere nihai model olarak EfficientNetB0 seçilmiştir.

---

##  Kaggle Proje Linki

Bu projeyi Kaggle üzerinde incelemek ve desteklemek (upvote) isterseniz aşağıdaki bağlantıdan ulaşabilirsiniz:

[Kaggle Notebook: Cats-Dogs-CNN-Transfer-Learning](https://www.kaggle.com/code/neclaersz/cats-dogs)

## Referanslar
Veri setinin alındığı ve projenin temelini oluşturan orijinal Kaggle çalışması: Fatih Hattatoğlu - Cat & Dogs



