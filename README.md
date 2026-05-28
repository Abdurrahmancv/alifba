# Ortak İslam Elifbesi ve Evrensel Klavye Standartı

**Yazar:** Abdurrahman Çevik  
**Konum:** Mardin, Artuklu  
**E-posta:** abdurrahmancevik2005@gmail.com

---

## 1. VİZYONUMUZ: "Adem'in Oğulları İlmi Zeminde Buluşmalı"

Bu proje, küresel savaşların ve politik kutuplaşmaların anlamsızlığına inanan; insanlığın dürüstlük, samimiyet ve iyi niyetle ortak bir ilmi zeminde buluşmasını hedefleyen evrensel bir medeniyet hareketidir. Bizi birleştiren en güçlü unsur İslam medeniyetidir.

İslam coğrafyasındaki halklar (Kürtler, Türkler, Farslar, Araplar, Urdular..) kendi dillerinin özgün seslerini koruyarak, dijital dünyada ortak bir elifbe çatısı altında birleşebilirler. Bu sistem, dilleri aslına sadık kalarak, kıraati kolaylaştıran bir "orta yol" çözümüdür.

## 2. MEVCUT SİSTEMİN ZAAFİYETİ: Unicode ve Data İsrafı

Unicode standartlarında, Elifbe tabanlı diller (Arapça, Farsça, Türkçe, Kürtçe, Urduca..) ekrana basılırken hantal bir yapı kullanılır:

1. **0x06 Sırası (Standard Kodlar):** Harflerin sadece ham karakter değerini tutar.
2. **Presentation Forms (Sunum Biçimleri / 0xFB50 - 0xFEFF Sırası):** Bilgisayarın font motoru harfin başta, ortada, sonda veya yalın olduğunu hesaplaması için yüzlerce gereksiz alan işgal eder.

Bu durum veritabanlarında yer kaplar ve OpenType mimarları için hantal yazılım algoritmaları doğurur. Son yüzyılda süregelen "Arap harflerinde her harfin 4 farklı yazılış formu vardır, öğrenmesi zordur" iddiası bir yanılgıdan ibarettir.

*Yazının estetik görünmesi için kullanılan, harflerin diğer formları (ortadaki, sondaki ve hususi formlar) bu sırada yer alabilir. Bu haliyle estetlik formlar, mevcut ayrılan alandan çok daha az yer kaplar.*

## 3. MİMARİ ÇÖZÜM: Harflerde En Fazla 2 Form Vardır

Tavsiye ettiğimiz bu ortografik nizam ile, bilgisayarların font işleme mantığını kökten sadeleştirerek, elifbenin matematikal bir tasarrufa sahip olduğunu isbatlıyoruz:

* **2 Formlular (Kendinden sonra birleşenler):** Sadece iki şekli vardır; bağlantılı form (başta/ortada) ve bağlantısız form (sonda/yalın).
* **1 Formlular (Kendinden sonra birleşmeyenler):** Elif, Dal, Zel, Ra, Ze, Je, Vav gibi harfler her yerde aynı yazılır, sadece arkasındaki harf bağlanır.

*Harflerde 4 form yoktur, elifbede mesele sadece harfin kendinden sonraki harfe bağlanıp bağlanmamasıdır.*

Unicode cetvelindeki tüm "Arapça Sunum Biçimleri" (Presentation Forms) reform edilmeli, harfler **baştaki form** ve **yalın form** olmak üzere sadece iki forma indirilmelidir.

### 0x06 Sırasının Yeniden Tasarlanması (Başta/Bağlantılı Form)

Harflerin yalın hallerinin bulunduğu orijinal **0x06** tablosunda, harfler doğrudan **baştaki** yani **kendinden sonrakiyle birleşen** formuyla (Mesela: `بـ`) tutulmalıdır.

* Bu sayede kullanıcı harfe bastığı an, karakter otomatik olarak bir sonraki harfe akmaya ve el ele tutuşmaya hazır olur.
* Esasında harflerin tek bir standart şekli vardır. Sadece kelimeyi bitirirken bazı harflerin sonunu süsleriz. Bunu standard klavye usulündeki gibi Shift ile sağlamak daha makbuldür.

* Harflerin tabii görüntülerini elde etmek için Unicode cetveline yüzlerce yeni karakter eklemek sadece data israfıdır. Bunun yerine bazı harflerin (`ج`, `ح`, `خ`, `س`, `ش`, `ص`, `ض`, `ع`, `غ`, `ق`, `ن`, `ه`, `ي` gibi) sondaki haline Shift ile ulaşılacak.

* Kendinden sonraki harfle birleşen diğer `ب`, `ت`, `ث`, `ط`, `ظ`, `ف`, `ك`, `ل`, `م` gibi harflerin hemen ucuna halihazırda klavyede var olan Arapça virgül **(،)** işareti geldiğinde, harf zaten kendi yalın görüntüsüne tabii olarak kavuşacaktır. **(Mesela: `بـ` + `،` = `ب`)**

