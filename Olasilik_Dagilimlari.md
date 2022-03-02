# Veri Biliminde Kullanılan Olasılık Dağılımları

Bu yazıda, veri biliminde en çok kullanılan kesikli(ayrık) dağılımlardan bernoulli,binom ve poison olasılık dağılımlarını inceleyeceğiz. Örneklerimizi, kendi formül hesaplarımızdan sonra python ile de çözeceğiz. 

Öncelikle iki genel başlık olan sürekli ve kesikli olasılık dağılımlarından bahsetmemiz gerekir. Sürekli olasılık dağılımında bir aralık veya alan üzerinden olasılık belirtilirken, kesikli olasılık dağılımında tek bir nokta veya sonuç üzerinden olasılık belirtilebilir. Yazı-tura olayı kesikli olasılık için en bilinen örnektir. Görüldüğü üzere sonuç ya yazı ya da turadır ve olasıkları 1/2'dir. Sürekli olasılık dağılımınnda ise belirli bir aralıkta, fonksiyonun oluşturduğu eğri altında kalan alan üzerinden olasılık hesabı yapılır. Belirtilen değerler için toplam alan 1'e eşit olmalıdır. Alan hesabından dolayı integral kullanılır. Tek bir değer için integral sıfır olacağından, sabit bir değerde olasılığımız sıfır olacaktır. Normal olasılık dağılımı, sürekli olasılık dağılımları içinde en çok bilinen ve kullanılandır.

<br>

## Bernoulli Dağılımı

Olasılık deneyinde başarılı-başarısız, olumlu-olumsuz gibi iki olası sonuç varsa bu bernoulli dağılımına girer. Bir mahallenin sakinlerine evcil hayvan besleyip baslemedikleri sorulduğunda elde edeceğimiz cevap evet veya hayır olacaktır. Görüldüğü üzere iki sonuçlu olayımız bernouilli dağılımına örnektir. % 40 evet cevabı aldığımızda p değerimiz (Başarı Olasılığı)
0.4, q değerimiz ise (Başarısızlık Olasılığı) 0.6 olacaktır. (p+q=1) 

<br>

Başarı ve başarızlık sözcüklerini gerçek hayattaki şekilde düşünmememiz gerekir. Odaklandığımız sonuç bizim için başarı diye adlandırılır. Örneğin aşırı hız sonucunda oluşan trafik kazalarındaki ölüm olasılığı bizim için başarı değeri olacaktır.  

![ber_for](https://user-images.githubusercontent.com/81990839/156386412-d34fb2d6-0ce2-4cc0-af37-3653d7824ba8.PNG)

<br>

Formülümüzdeki x değeri, p(başarı) değeri hesabı için 1 iken, q(başarısızlık) da ise 0'dır. Verdiğimiz evcil hayvan örneği üzerinden q değerini fonksiyon kullanarak bulmak istersek;

q= 0.4^0 * (1-0.4)^(1-0) = 0.6 olacaktır.

<br>

````PYTHON
from scipy.stats import bernoulli

p= 0.4 

calculation=bernoulli(p)
q=calculation.pmf(k=0) 
print(q)
````

<br>

Kesikli olasılık dağılımının bir diğer adı, olasılık kütle fonksiyonudur. İngilizcesi probability mass function olarak geçer. Kodumuzda yer alan pmf, ingilizcedeki kullanımın baş harfleridir.

<br>

## Binom Dağılımı

Binom dağılımının, bernoullideki olayın n defa gerçekleşmiş hali diyebiliriz. Diğer bir söylemle, n bağımsız deneme sonucu x defa başarılı olma olasılığı binom dağılımını ifade eder.

![binom_formul](https://user-images.githubusercontent.com/81990839/156424690-af24083b-45f2-4f96-b051-9a442662583d.PNG)

<br>

Bir örnek üzerinden açıklamamıza devam edelim. Bir madeni para 4 kere atılıyor ve 2 kere yazı gelme olasılığını öğrenmek istiyorsak, bu binom dağılımının konusuna girer. Formülümüzde değerlerimizi yerlerine koyarsak;

f(2;4,0.5) = 0.375 olacak şekilde sonucumuza ulaşırız.

````PYTHON
from scipy.stats import binom

p=0.5
n=4
x=2
calculation=binom(n,p)
probability=calculation.pmf(x)
print(probability)
````

<br>

## Poisson Dağılımı

Belirli bir zaman aralığında nadiren rastlanan olayların olasılıklarını hesaplamak için kullanılır. Örneğin kullandığımız akıllı telefonumuzun yılda ortalama 2 defa arızalanmasını poisson dağılımı ile ifade edebiliriz. 

![poisson_formül](https://user-images.githubusercontent.com/81990839/156432791-74f2908a-ac38-4b50-a57f-693b6bb1a0d6.PNG)

<br>

Yukarıda verdiğimiz örnek üzerinden telefonumuzun yılda 4 kez bozulma olasılığını hesaplayalım. Lambda değerimizin 2 olduğunu belirtelim. x ise 4'tür. Buradan;

f(4,2)=0.09 değerini buluruz. Yani telefonumuzun verdiğimiz koşul altında yılda 4 kere bozulma olasılığı yüzde 9'dur.

````PYTHON
from scipy.stats import poisson

lambda_ = 2
x=4
calculation=poisson(mu=lambda_)
probability=calculation.pmf(x)
print(probability)
````

<br>

[Patika.dev için tıklayınız](https://app.patika.dev/moduller/temel-matematik/proje)








