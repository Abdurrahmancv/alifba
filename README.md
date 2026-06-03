# Evrensel İslami Elifbe ve Klavye Standardı

**Yazar:** Abdurrahman Çevik  
**Konum:** Mardin, Artuklu  
**E-posta:** abdurrahmancevik2005@gmail.com

---

## 1. VİZYONUMUZ: "Adem'in Oğulları İlmi Zeminde Buluşmalı"

Bu proje, küresel savaşların ve politik kutuplaşmaların anlamsızlığına inanan; insanlığın dürüstlük, samimiyet ve iyi niyetle ortak bir ilmi zeminde buluşmasını hedefleyen evrensel bir medeniyet hareketidir. Bizi birleştiren en güçlü unsur İslam medeniyetidir.

Dünyadaki halklar kendi dillerinin özgün seslerini koruyarak, dijital dünyada ortak bir elifbe çatısı altında birleşebilirler. Bu sistem, dilleri aslına sadık kalarak, kıraati kolaylaştıran bir "orta yol" çözümüdür.

### Neden Elifbe?

Bu evrensel nizamda nihai hedefimiz, tüm dilleri bu ortak elifbe çatısı altında birleştirmektir. Bu noktada akla şu sual gelebilir: *"Neden Çin, Japon, Hind yazıları veya Yunan, Latin, Kiril alfabeleri değil de Arap harfleri?"*

* **Mukkaddes Sebep:** Arapça, bilhassa Fushâ (Fasih Arapça), vahy-i ilahinin nazil olduğu Kur'an dilidir. Her bir İslam neferinin zihnen, ruhen ve ilmen hakim olması gereken, İslam alemini manen birbirine bağlayan yegane ortak bağdır.
* **Teknik Sebep:** Doğu Asya (Çin, Japon vb.) yazı sistemleri kendine mahsus olup öğrenmesi, dijitalleştirilmesi ve yazması zordur. Arap elifbesi ise yeryüzündeki tüm alfabelerin ortak atası kabul edilen Fenike harflerine morfolojik olarak en sadık kalan, karakter yapısı itibarıyla en yaygın, akışkan ve pratik geometrik forma sahip yazı sistemidir.

Bu yönüyle Elifbe, insanlığın ortak yazı mirasını uzun vadede taşımak adına en makul "orta yol" prensipidir.


---
## 2. MEVCUT SİSTEMİN ZAAFİYETİ: Unicode ve Data İsrafı

Unicode standartlarında, Elifbe tabanlı diller (Arapça, Farsça, Türkçe, Kürtçe, Urduca..) ekrana basılırken hantal bir yapı kullanılır:

1. **0x06 Sırası (Standard Kodlar):** Harflerin sadece ham karakter değerini tutar.
2. **Presentation Forms (Sunum Biçimleri / 0xFB50 - 0xFEFF Sırası):** Bilgisayarın font motoru harfin başta, ortada, sonda veya yalın olduğunu hesaplaması için yüzlerce gereksiz alan işgal eder.

Bu durum veritabanlarında yer kaplar ve OpenType mimarları için hantal yazılım algoritmaları doğurur. Son yüzyılda süregelen "Arap harflerinde her harfin 4 farklı yazılış formu vardır, öğrenmesi zordur" iddiası bir yanılgıdan ibarettir.

*Yazının estetik görünmesi için kullanılan diğer formlar (ortadaki, sondaki, alt alta gelen ve birbirinin içine geçen estetik harf ligatürleri) bu sırada yer alabilir. Tavsiyemizin tatbik edilmesiyle estetik formlar, mevcut ayrılan alandan çok daha az yer kaplar.*

---
## 3. MİMARİ ÇÖZÜM: Harflerde En Fazla 2 Form Vardır

Tavsiye ettiğimiz bu ortografik nizam ile, bilgisayarların font işleme mantığını kökten sadeleştirerek, elifbenin matematikal bir tasarrufa sahip olduğunu isbatlıyoruz.