### Keşide (ـ) Kullanımı

Unicode cetvelinde yer kaplayan Tatweel (ـ) karakteri tamamen sistemden kaldırılmalıdır.

* Bunun yerine klavyedeki standart nokta (.) kullanılacaktır. Nokta, birleşmeye hazır harflerin arasında bulunduğunda, zaten keşide görüntüsüne tabii olarak kavuşacaktır.

## 4. DİLLERİN SES İHTİYAÇLARINA GÖRE TASARRUF

İslam coğrafyasındaki dillerin dijital imla karmaşasını çözen tasarruf hamleleri yapılmıştır:

### Vav ve Ötrenin Kullanımı

* Türkçe Vav `و` harfinin asli sesi "o/u" olup, Klasik Türkçede bu harf "v" için de kullanılmıştır. Mutlak ince bir harfe temas etse dahi Vav'ın aslı kalındır.
* Kürtçe Waw `و` harfinin asli sesi "ô/û" olup, Klasik Kürtçede aynen ifade edilmiştir.
* Ötre `ـُ` okutucusunun asli sesi "ö/ü" olup, Klasik Türkçe'de aynen ifade edilmiştir. Mutlak kalın bir harfe temas etse bile Ötre'nin aslı incedir.
* Zemme `ـُ` okutucusunun asli sesi "ue/ui" olup, Klasik Kürtçe'de aynen ifade edilmiştir.

### Ötrenin Harf Formu به كࢫردي ضمه\تࢫركجه اࢫتره

**Kürtçe ve Türkçe Okutucu Harf Çözümü:** Klasik imlada *ötre* (ö/ü) ve Kürtçedeki *zemme* (ue/ui) telaffuzunun netleşmesi için ötre harf ile ifade edilerek, Unicode standardındaki **"ࢫ"** harfi sisteme dahil edilmiştir. Mesela: **بࢫل** (böl), **بول** (bul).

Ötrenin harf formunu kiraat talebeleri için ࢫ karakteriyle ifade ettik. Aşağıda bazı misaller verilmiştir:

**Türkçe Misaller:**

* Vav ile اوردی (ordu), سور (sur), كوشه (köşe), كوفی (küfi).
* Ötre ile عࢫمر (ömer), اࢫست (üst), نࢫقطه (nokta), طࢫغرࢫل (tuğrul).

**Misalên Kurdî:**

* Waw ile اوستا(ôste), شࢫور(şûr), دوست(dôst), هࢫور(hûr).
* Zemme ile خࢫستن(xuestin), خࢫين(xuîn), خࢫار(xuar), گࢫه(guh), دࢫهو(dohô).

### Jeyn (ژ) Harfinin Tasfiyesi

* Türkçenin yapısında Je (ژ) ünsüzü yoktur. Elifbede bu harfi barındırmak yerine, saf dudak-diş ünsüzü olan **"ڤ"** (V) harfi sabitlenmiştir. Klavye, Kürtçe gibi diller için ژ harfini barındırır. Jeyn harfi Kürtçe gibi İrani diller için zaruri olsa da, Türkçe için bu ses ج ve bazan ز\ش harfleriyle ifade edilebilir. (Mesela: شارز\شارج "şarj", جاله "jale", جندارمه "jandarma") Lakin ڤ sesi, Türkçe için elzemdir. 
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

## 5. DİJİTAL MÜHENDİSLİK: KLAVYE TUŞ DÜZENİ

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

## 6. BU NİZAMIN FAYDALARI

1. **Data Tasarrufu:** Unicode standartlarında İslam dünyası için ayrılan yüzlerce karakterlik hantal alan, sadece birkaç on karaktere düşerek dijital depolama ve veritabanı boyutlarını küçültecektir.
2. **AI ve NLP Hızı:** Büyük dil modelleri (LLM) ve suni zeka algoritmaları, Elifbe tabanlı metinleri işlerken çok daha hızlı tabii dil işleme (NLP) yapabilecektir.
3. **Font Tasarım Kolaylığı:** Hat (font) tasarımcıları, binlerce glif üretmek yerine sadece temel bağlantı formlarına odaklanabilecektir.

*Bu tavsiye, dijital ortografide tasarruf ve global standardizasyon sağlamak gayesiyle açık kaynak olarak tartışmaya sunulmuştur.*

### İndirme

Bu sistemin çalışır haldeki Windows kurulum dosyasını (`setup.exe`) ve kaynak kodlarını (`islami.klc`) tek bir paket halinde, kendi aranızdaki yazışmalarda bu standardı kullanmak için *[buradan](https://github.com/Abdurrahmancv/alifba)* indirebilirsiniz:

*([👉 KLAVYEYİ VE COĞRAFYALARI BİRLEŞTİREN YAZILIMI HEMEN TECRÜBE EDİN 👈](https://abdurrahmancv.github.io/alifba))*
