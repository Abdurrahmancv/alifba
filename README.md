# Ortak İslam Elifbesi ve Evrensel Klavye Standartı

**Geliştirici:** Abdurrahman Çevik  
**Konum:** Mardin, Artuklu  
**Lisans:** MIT License

---

## 1. VİZYONUMUZ: "Adem'in Oğulları İlmi Zeminde Buluşmalı"
Bu proje, küresel savaşların ve politik kutuplaşmaların anlamsızlığına inanan; insanlığın dürüstlük, samimiyet ve iyi niyetle ortak bir ilmi zeminde buluşmasını hedefleyen evrensel bir medeniyet hareketidir. Bizi birleştiren en güçlü unsur İslam medeniyetidir. 

İslam coğrafyasındaki halklar (Kürtler, Türkler, Farslar, Araplar, Urdular..) kendi dillerinin özgün seslerini koruyarak, dijital dünyada ortak bir elifbe çatısı altında birleşebilirler. Bu sistem, dilleri, aslına sadık kalarak kıraati kolaylaştıran bir "orta yol" çözümüdür.

---

## 2. ELİFBE ÖĞRENMEK KOLAYDIR
Son yüzyılda süregelen "Arap harflerinde her harfin 4 farklı yazılış formu vardır, öğrenmesi zordur" iddiası bir yanılgıdan ibarettir. Bu proje ile elifbenin matematikal bir tasarrufa sahip olduğunu isbatlıyoruz:

- **2 Formlular (Kendinden sonra birleşenler):** Sadece iki şekli vardır; bağlantılı form (kelime başı/ortası) ve bağlantısız form (kelime sonu/yalın).
- **1 Formlular (Kendinden sonra birleşmeyenler):** Elif, Dal, Zel, Ra, Ze, Je, Vav gibi harfler her yerde aynı yazılır, sadece arkasındaki harf bağlanır.
- **Harflerde 4 Form Yoktur:** Elifbede mesele sadece harfin kendinden sonraki harfe bağlanıp bağlanmamasıdır.

---

## 3. DİLLERİN SES İHTİYAÇLARI VE YAPILAN OPTİMİZASYONLAR
Bu sistemde, İslam coğrafyasındaki dillerin dijital imla karmaşasını çözen tasarruf hamleleri yapılmıştır:

1. **Fazlalık Harflerin Elenmesi (J Sesi):** Türkçenin orijinal yapısında "J" (ژ) ünsüzü yoktur. Elifbede bu harfi barındırmak yerine, saf dudak-diş ünsüzü olan **"ڤ"** (V) harfi sabitlenmiştir.
2. **Urduca ve Kürtçe Aspirasyon (Soluklaşma) Çözümü:** Urducadaki "Du Çeşm He" (ھ) harfine ihtiyaç yoktur. Kelimelerde aspirasyonu (hava üfleyerek okumayı) göstermek için sıradan **"ه"** harfi tek başına yeterlidir.
   - Kürtçe'de hava verilmeden okunan *Kêr* (Kâr) kelimesi **کێر** şeklinde yazılırken; hava üfleyerek okunan *Kêr* (Bıçak) kelimesi **کهێر** şeklinde yazılarak anlam karmaşası kökten çözülmüştür.
   - Urduca "Sert Te" (ٹ) harfine de ihtiyaç yoktur. Elifbede halihazırda bulunan Te (ت), Havalı Te (ته), The (ث), Tı (ط) formları, Urducadaki sesleri tam olarak karşılayabilmektedir.
3. **Kürtçe ve Türkçe Okutucu Harf Çözümü:** Klasik imlada *ötre* (ö/ü) ve Kürtçedeki *zemme* (we/wi) telaffuzunun netleşmesi için ötre harf ile ifade edilerek, Unicode standardındaki **"ࢫ"** harfi sisteme dahil edilmiştir. (Mesela: Bul/Böl kelimelerini ayırmak için **بول\بࢫل** imlası geliştirilmiştir).

---

## 4. DİJİTAL MÜHENDİSLİK: KLAVYE TUŞ DİZİLİMİ
Bu vizyon, Microsoft altyapısı (MSKLC) ile derlenmiş ve çalışan bir yazılım teknolojisidir. Standard Q klavyesindeki kas hafızası aynen korunmuştur. Klavyenin bu versiyonu Türkçe Q düzenine, tam uyumlu tasarlanmıştır:

### Evrensel İslam Klavyesi Tuş Haritası:


| Latin Tuşu | Normal Basış | Shift + Tuş | AltGr + Tuş |
| :---: | :---: | :---: | :---: |
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

## 5. BAĞLANTI VE İNDİRME
Bu sistemin çalışır haldeki Windows kurulum dosyasını (`setup.exe`) ve kaynak kodlarını (`Islami.klc`) tek bir paket halinde indirmek, kendi aranızdaki yazışmalarda bu standardı kullanmak için aşağıdaki bağlantıyı kullanabilirsiniz:

[👉 KLAVYEYİ VE COĞRAFYALARI BİRLEŞTİREN YAZILIMI ÜCRETSİZ İNDİRİN 👈] 
*(https://github.com/Abdurrahmancv/alifba)*
