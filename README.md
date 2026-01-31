# 📱 Google Play Store Veri Analizi Projesi (2018)

Bu proje, 2018 yılına ait Google Play Store verilerini kullanarak Android uygulama pazarındaki trendleri, kullanıcı davranışlarını ve başarı kriterlerini veri bilimi teknikleriyle analiz etmeyi amaçlamaktadır.

🔗 **Projeyi ve Kodları İncelemek İçin:** 

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1WxYCVHUDWB0AI-5uryfF5hCdJBJJacKk?usp=sharing)

## 🎯 Projenin Amacı

Bu çalışmanın temel hedefleri şunlardır:

* En popüler ve en çok indirilen uygulama kategorilerini belirlemek.
* Kategorilere göre uygulamaların indirilme ve etkileşim (puan ve yorum) oranlarını incelemek.
* İndirme sayısı ile kullanıcı memnuniyeti arasındaki ilişkiyi analiz etmek.
* Ücretli ve ücretsiz uygulamaların kalite algısını karşılaştırmak.
* Hedef kitle seçiminin uygulama başarısı üzerindeki etkisini ölçmek.

---

## 🛠️ Veri Ön İşleme (Data Preprocessing)

Analiz öncesinde veri setinin doğruluğunu ve güvenilirliğini artırmak için aşağıdaki temizlik adımları uygulanmıştır:

* **Veri Temizliği:** Veri uyuşmazlıkları giderilmiş, eksik veriler (Null values) istatistiksel yöntemlerle ele alınmış veya temizlenmiştir.
* **Tekrarlayan Veriler:** Tekrarlayan veriler tespit edilerek veri setinden kaldırılmıştır.
* **Tip Dönüşümü:** `Installs` (İndirme) ve `Price` (Fiyat) gibi sayısal olması gereken ancak "string" formatında gelen değişkenler temizlenerek sayısal veri tiplerine dönüştürülmüştür.
* **Keşifçi Analiz (EDA):** Sayısal (numeric) değişkenlerin dağılım grafikleri ve kategorik değişkenlerin frekansları incelenmiştir.

---

## 📊 Analiz ve Bulgular

### 1. Kategori Bazlı İndirme ve Etkileşim Analizi

En çok indirilen kategoriler ile en çok etkileşime girilen (yorum yapılan ve puanlanan) kategoriler arasında farklar gözlemlenmiştir.

* **İndirme (Nicelik):** Oyun (Game) kategorisi indirme sayılarında liderdir.
* **Etkileşim (Nitelik):** İletişim (Communication) etkileşimde zirvededir.

  <img width="1189" height="690" alt="image" src="https://github.com/user-attachments/assets/17a8c27b-65f4-4113-b9ee-7da006a527e9" />
  <img width="1187" height="690" alt="image" src="https://github.com/user-attachments/assets/5178a2d7-249c-4a46-90f3-ba22a5e352cb" />

---

### 2. Puan ve Yorum İlişkisi (Güvenilirlik Analizi)

Veri seti üzerinde yapılan Scatter Plot incelemesi sonucunda uygulamalar dört ana grupta toplanmıştır:

1. **Düşük Puan & Düşük Yorum:** Başarısız ve kullanıcı tarafından beğenilmeyen uygulamalar.
2. **Orta Puan & Orta Yorum:** Standart performans gösteren uygulamalar.
3. **Yüksek Puan & Yüksek Yorum:** Geniş kitlelerce indirilmiş, kalitesi binlerce kullanıcı tarafından doğrulanmış **"Güvenilir"** uygulamalar.
4. **Yüksek Puan & Düşük Yorum (Aykırı Grup):** Bu gruptaki uygulamaların puanları 5.0 veya çok yüksektir ancak indirme sayıları çok düşüktür. Burada **"Küçük Örneklem Yanlılığı" (Small Sample Size Bias)** tespit edilmiştir. Puanlar, uygulamanın kalitesinden ziyade, çok az kişi (muhtemelen geliştiricinin çevresi) tarafından oylandığını gösterir.

  <img width="846" height="554" alt="image" src="https://github.com/user-attachments/assets/7d01b96e-b5bb-4a95-ba92-723c3639b2fd" />

---

