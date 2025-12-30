# RSUAlgoritmasi
Klasik bilgisayar bilimlerinde kullanılan Linear Congruential Generator (LCG) algoritmasını, modern SHA-256 özetleme (hashing) fonksiyonu ile birleştirerek daha güvenli bir rastgele sayı üretim mekanizması sunar.

Neden "Hashed-LCG"?

Standart LCG algoritmaları X 
n+1
​	
 =(aX 
n
​	
 +c)modm formülüne dayanır. Bu formül hızlıdır ancak birkaç çıktı gözlemlendikten sonra bir sonraki sayının tahmin edilmesi kolaydır. Bu projede:

Her üretim adımında elde edilen değer SHA-256 ile maskelenir.

Hash fonksiyonlarının tek yönlü (one-way) olma özelliği sayesinde, üretilen sayıdan algoritmanın iç durumuna (internal state) ulaşmak matematiksel olarak imkansızdır.

Seed (Tohum) oluşturulurken sistem zamanı (nanosaniye) ve kullanıcıdan alınan benzersiz metin karıştırılarak entropi artırılır.

Özellikler
Hibrit Mimari: Matematiksel hız ve kriptografik güvenliğin birleşimi.

Görsel Analiz: Üretilen sayıların dağılımını terminal üzerinde yıldız grafiği ile görselleştirme.

İstatistiksel Rapor: En büyük, en küçük ve ortalama değer hesaplama.

Yüksek Entropi: time.time_ns() ve kullanıcı girdisi ile güçlendirilmiş başlangıç değeri.

 Kurulum ve Kullanım
Bu depoyu klonlayın:

Bash
git clone https://github.com/kullaniciadi/secure-rng.git
Proje dizinine gidin:

Bash
cd secure-rng
Algoritmayı çalıştırın:

Bash
python main.py
 Algoritma Akış Şeması
Girdi: Kullanıcıdan bir anahtar kelime alınır.

Tohumlama: Anahtar kelime + Zaman damgası → SHA-256 → Başlangıç Seed'i.

İterasyon: LCG formülü ile yeni bir geçici değer üretilir.

Güvenlik Katmanı: Geçici değer SHA-256'dan geçirilir.

Çıktı: Hash değerinin mod alınmış hali kullanıcıya sunulur ve görselleştirilir.
