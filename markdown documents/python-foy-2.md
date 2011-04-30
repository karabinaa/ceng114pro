## LABORATUVAR ÇALIŞMASI 2 - Değişkenler, Veri Girişi, Çevre & Alan Hesapları 

### Bu Çalışmanın Amacı

Bu çalışmadaki amacımız; değişken tanımlama, operatörler, veri girişi, çevre & alan hesapları ve 'doctest' kullanımı konularında öğrendiklerimizi pekiştirmektir.

### Değişken Tanımlama

"**Değişken**" i, bir niceliğin depolanabileceği bir yer, alan olarak tanımlayabiliriz. Değişkenler, içlerinde bir **karakter dizisi** (örneğin isminiz) bulundurabiliceği gibi bir **tamsayı** (örneğin yaşınız) ya da **ondalıklı sayı** da
(örneğin boyunuz) bulundurabilirler. Değişkenlerin türleri de içlerinde bulundurdukları bu değerlere göre değişmektedir. Örneğin, Python yorumlayıcısını etkileşimli biçimde kullanarak, ismi "Emre", yaşı 23 ve boyu 1.83 olan bir kişinin bu bilgilerini saklamak üzere üç ayrı değişken tanımlayalım:

~~~~{.python}
>>> isim = "Emre"
>>> yas = 23
>>> boy = 1.83
~~~~

Şimdi bu değişkenlerin her birinde ilgili kişiye ait bazı değerler tutulmakta olup bunlardan birisi karakter dizisi şeklinde olan isim ("**isim**" değişkeni içerisinde), diğeri tamsayı şeklinde olan yaş ("**yas**" değişkeni içerisinde), bir diğeri ise ondalıklı sayı şeklinde olan boy ("**boy**" değişkeni içerisinde) bilgilerdir.

Matematikte kullandığımız karmaşık sayıları da Python' da tanımlayabiliriz. "5 + 12j" ve "0 - 3j" sayılarının tanımlanmasına ait örnek, aşağıdadır:

~~~~{.python}
>>> a = 5 + 12j
>>> b = -3j
~~~~

Python' da bir değişkenin, ya da bir değişkene atanabilecek bir değerin türünü öğrenmek için "**type()**" fonksiyonu kullanılır. Türü öğrenilmek istenen değişken ya da değer, bu fonksiyonun parantezleri içerisine yazılır.

Yukarıda vermiş olduğumuz tanımlama örnekleri üzerinden (Python Shell penceresini kapatmadan) devam edecek olursak, "**type()**" fonksiyonunun kullanımı ile ilgili şu örneği verebiliriz:

~~~~{.python}
>>> type(isim)
<type 'str'>
>>> type(yas)
<type 'int'>
>>> type(boy)
<type 'float'>
>>> type(a)
<type 'complex'>
~~~~

Örnekte görüldüğü gibi "**type()**" fonksiyonu bize değişkenlerin türlerini vermektedir. Burada **str** "karakter dizisi" ne, **int** "tamsayı" ya, **float** "ondalıklı sayı" ya, **complex** ise "karmaşık sayı" ya karşılık gelmektedir.

**type()** fonksiyonu ile değişkenlerin türlerini öğrenebileceğimiz gibi, **bu değişkenler içerisine atılacak olan değerlerin türlerini** de öğrenmemiz mümkündür. Python Shell ekranını kapatmadan yukarıdaki örneğe devam ederek bunu görebiliriz.

~~~~{.python}
>>> type("Alper")
<type 'str'>
>>> type(12)
<type 'int'>
>>> type(1.58)
<type 'float'>
>>> type(-6 - 7j)
<type 'complex'>
~~~~

Bütün bunları göz önünde bulundurursak "Python, pek çok programlama dilinden farklı olarak, **değişkenlerin türlerini, kendilerine atanan değerin türüne bakarak, atama işlemi sırasında ___dinamik olarak___ belirler.** diyebiliriz.

İçerisinde değer bulunan değişkenleri ise programda yer alan başka fonksiyonlarla / komutlarla birlikte kullanabiliriz. Örnek :