Mevcut Unicode "Sunum Biçimleri" (Presentation Forms) cetvellerindeki hantallık tamamen tasfiye edilmelidir. Bizim sistemimizde her harf veri tabanında tek bir temel biçim (glif) olarak yer alır. Sadece bazı harflerin kelime sonunda bir "yalın/bitiş" varyasyonu bulunur:

* **Bağlantılı Harfler (Tek Form + Süslü Varyasyon):** Özünde tek bir şekli vardır; o da kendinden sonraki harfe akmaya hazır olan bağlantılı (baştaki) formdur. Sadece kelime sonlarında estetik olarak nihayete erdirilirler (süslenirler).
* **Bağlantısız Harfler (Tamamen Tek Form):** Elif (ا), Dal (د), Zel (ذ), Ra (ر), Ze (ز), Je (ژ), Vav (و) gibi harfler kendinden sonrakiyle zaten birleşmezler. Kelimenin neresinde olurlarsa olsunlar, hiçbir morfolojik varyasyona (süse) ihtiyaç duymadan tamamen tek bir formla temsil edilirler. Sadece arkasındaki harf onlara bağlanabilir.

*Harflerde 4 form yoktur, elifbede mesele sadece harfin kendinden sonraki harfe bağlanıp bağlanmamasıdır.*

Unicode cetvelindeki tüm "Arapça Sunum Biçimleri" (Presentation Forms) reform edilmeli, harfler **baştaki form** ve **yalın form** olmak üzere sadece 2 Unicode karaktere indirilmelidir.

### Unicode Cetveli (Bağlantılı/Bağlantısız Formlar)

Harfler yer aldığı **0x06** Unicode tablosunda, doğrudan bağlantılı formuyla **(Mesela: بـ)** tutulmalıdır. Yalın hali ayriyeten bulunan harflere sadece bir kod yeri daha ayrılır **(Mesela: ب)**. Bu sayede, klavyede yazı yazarken arka planda kompleks AI veya font işleme otomasyonları çalışmaz. İmla mantığı şu standarda tabidir:

* Kullanıcı klavyede bir harfe bastığı an, ekranda beliren glif doğrudan kendinden sonrakiyle birleşmeye hazır olan tek asli formdur (بـ). Karakterler yazıldıkça tabii olarak birbirinin elini tutar.
* Tıpkı mobil klavyelerin cümle başlarında harfleri otomatik olarak büyük harfe dönüştürmesi gibi; kullanıcı bir kelimeyi bitirip boşluk (Space) tuşuna bastığında veya harf olmayan bir karakter girdiğinde, yazılım algoritması kelimenin son harfini (eğer bir yalın varyasyonu varsa) otomatik olarak süslü/yalın formuna dönüştürür *(Optional Capitalization)*.
* Kullanıcı boşluk bıraktıktan sonra silme tuşuna (Backspace) bassa dahi, o harf yalın formunda kalır. Sırayla Lam ve Elif yazınca lamelif olur ve bu sayede silince tek seferde silinir. İkinci hali olmayıp birleşen harften hemen sonra virgül eklediğimizde harf sondaki halini alır, ve sildiğimizde harf tek bir karaktere dönüştüğü için tek seferde silinir.
* Kullanıcı otomatik boşluk fonksiyonunu beklemek istemezse veya bir kısaltma/istisna yazıyorsa; kuyruklu ve süslü biten harflerin (ج, ح, خ, س, ش, ص, ض, ع, غ, ق, ن, ه, ي gibi) bu varyasyonlarına standart klavye usulündeki gibi Shift tuşu kombinasyonuyla doğrudan da ulaşabilir.

* Kendinden sonraki harfle birleşen diğer `ب`, `ت`, `ث`, `ط`, `ظ`, `ف`, `ك`, `ل` gibi harflerin hemen ucuna halihazırda klavyede var olan Arapça virgül **(،)** işareti geldiğinde, harf zaten kendi yalın görüntüsüne tabii olarak kavuşacaktır. **(Mesela: `بـ` + `،` = `ب`)**

### Geleneksel Unicode Mantığı vs. Alifba Mantığı
- **Mevcut Unicode:** Be harfi = 5 farklı kod / 4 farklı karakter. (Hantal)
- **Alifba:** Be harfi = Sadece 1 temel Kod (بـ) ve 1 adet final varyasyon Kodu. (İkinci varyasyonu yoksa tek kod)