### 3. Kategori Bazlı Puan Değerlendirmesi

* **Genel Memnuniyet:** Market genelinde medyan puan **4.0** üzerindedir, bu da kullanıcıların genel olarak uygulamalardan memnun olduğunu gösterir.
* **En Tutarlı Kategori (Events):** Düşük varyansı, yüksek medyan değeri ve az sayıda aykırı değeri ile "Events" kategorisi, kullanıcının aradığını bulduğu en başarılı kategoridir.
* **Yüksek Riskli Kategoriler:** *Tools, Finance, Family* gibi kategorilerde medyan puan yüksek olsa da, "Outlier" (aykırı değer) yoğunluğu çok fazladır. Bu kategorilerde çok kaliteli uygulamalarla birlikte çok sayıda "çöp" (kalitesiz/spam) uygulama bir arada bulunmaktadır.

  <img width="1589" height="790" alt="image" src="https://github.com/user-attachments/assets/46a267ac-6d04-45ce-ba05-eb11220b9d97" />

---

### 4. Ücret Politikasının Etkisi (Paid vs Free)

* **Kalite Algısı:** Analizler, insanların ücretli uygulamalardan daha memnun kaldığını göstermektedir.
* **İstatistiksel Fark:** Ücretli uygulamaların medyan puanı ücretsizlere göre daha yüksektir ve puan dağılım kutusu (Boxplot) daha yukarıdadır.
* **Çöp Uygulama Sorunu:** Ücretsiz uygulamalarda 1.0 puana kadar inen yoğun bir aykırı değer kümesi varken, ücretli uygulamalarda bu durum belirgin şekilde daha azdır.

  <img width="691" height="549" alt="image" src="https://github.com/user-attachments/assets/ebca4c60-7e09-4c90-bcf7-1da7d2221225" />

---

### 5. Hedef Kitle Etkisi (Content Rating)

* **Everyone (Herkes) Tuzağı:** En geniş kitleye hitap eden "Everyone" kategorisi, memnun edilmesi en zor gruptur. Bu nedenle puan dağılımı çok geniştir ve aykırı değer sayısı fazladır.
* **Özelleşmiş Kitle:** Hedef kitle daraldıkça (Teen, Mature 17+), puanlardaki tutarlılık artmaktadır. Kitle seçimi puan ortalamasını radikal şekilde değiştirmese de, puanın **tutarlılığını** ve kalitenin korunmasını doğrudan etkilemektedir.
* *Not: "Adults only 18+" kategorisi veri yetersizliği nedeniyle analiz dışı bırakılmıştır.*

  <img width="846" height="623" alt="image" src="https://github.com/user-attachments/assets/9352f5f7-d6f1-4b2c-bb55-1168522c6ff0" />


---

## 💡 Sonuç ve Çıkarımlar

Bu çalışma sonucunda, Android uygulama pazarında başarılı olmak isteyen geliştiriciler ve yatırımcılar için şu kritik çıkarımlar elde edilmiştir:

1. **İndirme Sayısı Tek Başına Başarı Değildir:** Yüksek indirme sayıları her zaman yüksek kullanıcı memnuniyeti anlamına gelmez. Gerçek başarı, yüksek indirme ile birlikte gelen yüksek yorum ve puan etkileşimidir.
2. **Niş Pazarların Gücü:** "Herkes" için uygulama geliştirmek yerine, belirli bir kitleye (Events, Education, Mature 17+) odaklanmak, rekabetin yarattığı "gürültüden" kurtulmayı ve daha sadık/memnun bir kullanıcı kitlesi oluşturmayı sağlar.
3. **Ücretli Uygulama Fırsatı:** Kullanıcılar kaliteli bir hizmet için ödeme yapmaya isteklidir. Ücretli uygulamalar, geliştiriciyi daha yüksek bir kalite standardına zorlamakta ve karşılığında daha yüksek kullanıcı memnuniyeti getirmektedir.
4. **Veri Aldatmacasına Dikkat:** Puanı 5.0 olan ancak indirme/yorum sayısı düşük olan uygulamalar istatistiksel olarak güvenilir değildir. Pazar analizi yapılırken "Review" ve "Installs" sayıları mutlaka bir filtre olarak kullanılmalıdır.