~~~~{.python}
>>> universite = "Ondokuz Mayıs Üniversitesi"
>>> il_trafik_kodu = 55
>>> print universite
Ondokuz Mayıs Üniversitesi
>>> print il_trafik_kodu
55
~~~~

### Operatörler 

Python' da, "**bool**" ismi verilen bir değişken türü vardır. **bool** türündeki bir değişkenin türü ya "**True** (doğru)", ya da "**False** (yanlış)" olabilir. Yanındaki kriter sağlandığında (değeri **True** olduğunda) kendi kapsamındaki kod parçalarının çalıştırılmasına müsaade ederken kriter sağlanmadığında (değeri **False** olduğunda) buna müsaade etmeyen if ve while yapılarında (İlerleyen konularda ele alınacaktır.) **bool** türündeki ifadeler sıklıkla kullanılırlar.

Bu operatörler (+, -, *, /, % gibi) sonuç olarak **sayı** ya da **karakter dizisi** döndürürken bazıları da (==, !=, <, >, <=, >= gibi) **bool** tipinde değerler döndürürler.

"**and**", "**or**" ve "**xor**" mantıksal operatörleri ise "True" ya da "False" olan ifadelerin arasında bulunarak **bağlaç** görevi görürler. Bu operatörlerden **and** ile **or** yazı ile yazılabildiği gibi, **and** operatörünü "**&**" işareti ile, **or** operatörü de "|" işaretleri ile göstermek de mümkündür. **xor** operatör ise sadece "^" işareti ile kullanılabilir. Bu bağlaçların döndürecekleri sonuç aşağıdaki tablodan yararlanılarak çıkarılabilir:

![foy2-resim1]

"**not**" operatörü ise kendisinden sonra gelen ifadenin doğruluk değerini değiştirerek **True** ise **False**, **False** ise **True** yapar:

~~~~{.python}
>>> 7 == 7
True
>>> not 7==7
~~~~

Diğer operatörlerin görevlerini hatırlayalım:

*+*  -> İki sayıyı ya da iki karakter dizisini birleştirir. Bir fonksiyon gibi işlemin sonucunu döndürür.

~~~~{.python}
>>> 3 + 9.0
12.0
>>> 'pyt' + 'hon'
'python'
~~~~

**-**	-> İki sayının farkını alır. Bir fonksiyon gibi işlemin sonucunu döndürür.

~~~~{.python}
>>> 8.74 - 19
-10.26
~~~~

***  -> İki sayıyı çarpar ya da bir karakter dizisini belirli bir sayıda tekrarlayarak arka arkaya ekler. Bir fonksiyon gibi işlemin sonucunu döndürür.

~~~~{.pyhton}
>>> 13 * 61
793
>>> 'ekim' * 4 
'ekimekimekimekim'
~~~~

*/* -> İki sayıyı böler ve **bölümü** hesaplar.Bölen ve bölünen tamsayı ise kalan ihmal edilir. Bölen ve bölünenden en az biri ondalıklı sayı ise bölme işlemi kalan üzerinden de devam eder ve ondalıklı bölme yapılır. Bir fonksiyon gibi işlemin sonucunu döndürür.

~~~~{.pyhton}
>>> 7 / 4
1
>>> 7 / 4.0 
1.75
~~~~

% -> İki sayıyı böler ve **kalan**ı hesaplar (Başka bir deyişe bir sayının diğerine göre **mod**unu hesaplar.) Bir fonksiyon gibi sonucunu döndürür.

~~~~{.python}
>>> 7 % 4 
3
>>> 7 % 4.0
3.0
~~~~

== -> iki ifadenin **eşitliğini** kontrol ederek **True** ya da **False** döndürür.

~~~~{.python}
>>> 8 == 9
False
>>> 7 == 'yedi'
False
>>> '19mayis' == '19mayis'
True
>>> 35 == 35.0
True
>>> 'apostrof' == "apostrof"
True
~~~~

!= -> İki ifadenin **farklılığını** kontrol ederek **True** ya da **False** döndürür.

~~~~{.python}
>>> 8 != 9
True
>>> 7 != 'yedi'
True
>>> '19mayis' != '19mayis'
False
>>> 35 != 35.0
False
>>> 'apostrof' != "apostrof"
False 
~~~~

**<** ~~~>~~~