*Aslında bugün teklif ettiğimiz bu usul, matbaanın dünyaya ilk yayıldığı zaman kullanılabilir ve Elifbe dijital çağa yıllar evvelinden girebilirdi. Ancak o devirde, dünyevi menfaatini ve sosyo-ekonomik gücünü korumak isteyen statükocu bir kesim yüzünden bu imkan kısıtlandı. Matbaayı getirenler ise hattatlık tekelinin etkisiyle, harflerin fıtri ve akıcı tabiatini katlederek onları sanki 4 ayrı parçaymış gibi hantal ve suni bir standarda mahkum ettiler. Keza çirkin ve okunaksız rika hattı, matbaanın geç gelmesiyle ortaya çıkmıştır. Bugün Unicode'un omuzlarında taşıdığı bu kambur, asırlar evvel üretilen o çıkarcı refleksin dijital dünyaya sızmış bir kalıntısıdır.*



### Keşide (ـ) Kullanımı

Unicode cetvelinde yer kaplayan Tatweel (ـ) karakteri tamamen sistemden kaldırılmalıdır.

* Bunun yerine klavyedeki standart nokta (.) kullanılacaktır. Nokta, birleşmeye hazır harflerin arasında bulunduğunda, zaten keşide görüntüsüne tabii olarak kavuşacaktır.


Bu sistemde harf formları için işlemciye hiçbir hesaplama yaptırılmaz; hafızada sadece **Birleşen Kod** ve **Yalın Kod** olarak iki sabit değer saklanır, bazı harfler ise sadece **Yalın Koda** sahiptir. Harflerin ikinci formu font motorunun algoritmasıyla değil, harfin veri tabanındaki statik koduyla (default state) sağlanır.

---
## 4. DİLLERİN SES İHTİYAÇLARINA GÖRE TASARRUF

İslam coğrafyasındaki dillerin dijital imla karmaşasını çözen tasarruf hamleleri yapılmıştır.





### Okutucu Unsurlar

* Elif `ا` harfi Türkçede "a" sesi verir. Kürtçede (Elif) aynı sesi verir.
* Ye `ی` harfi Türkçede "ê/î" sesi verir. Kürtçede (Yê) aynı sesi verir.
* Vav `و` harfi Türkçede "o/u" sesi verir, ancak bazan "v" sesi için de kullanılmıştır. Kürtçede (Waw) "ô/û" sesini verir.

*Türkçede ince harf bulunan kelimelerde Elif uzun "e", Vav uzun "ö/ü" gibi, kalın harf bulunan kelimelerde Ye uzun "a/ı" gibi okunur.*

Kaidenin netleşmesi için bazı emsal aşağıda ifade edilmiştir:

| Harf | Normal Okunuş | Yumuşak Okunuş | Yumuşama Sebebi |
| --- | --- | --- | --- |
| **Elif ğa (ا)** | **طاش** (Taş) | **سَكسان** (Seksen) | İnce Kâf (ك) |
| **Ye ğe/yi (ی)** | **گیجه** (Gece) <br> **فیل** (Fil) | **مُصطَفی** (Mustafa) <br> **صاری** (Sarı) | Kalın Sad (ص) <br> Kalın Kaf (ق) |
| **Vav wo/wu (و)** | **توپراق** (Toprak) <br> **موز** (Muz) | **كوشه** (Kôşe) <br> **حكومت** (Hükûmet) | İnce Kâf (ك) |

### Harekeler
Türkçedeki ses geçişleri (okutucu uyumlarını) ek bir karaktere ihtiyaç duymadan, harfin kendi tabiatıyla (kalınlık-incelik mevzuuyla) tabii olarak çözmesidir. Temel harekelerin asli ses karşılıkları şöyledir:

* Üstün `ـَ` harekesi Türkçede "e" sesini (Azerbaycandaki açık *ə* gibi) verir. Kürtçede (Fethe) aynı sesi verir.
* Esre `ـِ` harekesi Türkçede "i" sesini verir. Kürtçede (Kesre) aynı sesi verir.
* Ötre `ـُ` harekesi Türkçede "ö/ü" sesi verir, ancak tanzimat devrinde, Türkçe asıllı kelimelerde ötre yerine vav kullanılmıştır. Kürtçede (Zemme) "ue/ui" sesini verir.

*Türkçede kalın harf veya uzatma harfi (Elif/Vav) bulunan kelimelerde Üstün kısa "a", Esre kısa "ı", Ötre kısa "o/u" gibi okunur.*

| Hareke | Normal Okunuş | Yumuşak Okunuş | Kalınlaşma Sebebi |
| :--- | :--- | :--- | :--- |
| **Üstün ğe (ـَ)** | **سَحَر** (Seher) | **یَهودی** (Yehudi) | Uzun Vav (و) |
| **Kesre ğı/ği (ـِ)** | **بِر** (Bir) | **قِزِل** (Kizil) | Kalın Kaf (ق) |
| **Ötre wö/wü (ـُ)** | **عُرف** (Örf) <br> **حُكم** (Hükm) | **عُثمان** (Ösman) <br> **عُنصُر** (Ünsür) | Uzun Elif (ا) <br> Kalın Sad (ص) |

Bu tabii fonetik esneklik sayesinde, bilgisayarın metin okuma (TTS) motorları, harfin kalınlık-incelik sınıfına bakarak harekenin ses değerini yapay zekaya ihtiyaç duymadan, saf matematikal bir algoritmayla doğru telaffuz edebilir.

*Harekelerin kalınlaşması veya okutucu harflerin incelmesi bir kaide değildir, kiraatin tabii akışının neticesidir.*



### Ötrenin Harf Formu به كࢫردي ضمه \ تࢫركجه اࢫتره

**Okutucu Harf Çözümü:** Klasik imlada *ötre* telaffuzu, kiraat talebeleri için harf ile ifade edilerek Unicode standardındaki **"ࢫ"** karakteri sisteme dahil edilmiştir. Mesela: **بࢫل** (böl), **بول** (bul).
* Kalın okutuculu Türkçe asıllı kelimelerde u sesini ayırmak için ötre kullanılabilir: **قࢫل** (kul), **قول** (kol).
* İnce okutuculu Türkçe asıllı kelimelerde ö sesini ayırmak için vav kullanılabilir: **گࢫل** (gül), **گول** (göl).

Aşağıda bazı misaller verilmiştir:

**Türkçe Misaller:**

* Vav ile اوردی (ordu), سور (sur), كوشه (köşe), كوفی (küfi).
* Ötre ile عࢫمر (ömer), اࢫست (üst), نࢫقطه (nokta), طࢫغرࢫل (tuğrul).

**Misalên Kurdî:**

* Waw ile اوستا(ôste), شࢫور(şûr), دوست(dôst), هࢫور(hûr).
* Zemme ile خࢫستن(xuestin), خࢫين(xuîn), خࢫار(xuar), گࢫه(guh), دࢫهو(dohô).

### Jeyn (ژ) Harfinin Tasfiyesi

* Türkçenin yapısında Je (ژ) ünsüzü yoktur. Türkçede bu harfi barındırmak yerine, saf dudak-diş ünsüzü olan **"ڤ"** (V) harfi sabitlenmiştir. Klavye, Kürtçe gibi diller için ژ harfini barındırır. Jeyn harfi Kürtçe gibi İrani diller için zaruri olsa da, Türkçede bu ses ج ve bazan ز\ش harfleriyle ifade edilebilir. (Mesela: شارز\شارج "şarj", جاله "jale", جندارمه "jandarma") Lakin ڤ sesi, Türkçe için elzemdir.
* Eski Türkçe بار (var), بیر (ver) ve بول (ol) kelimeleri, Oğuzcada و harfiyle ifade edilip, وار ve ویر ve وول şeklinde imla edilmiştir. Vav harfi Türkçenin asli harflerinden biridir ancak V sesini ifade etmek için yeterli değildir, bu yüzden bu kelimeler günümüz Türkçesinde ڤار ve ڤىر ve اول şeklinde imla edilebilir. Asli sesi "v" olan sesler için: تله‌ڤيزيون "televizyon", باغچڤان "bahçıvan". Asli sesi "û" olan sesler yine و ile yazılır: وادي "vadi", وطن "vatan".

