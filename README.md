- ph (float64):

  - Açıklama: Su numunesinin pH seviyesi. pH, bir sıvının asidik mi yoksa bazik mi olduğunu gösteren bir ölçüdür. pH değeri 7 ise nötrdür, 7'den küçükse asidik, 7'den büyükse baziktir.

  - Eksik Veri Oranı: Bu sütunda %17 civarında eksik veri var. 2785 kayıt mevcut, ancak 3276 satırdan toplamda 3276 - 2785 = 491 eksik değer bulunuyor.
  
  
- Hardness (float64):

  - Açıklama: Su sertliği, sudaki kalsiyum ve magnezyum iyonlarının konsantrasyonunun bir ölçüsüdür. Yüksek sertlik, suyun mineraller açısından zengin olduğunu gösterir.
  
  - Eksik Veri Oranı: Bu sütunda hiç eksik veri yok (3276 satırda da değer var).  
  
  
- Solids (float64):

  - Açıklama: Su numunesindeki toplam katı madde miktarını ifade eder. Katı maddeler, suda çözünmüş veya askıda bulunan her türlü maddeyi içerir.

  - Eksik Veri Oranı: Bu sütunda da eksik veri yoktur (3276 satırda da değer var).  
  
- Chloramines (float64):

  - Açıklama: Su dezenfeksiyonunda kullanılan kloraminlerin seviyesi. Kloraminler, klor ile amonyağın birleşiminden oluşan kimyasallardır ve genellikle içme suyu dezenfeksiyonunda kullanılır.

  - Eksik Veri Oranı: Bu sütunda da eksik veri yoktur (3276 satırda da değer var).

- Sulfate (float64):

  - Açıklama: Suda bulunan sülfat iyonlarının miktarını gösterir. Yüksek sülfat seviyeleri suyun kalitesini etkileyebilir ve bazı sağlık sorunlarına yol açabilir.

  - Eksik Veri Oranı: Bu sütun, % 31 civarında eksik verilere sahip. 2495 kayıt var.
  
- Conductivity (float64):

  - Açıklama: Su iletkenliği, sudaki iyonların elektriksel iletkenliğini ölçer. Yüksek iletkenlik, sudaki yüksek mineral yoğunluğunu gösterebilir.
  
  - Eksik Veri Oranı: Bu sütunda eksik veri yoktur (3276 satırda da değer var).

- Organic_carbon (float64):

  - Açıklama: Suda bulunan organik karbon miktarını ifade eder. Organik karbon, suyun kimyasal özellikleri hakkında bilgi verir ve suyun kirlenme seviyesini gösterir.

  - Eksik Veri Oranı: Bu sütunda eksik veri yoktur (3276 satırda da değer var).
  
- Trihalomethanes (float64):

  - Açıklama: Su dezenfeksiyonu sırasında oluşan trihalometanlar (THM'ler), suyun içeriğinde bulunan potansiyel zararlı bileşiklerdir.
  
  - Eksik Veri Oranı: Bu sütunda da eksik veri var (%5 civarında), 3114 kayıt mevcut.

- Turbidity (float64):

  - Açıklama: Su bulanıklığı, suda bulunan askıda katı maddelerin yoğunluğunu gösterir. Yüksek bulanıklık, suyun kalitesiz olduğu anlamına gelebilir.
  
  - Eksik Veri Oranı: Bu sütunda eksik veri yoktur (3276 satırda da değer var).

- Potability (int64):

  - Açıklama: Bu sütun, suyun içme suyu olarak uygun olup olmadığını belirten bir etiket olabilir. Bu genellikle 0 (içilemez) veya 1 (içilebilir) gibi ikili bir değişkenle ifade edilir.

  - Eksik Veri Oranı: Bu sütunda eksik veri yoktur (3276 satırda da değer var).
 

Fitting 5 folds for each of 12 candidates, totalling 60 fits
En İyi Tunelenmiş Parametreler: {'C': 1, 'gamma': 'auto', 'kernel': 'rbf'}
Train Doğruluğu (Tunelenmiş SVM): 0.7235837685817598
Test Doğruluğu (Tunelenmiş SVM): 0.6982343499197432
Train Hata Oranı (Tunelenmiş SVM): 0.27641623141824023
Test Hata Oranı (Tunelenmiş SVM): 0.3017656500802568



Fitting 5 folds for each of 2187 candidates, totalling 10935 fits
En İyi Tunelenmiş Parametreler: {'colsample_bytree': 1.0, 'gamma': 0, 'learning_rate': 0.05, 'max_depth': 7, 'min_child_weight': 1, 'n_estimators': 50, 'subsample': 1.0}
Test Doğruluğu (Tunelenmiş XGBoost): 0.6773675762439807
Train Doğruluğu (Tunelenmiş XGBoost): 0.7886701486540779
Test Hata Oranı (Tunelenmiş XGBoost): 0.3226324237560193
Train Hata Oranı (Tunelenmiş XGBoost): 0.21132985134592208



Veri analizi süreci, eksik veri analizi ile başlanmış ve MCAR (Missing Completely at Random) yöntemiyle verideki eksiklikler incelenmiştir. Bu süreçte, eksik verilere dair bir patern tespit edilmiştir. Sonrasında, eksik verilerin median yerine MICE (Multiple Imputation by Chained Equations) yöntemiyle impüte edilmesine karar verilmiştir.

Verideki çarpıklıkların düzeltilmesi için Box-Cox dönüşümü uygulanmıştır. Aykırı değer analizi ise Isolation Forest modeli ile gerçekleştirilmiş ve veri setindeki outlier’lar tespit edilmiştir.

Son olarak, modellerin başarısını ölçebilmek amacıyla, işlemler yapılmış ve yapılmamış veri setleri ayrı ayrı denenmiştir. Bu karşılaştırma, yapılan ön işleme adımlarının veri seti üzerindeki etkileri değerlendirmek amacıyla yapılmıştır.

