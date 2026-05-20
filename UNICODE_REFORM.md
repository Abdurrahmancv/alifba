# Unicode Karakter ve Ortografi Reformu Tavsiyesi

**Yazar:** Abdurrahman Çevik  
**Konum:** Mardin, Artuklu  
**E-posta:** abdurrahmancevik2005@gmail.com  
**Lisans:** MIT License

---

## 1. MEVCUT UNICODE SİSTEMİNDEKİ DATA İSRAFI
Mevcut Unicode standartlarında, Arap tabanlı alfabeler (Arapça, Farsça, Türkçe, Kürtçe, Urduca..) ekrana basılırken hantal bir yapı kullanılır:
1. **0x06 Sırası (Standard Kodlar):** Harflerin sadece ham karakter değerini tutar.
2. **Presentation Forms (Sunum Biçimleri / 0xFB50 - 0xFEFF Sırası):** Bilgisayarın font motoru harfin başta, ortada, sonda veya yalın olduğunu hesaplaması için yüzlerce gereksiz alan işgal eder.

Bu durum veritabanlarında yer kaplar ve OpenType mimarları için hantal yazılım algoritmaları doğurur. Yazının estetik görünmesi için kullanılan, harflerin diğer formları (ortadaki, sondaki ve hususi formlar) bu sırada yer alabilir. Bu haliyle estetlik formlar, mevcut ayrılan alandan çok daha az yer kaplar.

---

## 2. HARFLERDE 4 FORM YOKTUR
Tavsiye ettiğimiz bu ortografik reform, bilgisayarların font işleme mantığını kökten sadeleştirmektedir. Unicode cetvelindeki tüm "Arapça Sunum Biçimleri" (Presentation Forms) reform edilmeli, harfler sadece **iki forma (Başta ve Sonda)** indirilmelidir:

### A. 0x06 Sırasının Yeniden Tasarlanması (Başta/Bağlantılı Form)
Harflerin yalın hallerinin bulunduğu orijinal **0x06** tablosunda, harfler doğrudan **baştaki / kendinden sonrakiyle birleşen formuyla (Mesela: `بـ`)** tutulmalıdır. 
- Bu sayede kullanıcı harfe bastığı an, karakter otomatik olarak bir sonraki harfe akmaya ve el ele tutuşmaya hazır olur.

### B. Şekillendirici Operatör Olarak "Virgül (،)" Kullanımı
Harflerin kelime sonundaki ya da tek başlarına durdukları o yalın/bitişik görüntülerini elde etmek için Unicode cetveline yüzlerce yeni karakter eklemek bir veri israfıdır. Bunun yerine bazı harflerin (`ج`, `ح`, `خ`, `س`, `ش`, `ص`, `ض`, `ع`, `غ`, `ق`, `ن`, `ه`, `ي` gibi) sondaki haline Shift ile ulaşılacak, diğerleri için ise mevcut semboller birer operatör olarak kullanılmalıdır:
- Elifbedeki `ب`, `ت`, `ث`, `ط`, `ظ`, `ف`, `ك`, `ل`, `م` gibi harflerin hemen yanına halihazırda klavyede var olan Arapça virgül **(،)** işareti getirildiğinde; bu iki karakter dizilimi, harfin kelime sonundaki yalın görüntüsüne kavuşacaktır. **(Mesela: `بـ` + `،` = `ب`)**

### C. Keşide (0x0640) İsrafının Bitirilmesi
Metinleri uzatmak için Unicode cetvelinde yer tutan Tatweel (ـ) karakteri tamamen sistemden kaldırılmalıdır. 
- Bunun yerine klavyedeki standart alt çizgi (_) veya nokta (.) işaretleri kullanılacaktır. Bu işaretler harflerin arasında bulunduğunda, harf uzatma çizgisi görüntüsüne kavuşacaktır.

---

## 3. BU REFORMUN FAYDALARI
1. **Data Tasarrufu:** Unicode standartlarında İslam dünyası için ayrılan yüzlerce karakterlik hantal alan, sadece birkaç on karaktere düşerek dijital depolama ve veritabanı boyutlarını küçültecektir.
2. **AI ve NLP Hızı:** Büyük dil modelleri (LLM) ve suni zeka algoritmaları, Elifbe tabanlı metinleri işlerken 5 farklı karkter ve 4 farklı formun karmaşasından kurtularak, çok daha hızlı tabii dil işleme (NLP) yapabilecektir.
3. **Font Tasarım Kolaylığı:** Hat (font) tasarımcıları, binlerce glif üretmek yerine sadece temel bağlantı formlarına odaklanabilecektir.

---
*Bu doküman, dijital ortografide tasarruf ve global standardizasyon sağlamak gayesiyle açık kaynak olarak tartışmaya sunulmuştur.*