### İmale Çözümü

* İmale hem Kürtçe'de hem de Türkçe'de bulunan bir okutucudur ve ی (ye) harfiyle ifade edilir.
* Ye Harfi Türkçede `kesre "ı/i"`, `imale "e"` ve asli `ye "y"` sesi için kullanılır. Bu üç okutucuyu imlada ayırmak maksadıyla kesre için يـ ى formu, imale için ىـ ى formu ve asli ye için يـ ي formu kullanılabilir: ييل(yıl), قير(kır), كير(kir), اخلاقى(ahlakı), اخلاقي(ahlaki), ڤىرش(veriş), دىيش(deyiş), گىج(geç), گىجه(gece), اىرش(eriş), اىركن(erken), دعوى(dava), معنى(mana), هوى(heva), فتوى(fetva), موسى(musa), عيسى(isa), مصطفى(mustafa).

### Havayla Okunan He (ه) Formu

**Urduca ve Kürtçe Aspirasyon (Soluklaşma) Çözümü:** Urducadaki "Du Çeşm He" (ھ) harfine ihtiyaç yoktur. Kelimelerde aspirasyonu (hava üfleyerek okumayı) göstermek için sıradan **"ه"** harfi tek başına yeterlidir.

* Kürtçede `پ` `چ` `ت` `ك` harfleri bazı kelimelerde nefes vererek okunur. Mesela **چل** kelimesi "yarasa" manasına gelirken, چـ sesi nefesle okunduğunda "kırk" manasına gelir.
* Nefesle okunan sesi ayırt etmek için, *Du Çeşm He* ile **چهـ** şeklindeki gibi yazıldığında, normal yazılan **چل** "yarasa" kelimesiyle, "kırk" manasındaki **چهل** kelimesini ayırmış oluruz.
* Kürtçe'de nefes vermeden okunan *Kêr* (Kâr) kelimesi **کێر** şeklinde yazılırken; nefes vererek okunan *Kêr* (Bıçak) kelimesi **کهێر** şeklinde yazılarak anlam karmaşası kökten çözülmüştür.
* Du çeşm he harfini, nefes vererek okunan her kelimede kullanmaktan ziyade, kelimenin aslında ه bulunan veya birbirinden bu şekilde ayrılan kelimeler için kullanabiliriz: **تࢫ**(sen), **تهࢫ**(hiç), **كىر**(kâr), **كهىر**(bıçak), **تي**(sen ..eceksin), **تهي**(susamış).

* Urduca "Sert Te" (ٹ) harfine de ihtiyaç yoktur. Hlihazırda bulunan Te (ت), Havalı Te (ته), The (ث), Tı (ط) formları, Urducadaki sesleri tam olarak karşılayabilmektedir.


### Hemze (ء) İçeren Kelimeler

* Kürtçe **شئر** "aslan", **مئڤان** "misafir", **بئڤل** "burun", **بئن** "koku", **تئن** "hararet" kelimeleri yöreye göre *شىهر \ شىر* (şêr), *مىهڤان \ مىڤان* (mêvan), *بىهڤل \ بىڤل* (bêvil), *بىهن \ بىن* (bên), *تىهن \ تىن* (tên) şeklinde okunur. Bu varyasyona benzeyen, Arapça فهم (fehim) ve ذهن (zihin)'den gelen **فئم** ve **ذئن** kelimeleri zamanla Kürtçeleşerek فىهم \ فىم \ فَعم ve ذىهن \ ذىن şeklinde okunmaya başlamıştır.
* Kürtçe **چأڤ** "göz" ve  **بأجان** "patlıcan" kelimeleri, umumen چَعڤ ve بَعجان şeklinde, bazan چاڤ ve باجان şeklinde okunur.
* Arapçadan gelen **قرآن**، **أول**، **أرض**، **ألبت**، **أما** kelimeleri, Kürtçede قُرعان، عَوِل، عَرد، هَلبَت، هَما gibi okunur.

