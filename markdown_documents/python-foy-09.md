## LABORATUVAR ÇALIŞMASI 9 - Dosyalar ve Modüller

### Bu Çalışmanın Amacı

Bu çalışmadaki amacımız, dosyalar ve modüller konularında öğrendikleriminizi pekiştirmektir.

### Hatırlatma

Bu föy, Windows işletim sistemi üzerinde hazırlandığı için bazı ekran görüntüleri ve klasör isimleri, diğer işletim sistemlerindekilerden farklı görünebilecektir. Örnek olarak verilen dosya ve klasör adreslerinde, kullanmakta olduğunuz işletim sistemini de göz önüne alarak gerekli değişiklikleri yapmanız gerekmektedir (İlerleyen sayfalarda, bazı noktalarda size bilgi verilmiştir.). **Python programlama dilini gerek Linux, gerekse Windows işletim sistemleri üzerinde kullanarak programlama yapabileceğinizi unutmayınız.**

### Dosya İşlemleri

Hazırladığımız bir programı çalıştırarak çeşitli veriler elde ettikten sonra bu verileri daha sonra tekrar kullanmak üzere **kalıcı** olarak saklama ihtiyacı duyabiliriz. Bilgisayarı kapatıp açtıktan sonra dahi verilerimizin kaybolmaması için onları **dosyalara** kaydederek sabit diskte saklamamız gerekir. Verileri dosyalara kaydetmek için dosyaya yazma işlemi, dosyaya kaydedilmiş verilere daha sonradan ulaşmak içinse dosyadan okuma işlemi yapmamız gerekmektedir.

### Dosyadan Okuma İşlemi

Python' da bir dosyayı okuyabilmek için **öncelikle açmak gerekir**. Dosyayı açmak içinse "**open**" fonksiyonu kullanılır. **open** fonksiyonu parametre olarak **dosya adresini** (dosya ismine kadar, 'C:\...\...\...\dosya.txt' gibi) alır, sonuç olaraksa bir **dosya nesnesi** döndürür.

Dosyadan okuma işlemleri, işte bu **dosya nesnesi** üzerinden yapılır. Örneğin, "sozcuk.txt" isminde bir metin dosyamız olsun ve içeriği aşağıdaki gibi olsun :
 
**aba**		
**abajur**	
**abanmak**	
**abanoz**	
**abartmak**	
**abide**	
**abiye**	
**abone**	

Bu dosyanın çalışma dizininde (Python Shell’ de iken Ctrl+O ile ulaştığımız dizinde) bulunduğunu düşünelim ve bu dosyadan satır satır okuma yaparak okunan kelimeleri alt alta ekrana yazdıran bir program hazırlayalım (Python Shell ekranında). **open** fonksiyonunun döndüreceği değeri içerisine atacağımız dosya nesnesine, “dosya girdisi (file input)” anlamında “**fin**” ismini verelim (Genelde bu isim verilir.):

~~~~{.python}
>>> fin = open('sozcuk.txt')
>>> for satir in fin:
	print satir

aba

abajur

...

abone
~~~~

Kodu bu şekilde yazdığımızda sözcüklerin ekrana birer satır arayla yazıldığını görürüz. Bunun nedeni, hem print komutunun her defasında yeni bir satıra yazması, hem de dosyadan okunan her bir sözcüğün sonunda, “Bir alt satıra geç.” anlamına gelen“\r\n” karakterlerinin bulunmasıdır. Metin dosyasında biz bu “\r\n” karakterlerini yazılı olarak görmeyiz, çünkü bu karakterlerin görevi zaten metnin bir alt satırdan devam edeceğini göstermektir. 

**aba\r\n**
**abajur\r\n**
**abanmak\r\n**
**abanoz\r\n**
**abartmak\r\n**
**abide\r\n**
**abiye\r\n**
**abone\r\n**

Eğer “sozcuk.txt” dosyasından bir şekilde bu “\r\n” karakterlerini yok edersek elde edeceğimiz yeni metin dosyasını açtığımızda göreceğimiz şey şu şekilde olacaktır:

abaabajurabanmakabanozabartmakabideabiyeabone

**İlave Bilgi:** "\n" bir alt satıra geçmek, "r" ise satırın başına gelmek için kullanılır. İkiabaabajurabanmakabanozabartmakabideabiyeabone
si beraber "\r\n" biçiminde kullanıldığında bu, "Bir alt satırın en başına git." anlamına gelir.

Ancak "**readline**" komutu ile okuma yaptıktan sonra "**\r\n**" karakterlerini atmak da mümkündür. Bunun içinse "**strip**" fonksiyonu kullanılır. Örnek kullanım aşağıdaki gibidir:

~~~~{.python}
>>> fin = open('sozcuk.txt')
>>> for satir in fin:
	arindirilmis_satir = satir.strip()
	print arindirilmis_satir

aba
abajur
abanmak
abanoz
abartmak
abide
abiye
abone
~~~~

"arindirilmis_satir" değişkeni içerisinde "**\r\n**" karakterlerinden arındırılmış sözcükler bulunduğu için ve **print** komutu her defasında yeni bir satırdan yazmaya başladığı için kelimeler arasında boş satırlar yer almayacaktır.

### Dosyaya Yazma İşlemi 

Python çalışma dizini içerisinde (Python Shell ekranı açıkken Ctrl+O ile görüntülediğimiz dizinde) “hedef.txt” adında bir dosya oluşturarak birinci satırına “Ondokuz Mayis Universitesi”, ikinci satırına “Muhendislik Fakultesi”, üçüncü satırına ise “Bilgisayar Muhendisligi Bolumu” yazdırarak kaydetmek için şu işlemleri yapmamız gerekir:

~~~~{.python}
>>> satir1 = 'Ondokuz Mayıs Universitesi\n'
>>> satir2 = 'Muhendislik Fakultesi\n'
>>> satir3 = 'Bilgisayar Muhendisligi Bolumu\n'
>>> fout = open('hedef.txt', 'w')
>>> fout.write(satir1)
>>> fout.write(satir2)
>>> fout.write(satir3)
>>> fout.close()
~~~~

Buradaki “**fout**” dosya nesnesini tutan değişken olup, dosya işlemlerinin yapılması için gereklidir. “**fout**” yerine istediğimiz herhangi bir ismi de verebiliriz ancak bir kodlama standardı oluşturmak adına “fout” adını kullanmak daha uygun olacaktır. Karakter dizilerinin sonlarındaki “**\n**” karakterleri, metin dosyasında bir alt satıra geçmek içindir (Tek başına “\n” de bir alt satırın en başına geçmek için yeterlidir.). “**open**” fonksiyonu ile dosyayı **yazma işlemi için** (‘**w**’ parametresi yazma işlemini ifade eder.)oluşturduktan (ilk parametrede verilen dosya ismi ile) sonra bu fonksiyonun döndürdüğü nesneyi “**fout**” değişkenine atarız. Bu nesne üzerinde “**write**” fonksiyonunu kullanarak istediğimiz karakter dizilerini dosyaya yazdırırız. Son olarak ise “close” fonksiyonu ile dosya nesnesinin görevini sonlandırırız (Bunu yapmazsak veriler dosyaya kaydedilmez [Ancak Python’ u kapattığımızda kaydedilir.] ve çeşitli sorunlarla karşılaşabiliriz.). Oluşan dosyayı açtığımızda yazılanları görebiliriz (Windows’ tan alınmış bir örnek ekran görüntüsü):

![](foy9-resim1.png)

Dosyaya yazdığımız veriler **karakter dizisi olmak zorundadır**. Bu nedenle, herhangi bir işlemin sonucunda elde ettiğimiz sayı değerlerini dosyaya yazdırmamız gerektiğinde, öncelikle “**str()**” fonksiyonunu kullanarak bunları karakter dizisine dönüştürmeliyiz:

~~~~{.python}
...
>>> x = 0.362
>>> type(X)
<tpye 'float'>
>>> fout.write(str(x))
...
~~~~





