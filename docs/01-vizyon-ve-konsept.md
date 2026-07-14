# 01 — Vizyon ve Konsept

## Ne yapıyoruz?

**Gölge Oyunu** (kod adı: Kuzgun), Thief: The Dark Project (1998) ve Thief II: The Metal Age (2000)
geleneğini takip eden bir **birinci sınıf gizlilik oyunu**dur — ama 3D birinci şahıs yerine,
tek kişilik/küçük ekiple üretilebilir **2D piksel sanat, yukarıdan bakışlı** bir formda.
Mekân: Osmanlı estetiğinden beslenen **kurgusal** liman şehri **Sayeban**.

Oyuncu, kentin en usta hırsızı **Kuzgun**'dur. Görev tabanlı ilerler: her görev bir "bulmaca
kutusu" gibi tasarlanmış bir mekândır (konak, bedesten, sarnıç, saat kulesi...). Amaç çoğu zaman
aynıdır: **içeri gir, keseni doldur, asıl hedefi ele geçir, görünmeden çık.**

## Neden bu oyun? (Fırsat)

1. **Tür aç ama arz kıt.** Thief 2014'ten beri ana seri sessizdi; 2025–26'da tür yeniden
   canlandı (Thief VR: Legacy of Shadow — Aralık 2025; Warren Spector'un Thick as Thieves'i —
   Mayıs 2026; Gloomwood hâlâ erken erişimde). Talep kanıtlı, ama "klasik Thief hissi" veren
   yeni oyun sayısı bir elin parmağını geçmiyor. Bkz. `05-hedef-kitle-ve-pazar.md`.
2. **2D piksel + gizlilik kombinasyonu kanıtlı ve üretilebilir.** The Siege and the Sandfox (2025)
   ve Mark of the Ninja (2012) bu formülün çalıştığını gösterdi. 3D immersive sim üretmek
   yıllar ve milyonlar ister; 2D'si bir-iki kişiyle mümkün.
3. **Kültürel açı = küresel özgünlük.** Batı fantezisi hırsız oyunu yüzlerce kez yapıldı.
   Osmanlı gecesi, kandiller, asesler, Karagöz perdesi — bunu **hiç kimse yapmadı**.
   Yerel oyuncuda gurur, küresel oyuncuda merak uyandırır (Assassin's Creed Revelations'ın
   İstanbul'unun sevilme sebebi). "Gölge oyunu" tabirinin Türkçede zaten Karagöz demek olması,
   pazarlamada eşi bulunmaz bir kelime oyunudur.

## Tasarım Sütunları (her karar bunlara vurulur)

1. **Gölge özgürlüktür.** Işık mekanik bir kaynaktır: fener, mum, ay. Oyuncu ışığı söndürür,
   gölgeyi giyinir. Ekrandaki "Işık Taşı" ne kadar parlaksa o kadar görünürsün.
2. **Ses bir sistemdir.** Halı susturur, taş fısıldar, gıcırtılı ahşap ihbar eder. Koşmak
   bir karardır, bedeli vardır.
3. **Şiddet son çaredir.** Kuzgun savaşçı değildir. Bayıltmak mümkün, öldürmek (varsa bile)
   cezalandırılır; en itibarlı derece "Hayalet"tir: kimseye dokunmadan, kimseye görünmeden.
4. **Seviye bir bulmaca kutusudur.** Her hedefe en az iki-üç yol: çatı, kanalizasyon, rüşvet
   verilmiş kapı. Keşfeden ödüllendirilir (loot, kestirme, kulak misafiri olunan diyalog).
5. **Şehir bir karakterdir.** Sayeban'ın loncaları, tarikatları, dedikoduları görevler arasında
   gazete küpürleri ve sokak konuşmalarıyla işlenir (Thief II'nin gazeteleri gibi).
6. **Perde estetiği.** Anlatı, Karagöz gölge tiyatrosu diliyle sahnelenir: ara sahneler deri
   kukla silüetleri, perde arkası ışık, tef-kudüm geçişleri. Ucuz üretilir, unutulmaz görünür.

## Tema Kararı

Üç aday değerlendirildi; **A önerilir ve bu depo A üzerine kuruludur.**

| Seçenek | Artıları | Eksileri |
|---|---|---|
| **A) Osmanlı esintili kurgusal şehir (Sayeban)** ✅ | Özgün, pazarlanabilir "ilk", yerel gurur + küresel egzotizm, Thief'in lonca/tarikat yapısına birebir oturan tarihî kurumlar (asesler, böcekbaşı, loncalar), Karagöz estetiği bedava geliyor | Kültürel temsil özeni ister (aşağıda ilkeler var) |
| B) 1900'ler Pera / erken Cumhuriyet steampunk | Metal Age'in makine temasına yakın, tramvay/telgraf/fabrika | Görsel üretimi daha pahalı, "Osmanlı gecesi" kadar ikonik değil; Sezon 2 teması olarak saklanabilir |
| C) Klasik Batı fantezi şehri (saf Thief klonu) | Güvenli, referans bol | Kalabalıkta kaybolur, "neden Thief oynamayayım?" sorusuna cevabı yok |

**Neden kurgusal şehir, gerçek İstanbul değil?** Thief'in "The City"si gibi Sayeban da
gerçek tarihin yükünü taşımadan onun dokusunu ödünç alır. Tarihî hata diye bir şey kalmaz,
yaratıcı özgürlük tamdır, hassas konulardan doğal mesafe alınır. (Altındaki Bizans-vari
"Kadim Şehir" harabeleri, İstanbul'un sarnıçlar üstünde kurulu gerçeğinin kurgusal yankısıdır.)

## Duyarlılık İlkeleri (pazarlıksız)

- **Gerçek din oyun malzemesi değildir.** Thief, Hıristiyanlığı değil kurgusal Hammerite
  tarikatını kullandı. Biz de İslam'ı değil, kurgusal **Ehl-i Mizan**, **Yaban** ve
  **Akrebiyye** düzenlerini kullanırız. Cami, ezan, Kur'an, gerçek tarikat adları oyunda
  **yer almaz**; soygun hedefi hiçbir gerçek ibadet mekânı olamaz.
- Mimari doku (konak, bedesten, arasta, hamam, sarnıç, saat kulesi), gündelik kültür
  (kahvehane, çarşı, esnaf loncası, Karagöz) ve müzik makamları **kullanılır** — bunlar
  medeniyet mirasıdır, ibadet değildir.
- Karakterler karikatür değildir: asesler tembel-aptal "yabancı bekçi" klişesi değil,
  maaşı geciken, çorbası soğuyan, kendi derdinde insanlar olarak yazılır (Thief'in
  muhafız diyaloglarının sevilme sebebi buydu).

## Kapsam Gerçekçiliği

Bu projeyi öldürebilecek tek şey kapsam şişmesidir. Kural:

- **Önce tek bir mükemmel görev.** Thief'i Thief yapan "Lord Bafford'un Malikânesi"nin
  ilk 10 dakikasıdır. Bizim "Kesat Zamanlar" görevimiz o kaliteye ulaşmadan ikinci görev açılmaz.
- Prototip (bu depoda) → Godot'da gri kutu (graybox) → dikey dilim → demo → Sezon 1 (8 görev).
  Ayrıntı: `06-yol-haritasi-ve-araclar.md`.
- Her özellik şu soruya cevap vermek zorunda: *"Bu, gölge-ışık-ses üçgenini derinleştiriyor mu?"*
  Cevap hayırsa listeye bile girmez.