### Harflerin Fonetik Aslı ve Evrensel Elifbe Birliği
Yaygın ve hatalı bir inanışın aksine, elifbedeki harflerin büyük bir kısmı sadece Arap diline mahsus olmayıp, küresel ses alemine hitap etmektedir. Dil ilmi ve fonetik ekseninde tedkik edildiğinde, hakiki manada münhasıran Arapçaya ait sayılabilecek harfler sadece Dad **ض** ve kendine has gırtlaksı yapısıyla Ayn **ع** harfleridir. Bu iki harf yine de bazı dillerde ses olarak mevcuttur. İkisi haricindeki diğer Hı **خ**, Peltek Se **ث** veya Ha **ح** gibi sesler, aslında Latin, Cermen, Slav ve Kafkas dilleri gibi Arapça ile hiçbir akrabalığı bulunmayan dillerde yapısal olarak mevcuttur. 

Nitekim Batı elifbelerinin temelindeki "H" harfi, tarihi ve etimolojik olarak Ha **ح** harfiyle aynı Fenike (Het) karaktere dayanmaktadır. Bu evrensel bağlar göz önünde bulunduğunda, elifbeyi belli bir coğrafyaya hapsetmek yerine, seslerin küresel ortaklığını esnek ve akil bir imla nizamı elzemdir.

* Rumi dillerden gelen kelimeler bu standarda göre imla edilmelidir:

| Rumi | Arabi |
| --- | --- |
| A | ا |
| B | ب (bazan ڤ) |
| C | خ (bazan ق\ك) |
| Ç | چ (bazan س\ش) |
| D | د |
| E | ه (bazan ا\ى\ع) |
| F | ف |
| G | ج\غ\گ |
| GH | غ |
| H | ح\ه |
| I | ى\ي |
| J | ژ\ي |
| K | ك |
| L | ل |
| M | م |
| N | ن (bazan ڭ\ڠ)
| O | و (bazan ع) |
| P | پ (bazan ف) |
| Q | ق |
| R | ر |
| S | س (bazan ص\ش) |
| T | ت (bazan ث\ذ\ط\ظ) |
| U | ࢫ |
| V | ڤ |
| W | و |
| X | كس (bazen خ\ش) |
| Y | ي |
| Z | ز (bazan ص\ژ) |

---
## 5. DİJİTAL MÜHENDİSLİK: KLAVYE TUŞ DÜZENİ

![Evrensel Elifbe Klavye Düzeni](klavye.png)

Bu vizyon, Microsoft altyapısı (MSKLC) ile derlenmiş ve çalışan bir yazılım teknolojisidir. Standard Q klavyesindeki kas hafızası aynen korunmuştur. Klavyenin bu versiyonu mevcut Unicode sistemine ve Türkçe Q düzenine, tam uyumlu tasarlanmıştır:

### Evrensel İslami Klavye Tuş Haritası:

