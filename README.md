# RSUAlgoritmasi
Secure-RNG (Hashed-LCG)
SHA-256 ile güçlendirilmiş rastgele sayı üreteci.

Proje Hakkında
Bu proje, deterministik bilgisayar sistemlerinde güvenli rastgele sayı üretme problemini ele alır. Standart üreteçlerin aksine, bu algoritma matematiksel bir formülü kriptografik bir hash fonksiyonu ile birleştirerek tahmin edilebilirliği ortadan kaldırır.

Teknik Analiz ve Güvenlik Mimarisi
Projenin güvenlik katmanları şu şekildedir:

1. Dinamik Tohumlama (Hybrid Seeding)

Sistem sadece statik bir anahtar kullanmaz. anahtar_kelime + time.time_ns() formülü ile kullanıcı girdisi yüksek çözünürlüklü zaman damgasıyla karıştırılır. Bu, aynı anahtar girilse bile her saniye farklı bir başlangıç (seed) noktası oluşturur.

2. Matematiksel Üretim (LCG)

Üretim motoru olarak Linear Congruential Generator kullanılır.

$$X_{n+1} = (a \cdot X_n + c) \pmod m$$ Burada kullanılan a, c ve m değerleri dünya genelinde kabul görmüş güvenli parametrelerdir.

3. Kriptografik Maskeleme (SHA-256 Layer)

Bu projenin en önemli güvenlik özelliği, LCG çıktılarının doğrudan kullanıcıya sunulmamasıdır.

Doğrusallık Kırılması: LCG'nin matematiksel düzeni, SHA-256 hash fonksiyonu ile kaotik bir hale getirilir.

Tek Yönlü Güvenlik: Hash fonksiyonu tek yönlü (one-way) olduğu için, üretilen sayıdan algoritmanın iç durumuna geri dönmek imkansızdır.

Örnek Çıktı ve Dağılım
Algoritma, sayıları 0-1000 aralığına Uniform Distribution (Düzgün Dağılım) ilkesine göre yayar. Terminal üzerinden yıldız grafiği ile görselleştirme sağlanmaktadır:

Plaintext
Sayı 01:  919 | ************************************

Sayı 02:  809 | ********************************

Sayı 03:  547 | *********************

Kurulum
Dosyayı indirin: main.py

Çalıştırın: python main.py

Bir anahtar kelime girin ve rastgeleliği gözlemleyin.
