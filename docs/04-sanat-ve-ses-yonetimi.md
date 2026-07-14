# 04 — Sanat ve Ses Yönetimi

## 1. Görsel Kimlik: "Kandil ışığında piksel" — POV sürümü

Kullanıcı vizyonu net: **POV görünüm + piksel tarzı korunacak, ama daha hoş görünecek.**
Çeviri: 1998'in "software-render" bakışı, bugünün eliyle — düşük çözünürlüklü birinci şahıs,
piksel dokular, kuantalanmış ışık (Gloomwood/Dusk/Cruelty Squad okulunun atmosferik kanadı).

- **Ekran keskin, doku retro:** ekran tam çözünürlük (yazılar cam gibi), dünya dokuları
  32×32 px el boyaması — Thief 1998'in gerçek reçetesi budur (düşük doku, net ekran).
- **Karakterler: kutu-gövde low-poly** (prototipte kanıtlandı): kafa/gövde/bacak/kol
  kutuları + yüz dokusu (göz-kaş-bıyık) + börk. PS1/N64 dönemi insan hissi — piksel
  sanat becerisiyle üretilebilir, animasyonu programatik (bacak salınımı, eğilme).
  Godot'ta bir tık yukarısı: aynı oranlarda düşük poligon gövde + piksel doku giydirme;
  Kukla (otomat) düşmanlar bu dile zaten mükemmel oturur (köşeli, mekanik).
- **Işık kuantalanır:** parlaklık 8 kademeye yuvarlanır (banding = estetik imza),
  kaynak yakını amber, gölge mavi; mesafe sisi karanlığa değil laciverte düşer.
- **Siluet kuralı:** Her varlık dış hattından tanınmalı — oyun çoğu zaman karanlık.
  Karagöz disipliniyle: perde figürü gibi çiz.
- **El varlığı:** Ekranın sağ altında Kuzgun'un eli + **fanus** — içindeki çalıntı alevler
  gerçek zamanlı yanar. Oyuncunun gözü sürekli orada; oyunun poster karesi budur.

## 2. Renk Paleti (Thief II gecesinin Sayeban çevirisi)

Ana fikir: **soğuk gece ↔ sıcak kandil** çatışması. Gölge maviye, tehlike ışığı ambere aittir.

| Rol | Hex | Not |
|---|---|---|
| Gece zemini (en koyu) | `#0b0e1a` | saf siyah asla kullanma |
| Gölge mavisi | `#1c2333` / `#2a3247` | duvar/zemin karanlık tonları |
| Ay çeliği | `#4a5a74` | ay ışığı vurguları, metal |
| Kandil amberi | `#ffb347` → `#ffe9a8` | ışık kaynağı çekirdek/hale |
| Halı laли | `#5a2330` / `#7c3140` | kilim, perde, kaftan astarı |
| Ases kırmızısı | `#a04030` | devriye üniforması (okunabilirlik: düşman = kızıl) |
| Kuzgun fümesi | `#3f4f5c` | oyuncu pelerini (gölgeyle akraba ama seçilebilir) |
| Loot altını | `#ffd76a` + parıltı beyazı | yalnızca değerli şeyler bu rengi alır (kutsal kural) |
| Yaban yeşili | `#3e6b4f` | bitki, Yeşil Pir sahneleri |
| Kukla bakırı | `#b87333` | otomatlar; amber ışıkta "yanlış" parlar (tekinsizlik) |

**Kural:** Altın sarısı UI'da ve loot dışında hiçbir yerde kullanılmaz — göz, parıltıyı
refleksle "değer" diye okusun.

## 3. Karagöz Perdesi: Anlatı Dili (projenin imzası)

Ara sahneler, ana menü, ölüm/zafer ekranları ve rüya bölümleri **gölge tiyatrosu** olarak
sahnelenir:

- Arkadan aydınlatılmış bez perde dokusu (hafif dalgalanma shader'ı),
- Karakterler deri kukla gibi: tek renk silüet + eklem yerlerinden oynayan parçalı animasyon
  (Spine/Godot Skeleton2D ile ucuz üretilir),
- Sahne geçişlerinde tef/kudüm vuruşu; anlatıcı ("Hayalî") sesli betimleme yapar —
  Thief'in çizgi-kolaj ara sahnelerinin bizdeki karşılığı, ama bizimki **kültürel olarak bizim**.
- Bonus: Karagöz oynatma lisansı/telifi diye bir şey yok — gelenek kamu malı; sadece
  kendi özgün figürlerimizi çizeriz (Kuzgun kuklası, Saatçi kuklası...).

## 4. Mimari ve Mekân Referans Listesi (görsel araştırma klasörü için)

- **Konak/köşk:** cumbalı cepheler, taşlık-avlu, harem/selamlık ayrımı → doğal iki-rota tasarımı.
- **Bedesten/arasta/kapalıçarşı:** kubbeli sokaklar, kepenkli dükkânlar, dam silueti (Görev 6).
- **Sarnıç (Bin Direk):** sütun ormanı + su yansıması — ışık oyunlarının vitrini (Görev 3).
- **Saat kulesi:** finalin düşey seviyesi; çark odaları, sarkaç boşluğu (Görev 8).
- **Hamam, kahvehane, liman zindanı, tersane:** yan görev mekânları.
- **Kullanılmayacaklar:** cami/mescit/türbe iç mekânları, gerçek dinî semboller (bkz. 01 ilkeler).
  Kubbe silüeti şehir panoramasında mimari doku olarak uzakta kalabilir; oynanır alan olamaz.

## 5. Animasyon Öncelik Listesi (az ama öz)

1. Kuzgun: yürüme/sessiz yürüme/koşma/çömelme (4 yön), bayıltma vuruşu, loot alma eğilmesi.
2. Devriye: yürüme, duraksama-etrafa bakınma (şüphe okunur olmalı!), alarm koşusu, yere yığılma.
3. Işık: fener alev titremesi (2-3 kare), sönme dumanı.
4. Loot parıltısı (4 kare yıldız).
5. Kukla (Sezon 1 ortası): tek düze kayar yürüyüş — insan animasyonundan bilinçli olarak
   *daha pürüzsüz* = tekinsiz vadi hissi.

## 6. Ses Yönetimi

**İlke: Bu oyun kulakla oynanır.** Ses bütçesi görselden önce gelir.

- **Müzik:** Makam esintili karanlık ambiyans — Nihavend/Hüseynî merkezli, ney + tanbur +
  su damlası + uzak liman çanları; gerilim katmanı (şüphe/alarm durumunda yükselen
  perdeli katman — dikey remix tekniği). Referans ruh: Thief'in Eric Brosius ambiyansı ×
  taksim geleneği. (Telifli eser örnekleme YOK; özgün beste veya lisanslı çalışma.)
- **SFX önceliği:** ayak sesi setleri (zemin başına 3-4 varyasyon), kapı gıcırtısı,
  fener cızırtısı-sönmesi, çakıl tıkırtısı, kumaş hışırtısı, bayıltma "puf"u, alarm düdüğü
  (asesler gerçekte düdük/asa vururdu — asa tak-tak sesi devriye habercisi olsun: oyuncu
  devriyeyi görmeden **duyar**).
- **Seslendirme:** Kuzgun iç monologları (TR ana dil + EN dublaj hedefi). Devriye bark'ları
  bol varyasyonlu; yazım `02`'de. Kukla sesleri: vokoder/metalik TTS estetiği.
- **Karagöz sahneleri:** tek anlatıcı ses (Hayalî) her şeyi taklit eder — geleneksel tek-adam
  performansı hem otantik hem ucuz (tek ses oyuncusu bütçesi).

## 7. Asset Üretim Stratejisi (sıfır çizim tecrübesiyle yol)

1. **Graybox aşaması:** renkli kutular + bu prototipteki gibi kod-çizimi; sanat sıfır.
2. **Öğrenilebilir çekirdek:** 16×16 karo setleri piksel sanatın en öğrenilebilir dalıdır.
   Aseprite + "Pixel Pete" / Saint11 (Pedro Medeiros) ders serileri; günde bir karo hedefi.
3. **Satın al/uyarla:** itch.io'da "top-down interior/medieval/arabian" karo setleri CC0/ticari
   lisansla mevcut; **paletimize boyayarak** tutarlılaştır (palet swap = ucuz kimlik).
4. **Komisyon:** Kimlik parçaları (Kuzgun sprite'ı, Karagöz kuklaları, kapak resmi) tecrübeli
   piksel sanatçısına sipariş — en yüksek getirili harcama kalemi.
5. **Üretken YZ notu:** ara doku/konsept eskizi için iç kullanımda serbest; nihai oyun içi
   asset olarak kullanılacaksa mağaza kurallarına uygun beyan gerekir (Steam YZ beyanı) ve
   stil tutarlılığı için elle rötuş şart. Kimlik parçalarında (karakter, kapak) insan eli tercih.