| Latin Tuşu | Normal Basış | Shift + Tuş | AltGr + Tuş |
| --- | --- | --- | --- |
| **`** / **"** | **ء** (Hemze) | ٔ (Harf Üstünde Hemze) | ۀ (Hemzeli He) |
| **Q** | ق (Kaf) | ٯ (Noktasız Kaf) | - |
| **W** | ص (Sad) | ض (Dad) | ؤ (Vav Hemze) |
| **E** | ه (He) | ة (Te Merbuta) | ہ (Kancalı He) |
| **R** | ر (Re) | ڕ (Kürtçe Kalın Re) | ڑ (Urduca Sert Re) |
| **T** | ت (Te) | ث (Peltek Se) | ٹ (Urduca Sert Te) |
| **Y** | ط (Tı) | ظ (Zı) | - |
| **U** | و (Vav) | **ࢫ** (Altında Nokta Olan Vav) | ۆ (Kürtçe Wo) |
| **I** | ي (Ye) | **ى** (Elif Maksure) | ێ (Kürtçe İmale) |
| **O** | ع (Ayn) | **ڠ** (Jawi Ngayn) | - |
| **P** | پ (Pe) | ْ (Sükun) | ٮ (Noktasız Be) |
| **[** / **Ğ** | غ (Gayn) | ّ (Şedde) | - |
| **]** / **Ü** | ~ (Med İşareti) | آ (Elif Med) | ٓ (Med) |
| **A** | ا (Elif) | أ (Elif Hemze) | ٱ (Hemze Vasl) |
| **S** | س (Sin) | ئ (Ye Hemze) | - |
| **D** | د (Dâl) | ذ (Zâl) | ڈ (Urduca Sert Dâl) |
| **F** | ف (Fe) | ڡ (Noktasız Fe) | - |
| **G** | گ (Gâf) | ک (Sade Kâf) | - |
| **H** | ح (Ha) | حٔ (Hemzeli Ha) | ں (Noktasız Nun) |
| **J** | ژ (Jeyn) | ے (Ye Beri) | ۓ (Ye Beri Hemze) |
| **K** | ك (Kâf) | ڪ (Kâf Sindi) | - |
| **L** | ل (Lam) | ڵ (Kürtçe Kalın Lam) | لا (Lamelif) |
| **;** / **Ş** | ش (Şin) | - | ´ (Sağ Yatık Çizgi) |
| **'** / **İ** | (ZWNJ) | (ZWJ) | - |
| \ / **,** | , (Virgül) | ; (Noktalı Virgül) | ` (Sol Yatık Çizgi) |
| \ / **<** | < (Sağ Büyüktür) | > (Sol Büyüktür) | (Dik Uzun Çizgi) |
| **Z** | ز (Zeyn) | َ (Üstün) | 1 (Rakam) |
| **X** | خ (Hı) | ً (Üstün Tenvini) | 2 (Rakam) |
| **C** | ج (Cim) | ٰ (Üstün Çekeri) | 3 (Rakam) |
| **V** | **ڤ** (Ve) | ِ (Kesre) | 4 (Rakam) |
| **B** | ب (Be) | ٍ (Kesre Tenvini) | 5 (Rakam) |
| **N** | ن (Nun) | ٖ (Kesre Çekeri) | 6 (Rakam) |
| **M** | م (Mim) | ُ (Ötre) | 7 (Rakam) |
| **,** / **Ö** | **ڭ** (Nâf) | ٌ (Ötre Tenvini) | 8 (Rakam) |
| **.** / **Ç** | چ (Çim) | ݮ (Altında Tı Olan Ha) | 9 (Rakam) |
| **/** / **.** | . (Nokta) | : (İki Nokta) | 0 (Rakam) |

---
## 6. BU NİZAMIN FAYDALARI

1. **Data Tasarrufu:** Unicode standartlarında İslam dünyası için ayrılan yüzlerce karakterlik hantal alan, sadece birkaç on karaktere düşerek dijital depolama ve veritabanı boyutlarını küçültecektir.
2. **AI ve NLP Hızı:** Büyük dil modelleri (LLM) ve suni zeka algoritmaları, Elifbe tabanlı metinleri işlerken çok daha hızlı tabii dil işleme (NLP) yapabilecektir.
3. **Font Tasarım Kolaylığı:** Hat (font) tasarımcıları, binlerce glif üretmek yerine sadece temel bağlantı formlarına odaklanabilecektir.

*Bu tavsiye, dijital ortografide tasarruf ve global standardizasyon sağlamak gayesiyle açık kaynak olarak tartışmaya sunulmuştur.*

### İndirme

Bu sistemin çalışır haldeki Windows kurulum dosyasını (`setup.exe`) ve kaynak kodlarını (`islami.klc`) tek bir paket halinde, kendi aranızdaki yazışmalarda bu standardı kullanmak için *[buradan](https://github.com/Abdurrahmancv/alifba)* indirebilirsiniz:

*([👉 KLAVYEYİ VE COĞRAFYALARI BİRLEŞTİREN YAZILIMI HEMEN TECRÜBE EDİN 👈](https://abdurrahmancv.github.io/alifba))*
