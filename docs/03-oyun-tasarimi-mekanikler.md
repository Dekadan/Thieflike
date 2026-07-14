# 03 — Oyun Tasarımı ve Mekanikler

## 1. Perspektif Kararı — **BİRİNCİ ŞAHIS (POV)** ✅

> Revizyon: İlk taslak yukarıdan bakışı öneriyordu; yapımcı kararıyla perspektif
> **birinci şahsa** çevrildi — Thief'in "kapı aralığından süzülme" gerginliği ancak
> POV'de yaşanır. Üstten bakış prototipi `prototip/arsiv-ustten-bakis.html`'de
> arşivlendi (devriye rotası okuma/planlama aracı olarak hâlâ değerli).

| Aday | Artıları | Eksileri | Karar |
|---|---|---|---|
| **Birinci şahıs, retro "software-render" estetiği** ✅ | Thief gerginliğinin aslı; piksel doku + düşük çözünürlük = tek kişiyle üretilebilir 3D (Gloomwood/Dusk okulu); ışık-gölge yüz hatlarında hissedilir; ses yönü POV'de iki kat etkili | Devriye rotası okumak zorlaşır → çözüm: ses işaretleri (asa tık-tıkı), TAB el çizimi harita, kapı aralığından gözetleme | **Seçildi** — prototip bu formda |
| Yukarıdan bakış | Planlama netliği, en ucuz üretim | "İçinde olma" hissi yok | Arşivlendi; belki "Hafız kayıt masası" mini-oyunu olarak döner |
| Yandan görünüm / izometrik | — | Kat planı hissi ve/veya maliyet | Reddedildi |

**Teknik çeviri:** Prototip el yazması **WebGL gerçek-3D motoru**: serbest bakış
(yukarı/aşağı/çapraz fare kontrolü), gerçek perspektif kamera, kutu-gövde low-poly
karakterler (yüz dokulu), karo bazlı ışık haritası shader'da yumuşak örneklenir,
UI tam çözünürlüklü ayrı katmanda (okunur tipografi). Godot'da hedef aynı reçetenin
büyüğü: Godot 3D + piksel dokular + karo bazlı ışık değeri gameplay için ayrı hesap —
görünüm retro (Thief 1998 "software-render" hissi), sistemler modern.

## 2. Çekirdek Döngü (30 saniyelik döngü)

**Gözle → Planla → Sız → Al → Kaybol**

