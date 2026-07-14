# 03 — Oyun Tasarımı ve Mekanikler

## 1. Perspektif Kararı

| Aday | Artıları | Eksileri | Karar |
|---|---|---|---|
| **Yukarıdan bakış (top-down)** ✅ | Görüş konileri/devriye okuma kristal netlikte; ışık-gölge 2D'de en iyi burada çalışır; seviye tasarımı = kat planı (konak planı çizmek gibi); üretimi en ucuz | "Birinci şahıs gerginliği" birebir taşınamaz | **Seçildi.** Thief'in *sistemlerini* en sadık taşıyan 2D form bu. Gerginliği ses tasarımı + görüş menzili kısıtıyla geri kazanacağız. |
| Yandan görünüm (Mark of the Ninja tarzı) | Siluet estetiği güçlü; platform hissi | Kat planı hissi kaybolur, "binayı soymak" yerine "ekranı geçmek" hissi; animasyon yükü çok daha ağır | Sezon 2'de tek görevlik deney olabilir |
| İzometrik | Mimari gösterişli | Üretim maliyeti (her sprite 4-8 açı), gölge hesabı karmaşık | Reddedildi (tek kişilik ekip için) |

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

## 6. Araç Çantası (Thief karşılıkları)

| Bizim | Thief'teki | İşlev | Prototipte? |
|---|---|---|---|
| **Matara** (su kesesi) | Water arrow | Fırlat: fener/meşale söndür | ✅ (F / sağ tık) |
| **Fitil makası** | (yakın söndürme) | Bitişik mumu sessizce söndür | ✅ (E) |
| **Çakıl taşı** | Noisemaker | Fırlat: sahte gürültü | ✅ (sol tık) |
| **Kum kesesi** (topuz) | Blackjack | Arkadan habersiz devriyeyi bayılt | ✅ (Space) |
| **Maymuncuk takımı** | Lockpicks | Kilitli kapı/kasa mini-etkileşimi | Tam oyunda |
| **Kement + kanca** | Rope arrow | Belirli noktalara düşey erişim | Tam oyunda |
| **Keçe parçası** | Moss arrow | Gürültülü zemine sessiz şerit döşe | Tam oyunda |
| **Dürbün** | Scouting orb yok ama... | Uzak devriye rotası okuma | Tam oyunda (belki) |

Araçlar **görevler arası dükkândan** akçeyle alınır (Thief II'nin görev önü mağazası):
çaldığın para, sonraki işin sermayesi. Ekonomi döngüsü budur; para biriktirme oyunu değildir.

## 7. Loot ve Ekonomi

- Loot üç boy: kese/çatal-kaşık (25–50), şamdan/enfiye kutusu (50–80),
  mühürlü kese/mücevher/cep saati (100+). Parıltı animasyonu karanlıkta bile fark edilir
  (adalet ilkesi: göremeyeceğin şeyi kaçırmış sayılmazsın).
- Görev hedefi: asgari loot + ana hedef (obje/bilgi) + opsiyonel hedefler.
- **Zorluk = sözleşme** (Thief'in usta dokunuşu): Acemi/Usta/Hayalet seçimi sadece can
  sayısı değil, **hedef listesi** değiştirir: Hayalet'te "hiç görünme, kimseyi bayıltma,
  %90 loot" gibi şartlar eklenir. Aynı harita, üç ayrı oyun.

## 8. Kontroller (PC birinci hedef)

| Girdi | Eylem |
|---|---|
| WASD / oklar | Hareket (varsayılan: sessize yakın **yürüyüş**) |
| Shift (basılı) | **Koş** — hızlı ve gürültülü |
| C | **Çömel/gizlen** — yavaş, sessiz, zor görünür |
| E | Etkileşim: loot al, kapı aç/kapa, mum söndür |
| Sol tık | Çakıl fırlat (imlece) |
| F / sağ tık | Matara fırlat (imlece) |
| Space | Arkadan bayılt |
| M | Ses aç/kapa · R | Yeniden başlat |

Gamepad desteği Godot aşamasında eklenir (stealth kitlesi klavye ağırlıklıdır, öncelik düşük).

## 9. Prototip ↔ Tam Oyun Kapsam Tablosu

| Sistem | Prototip (bu depo) | Dikey dilim (Godot) | Sezon 1 |
|---|---|---|---|
| Işık/gölge + Işık Taşı | ✅ karo tabanlı | Godot 2D ışık/gölge (piksel-perfect) | + pencere/ay, hareketli ışık (el feneri devriyesi) |
| Zemin sesi | ✅ 4 tür | + su, cam kırığı | + ıslak iz sistemi |
| Devriye YZ | ✅ 4 durumlu | + rota varyasyonu, ikili muhabbet | + kukla (otomat) düşman sınıfı |
| Araçlar | ✅ 4 araç | + maymuncuk | + kement, keçe, dükkân |
| Bayıltma/ceset | ✅ bayılt + fark edilme | + taşıma/saklama | + "öldürme yasağı" zorluk şartı |
| Görev yapısı | tek konak, loot hedefi | tam "Kesat Zamanlar" (çok katlı, 3 giriş) | 8 görev + zorluk sözleşmeleri |
| Anlatı | başlık + görev metni | Karagöz açılış perdesi | tam senaryo, ara perdeler, mektuplar |