1. **Gözle:** Devriye rotasını, ışık kaynaklarını, zemin türlerini oku.
2. **Planla:** Hangi ışık söndürülecek, hangi gürültü nereye çekilecek?
3. **Sız:** Gölgeden gölgeye; hız = ses; kapı = risk.
4. **Al:** Loot parıltısı riskin ödülü; en değerli mal en aydınlık yerde durur (tasarım kuralı).
5. **Kaybol:** Alarm çaldıysa bile oyun bitmez — saklan, bekle, devriye "kedidir kedi" deyip
   dönsün (Thief'in en sevilen duygusu: fırtınayı dolapta atlatmak).

## 3. Işık ve Görünürlük — "Işık Taşı"

- Dünya karo (tile) tabanlı; her karonun 0–1 arası **ışık değeri** var: kaynaklardan
  (fener, mum, meşale, pencere/ay) mesafe + duvar engeliyle (görüş hattı) hesaplanır.
- Oyuncunun bastığı karonun ışığı = **görünürlük çarpanı**. Ekrandaki **Işık Taşı**
  (Thief'in light gem'i) bunu gösterir: kapkara = görünmezsin, bembeyaz = ortadasın.
- Devriye görüş menzili ≈ `taban_menzil × (0.2 + 0.8 × ışık) × (çömelme ? 0.75 : 1)`.
  Karanlıkta bir devriyenin dibinden geçilebilir — Thief'in tanımlayıcı duygusu korunur.
- **Işık söndürme:** Mum → yakından üfleme/fitil makası (sessiz). Fener/meşale → **matara**
  (su kesesi) fırlatmak gerekir (Thief'in su oku), küçük gürültü çıkarır. Söndürülen ışık
  devriyeleri **tedirgin eder**: sönen feneri gören devriye şüpheye geçer (risk/ödül).

## 4. Ses Sistemi — zemin türleri

| Zemin | Sezgi | Gürültü yarıçapı (sessiz yürüme / yürüme / koşma) |
|---|---|---|
| Halı / kilim | dost | çok küçük / küçük / orta |
| Çimen, toprak | dost | çok küçük / küçük / orta |
| Taş, mermer | nötr | küçük / orta / **büyük** |
| Gıcırtılı ahşap | tuzak | orta / büyük / **çok büyük** |
| Su birikintisi (tam oyun) | tuzak + iz | orta / büyük / çok büyük + ıslak ayak izi |

- Gürültü bir **olaydır**: yarıçapı içindeki devriye, kaynağa yürür ("Şu sese bir bakayım").
- **Çakıl taşı**: oyuncunun cebindeki taşınabilir gürültü — istediğin köşeye "ses" atarsın
  (Thief'in noisemaker oku). Devriyeyi kapıdan uzaklaştırmanın temel aleti.
- Kapılar açılırken ses çıkarır; koşarak kapı açmak "davul çalmak"tır.

## 5. Devriye Yapay Zekâsı — durum makinesi

```
DEVRİYE ──(kısmi görme / ses)──► ŞÜPHE ──(tam görme)──► ALARM
   ▲                              │  ▲                    │
   │      (bir şey bulamadı)      │  │ (ceset/sönmüş      │ (oyuncuyu kaybetti)
   └──────────────────────────────┘  │  fener gördü)      ▼
                                     └───────────────── ARAMA ──(süre doldu)──► DEVRİYE*
```

- **Görme birikimlidir** (anında değil): görüş konisinde + görüş hattı açık + yeterli ışıkta
  duran oyuncu, devriyenin "şüphe ibresini" doldurur; mesafe ve oyuncu hızı doldurma hızını
  belirler. Kısa bir siluet = "Hı? Kim var orada?"; uzun bakış = alarm.
- **ALARM**: kovalar; yakalarsa görev biter (tam oyunda: kılıçlı çatışma seçeneği, ama
  Kuzgun dövüşte zayıftır — kaçmak her zaman daha akıllıca).
- **ARAMA**: son görülen noktanın çevresini tarar, sonra homurdanarak döner
  (*"Rüzgârdır... rüzgâr olsun."*). Ama artık **tedirgindir**: görüş menzili kalıcı olarak artar (*).
- **Ceset/bayıltılmış devriye** görülürse: anında ALARM + görev boyu yükseltilmiş teyakkuz.
  (Tam oyunda: cesetleri taşıyıp saklamak — Thief'in omuzda taşıma mekaniği.)
- Devriyeler insan gibi yazılır: kendi kendine söylenir, mola verir, pencereden bakar.
  YZ'nin "aptallıkları" bile karakter olmalı (Thief muhafızlarının mirası).

## 6. İMZA MEKANİK: **FANUS** — "Işığı söndürmezsin, ÇALARSIN."

Thief'i kopyalamamak için çekirdeğe (ışık-gölge) eklediğimiz, oyunun adına dönüşecek sistem.
Thief'in su oku ışığı *yok eder* (tek yönlü, tüketilir). Fanus ışığı **taşınabilir mala** çevirir:

- **Çal:** Herhangi bir alevin (mum, fener, meşale) başında `E`'ye basılı tut (~1 sn, kıpırdamadan).
  Alev fanusa girer, kaynak söner. Sessizdir — ama **ışığın söndüğünü gören devriye şüphelenir.**
- **Taşı:** Fanus en fazla 2 alev alır. (Elindeki fanusta alevler gerçekten yanar — HUD'ın kalbi.)
- **Bırak:** Sol tıkla alevi fırlat; düştüğü yerde **yeniden yanar** — yeni, gerçek bir ışık kaynağı.
  **Yoktan beliren ışığı gören devriye de şüphelenir** ve bakmaya gelir.

Bu üçlü tek başına şu oyunları doğurur:
1. **Karanlık kazmak:** Rotandaki ışıkları söküp geçilmez koridoru geçilir yapmak (su oku işlevi, ama geri alınabilir).
2. **Sahte ışık tuzağı:** Alevi boş odaya fırlat → devriye "Bu ışık da nereden çıktı?" diye oraya yürür → sen ters kapıdan geçersin (çakıldan daha güçlü, çünkü devriye ışığı *incelemek için bekler*).
3. **Risk ekonomisi:** Çalma kanalı seni 1 sn kımıldamaz bırakır; dolu fanus elini aydınlatır (görünürlüğün artar — ışığı taşımak bedel ister).
4. **Tema = mekanik:** Sezonun finali Kalb'i çalmaktır; oyun boyunca zaten "yanan şeyleri çalıyorsun". Kandil Gecesi görevinde (G6) şehir şenlik ışıklarıyla donanır — fanus orada altın değerinde.

**Diğer aday imza mekanikler** (Sezon 1 içinde katman olarak eklenebilir; öncelik sırasıyla):

| Fikir | Ne katıyor | Durum |
|---|---|---|
| **Islık / işaret taklidi** — aseslerin asa tık-tık kodlarını dinleyip taklit etmek ("devriye değiş" sinyaliyle nöbetçiyi yerinden etmek) | Ses sistemini savunmadan saldırıya çevirir; her görevde dinleyerek öğrenilir | G4'te sisteme girsin (planlandı) |
| **Gölge Kipi ("Perde")** — tam karanlıkta duvara yaslanınca Karagöz silüetine dönüşüp duvar boyunca kayma; ışık değene kadar görünmezsin | Fantezi ve sanat imzası; Yeşil Pir'in lütfu olarak hikâyeyle açılır | Sezon ortası güç (G7 rüyasından sonra) |
| **Kayıt Defteri** — kulak misafirliğiyle toplanan sırlar somut anahtara dönüşür (şantajla kapı açtırma, nöbet değiştirme) | Hafızlar temasını oynanışa bağlar; konuşmaları dinlemeye sebep verir | Dikey dilimde metin düzeyinde, sistemleşmesi Sezon 1 sonu |

## 6b. Araç Çantası (Thief karşılıkları)

| Bizim | Thief'teki | İşlev | Prototipte? |
|---|---|---|---|
| **FANUS** | Water arrow'un tersyüz edilmişi | Alev çal / taşı / yeniden yerleştir | ✅ (E basılı + sol tık) |
| **Çakıl taşı** | Noisemaker | Fırlat: sahte gürültü | ✅ (Q / sağ tık) |
| **Kum kesesi** (topuz) | Blackjack | Arkadan habersiz devriyeyi bayılt | ✅ (Space) |
| **Maymuncuk takımı** | Lockpicks | Kilitli kapı/kasa mini-etkileşimi | Tam oyunda |
| **Kement + kanca** | Rope arrow | Düşey erişim | Tam oyunda |
| **Keçe parçası** | Moss arrow | Gürültülü zemine sessiz şerit | Tam oyunda |

Araçlar **görevler arası dükkândan** akçeyle alınır (Thief II'nin görev önü mağazası):
çaldığın para, sonraki işin sermayesi. Fanus satın alınmaz — Kuzgun'un alametifarikasıdır;
kapasite yükseltmeleri (2→3 alev) dükkândan gelir.

## 7. Loot ve Ekonomi

- Loot üç boy: kese/çatal-kaşık (25–50), şamdan/enfiye kutusu (50–80),
  mühürlü kese/mücevher/cep saati (100+). Parıltı animasyonu karanlıkta bile fark edilir
  (adalet ilkesi: göremeyeceğin şeyi kaçırmış sayılmazsın).
- Görev hedefi: asgari loot + ana hedef (obje/bilgi) + opsiyonel hedefler.
- **Zorluk = sözleşme** (Thief'in usta dokunuşu): Acemi/Usta/Hayalet seçimi sadece can
  sayısı değil, **hedef listesi** değiştirir: Hayalet'te "hiç görünme, kimseyi bayıltma,
  %90 loot" gibi şartlar eklenir. Aynı harita, üç ayrı oyun.

## 8. Kontroller (PC birinci hedef — POV düzeni)

| Girdi | Eylem |
|---|---|
| Fare | Bakış (tıklayıp kilitle) |
| WASD | Yürü/yan adım (varsayılan: sessize yakın **yürüyüş**) |
| Shift (basılı) | **Koş** — hızlı ve gürültülü |
| C | **Çömel** — yavaş, sessiz, alçak (kamera düşer) |
| E (tık) | Etkileşim: loot al, kapı aç/kapa |
| E (basılı tut) | **Alevi fanusla çal** (~1 sn kanal) |
| Sol tık | **Fanustaki alevi fırlat** (baktığın yere yerleşir, yanar) |
| Q / sağ tık | Çakıl fırlat (baktığın yöne) |
| Space | Arkadan bayılt |
| TAB (basılı) | El çizimi kat planı |
| M | Ses aç/kapa · R | Yeniden başlat |

Gamepad desteği Godot aşamasında eklenir (stealth kitlesi klavye ağırlıklıdır, öncelik düşük).

## 9. Prototip ↔ Tam Oyun Kapsam Tablosu

| Sistem | Prototip (bu depo) | Dikey dilim (Godot) | Sezon 1 |
|---|---|---|---|
| POV render | ✅ raycast (tek kat) | Godot 3D low-res (çok kat, merdiven, pencere) | + dam/çatı seviyeleri |
| Işık/gölge + Işık Taşı | ✅ karo tabanlı | ışık prob sistemi (gameplay) + görsel ışık ayrımı | + hareketli ışık (el feneri devriyesi) |
| **Fanus** | ✅ çal/taşı/bırak + devriye tepkisi | + kapasite yükseltme, ateş fiziği (perde tutuşması?) | + Kandil Gecesi set-piece, ıslık taklidi, Gölge Kipi |
| Zemin sesi | ✅ 4 tür | + su, cam kırığı | + ıslak iz sistemi |
| Devriye YZ | ✅ 4 durumlu + ışık değişimi tepkisi | + rota varyasyonu, ikili muhabbet, asa tık-tık işaretleri | + kukla (otomat) düşman sınıfı |
| Bayıltma/ceset | ✅ bayılt + fark edilme | + taşıma/saklama | + "öldürme yasağı" zorluk şartı |
| Görev yapısı | tek konak, loot hedefi | tam "Kesat Zamanlar" (çok katlı, 3 giriş) | 8 görev + zorluk sözleşmeleri |
| Anlatı | başlık + görev metni | Karagöz açılış perdesi | tam senaryo, ara perdeler, mektuplar |
