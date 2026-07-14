# 06 — Üretim Yol Haritası ve Araç Seti

## 1. Motor Kararı: Godot 4

| Motor | Değerlendirme |
|---|---|
| **Godot 4.x** ✅ | Ücretsiz + açık kaynak (telif/abonelik derdi yok), GDScript Python kadar kolay, tek tıkla Win/Linux/Mac export, dev topluluk + bol Türkçe kaynak. **POV pivotu sonrası reçete:** Godot 3D + düşük çözünürlüklü `SubViewport` (480×270) + `nearest` filtreli piksel dokular + billboard `Sprite3D` düşmanlar. Retro FPS şablonları hazır (aşağıda). |
| Unity | Lisans güveni sarsıldı, öğrenme yükü daha çok |
| GZDoom / Doom motoru | Retro POV'nin en otantiği ve harita editörü müthiş; ama gizlilik YZ'si/ışık-gameplay bağı için motoru eğmek gerekir — ikinci aday olarak cepte dursun |
| Löve2D / MonoGame | Saf kod; her şeyi elle yazarsın — öğrenme projesi olur, ürün gecikir |

**Godot retro-FPS hızlandırıcıları:** itch.io/GitHub'da "Godot Retro FPS template",
"Godot PSX style shader" aramaları hazır başlangıç projeleri verir (ör. düşük çözünürlük
+ doku titremesi shader'ları). Prototipteki karo bazlı ışık haritası mantığı GDScript'e
birebir taşınır: ışık DEĞERİ gameplay içindir, görsel ışık ayrı katmandır.

**İndir:** https://godotengine.org/download (standart sürüm yeterli, .NET gerekmez).

## 2. Araç Çantası (hepsi indirilebilir, çoğu ücretsiz)

| İş | Araç | Not |
|---|---|---|
| Piksel sanat | **Aseprite** (~20$, https://www.aseprite.org) | Endüstri standardı; ücretsiz alternatif: **LibreSprite**, **Piskel** (tarayıcı) |
| Seviye editörü | **LDtk** (ücretsiz, https://ldtk.io — Dead Cells tasarımcısından) veya **Tiled** (https://www.mapeditor.org) | İkisinin de Godot içe aktarıcısı var |
| SFX | **jsfxr** (https://sfxr.me), **ChipTone** | Prototip cızırtıları için; gerçek SFX'e geçişte **freesound.org** (CC0 filtresiyle) |
| Ses düzenleme | **Audacity** (ücretsiz) | Kayıt + temizlik |
| Müzik | **LMMS** (ücretsiz) / Reaper (ucuz) | Makam esintili ambiyans için başlangıç; sonra besteci komisyonu |
| Hazır asset | **Kenney.nl** (CC0, greybox için), **itch.io asset** pazarı, **OpenGameArt** | Lisansı MUTLAKA oku; CC0 > CC-BY > ticari |
| Font | TR glifli piksel font şart (ş, ğ, ı, İ, ç, ö, ü!) | Satın almadan önce "Turkish/Latin Extended" desteğini test et; gerekirse FontForge ile glif ekle |
| Sürüm kontrol | Git + GitHub (bu depo) | Godot projesinde `.godot/` klasörünü `.gitignore`'a ekle |
| Konsept/pano | Pinterest/ArtStation panosu + PureRef | `04`'teki mimari referans listesini doldur |

## 3. Öğrenme Sırası (sıfırdan, ~6-8 hafta yarı zamanlı)

1. **Hafta 1-2 — Godot alfabesi:** Resmî "Your first 2D game" + "Your first 3D game"
   eğitimleri (docs.godotengine.org) → GDQuest'in ücretsiz "Learn GDScript From Zero" uygulaması.
2. **Hafta 3-4 — POV temelleri:** Bir "Godot FPS controller" serisi bitir (fare bakışı,
   çarpışma, merdiven). Retro görünüm: SubViewport 480×270 + nearest doku filtresi.
   Bu aşamada prototipteki konağı Godot'da **GridMap + gri kutularla** yeniden kur (aynı plan!).
3. **Hafta 5-6 — Işık ve YZ:** Karo bazlı ışık haritasını GDScript'e taşı (prototipteki
   `computeLight()` birebir çevrilir); `NavigationAgent3D` + durum makinesiyle devriye
   (`03`'teki şema); Işık Taşı HUD'ı.
4. **Hafta 7-8 — His + Fanus:** ayak sesi/zemin sistemi, E-kanalı ile alev çalma,
   alev fırlatma, devriyenin ışık değişimi tepkisi. Sonuç: **M1 tamam** demektir.
5. **Sürekli:** Mark of the Ninja GDC konuşması ("Empowering the Player in a Stealth Game"),
   Thief post-mortem yazıları, Monaco/Intravenous incelemesi — haftada bir "usta işi" analiz et.

## 4. Kilometre Taşları

| Taş | İçerik | Bitti sayılma ölçütü | Süre (yarı zamanlı) |
|---|---|---|---|
| **M0 — Kanıt** ✅ | Bu depodaki tarayıcı prototipi | Çekirdek döngü hissediliyor mu? Arkadaşların "bir tur daha" diyor mu? | tamam |
| **M1 — Godot iskeleti** | Prototipin Godot'da gri kutu eşleniği | Aynı konak, aynı his, 60fps | 6-8 hafta |
| **M2 — Dikey dilim** | "Kesat Zamanlar" tam görev: 3 giriş, 2 kat, zorluk sözleşmesi, Karagöz açılışı | Yabancı biri yardımsız oynayıp bitiriyor | +3 ay |
| **M3 — Sanat geçişi** | Gri kutu → piksel sanat + ses paketi v1 | Ekran görüntüsü "wishlist'lenebilir" kalitede | +2-3 ay |
| **M4 — Demo** | Steam sayfası + Next Fest demosu | 1000+ wishlist ilk ay | +2 ay |
| **M5 — Sezon 1** | 8 görev, tam senaryo | İçerik kilidi → cila → çıkış | +8-12 ay |

**Toplam gerçekçi ufuk:** yarı zamanlı tek kişi için ~2 yıl; M3'ten sonra piksel sanatçısı
ve besteci komisyonu ile kısalır. Bu normaldir — Sandfox 5+ yıl sürdü, biz kapsamı ona göre kırptık.

## 5. Bütçe Kalemleri (asgari senaryo)

| Kalem | Tahmin |
|---|---|
| Aseprite + araçlar | ~30 $ |
| Piksel sanatçı komisyonu (kimlik parçaları: kahraman seti, kapak, Karagöz kuklaları) | 800–2500 $ |
| Müzik/SFX komisyonu (20-30 dk ambiyans + SFX paketi) | 1000–3000 $ |
| TR/EN yerelleştirme redaksiyonu + seslendirme (Kuzgun + Hayalî) | 500–1500 $ |
| Steam kayıt ücreti | 100 $ |
| Tarih danışmanı okuma ücreti (duyarlılık kontrolü) | 100–300 $ |

Erken aşamada sıfır harcamayla ilerlenebilir (greybox + kod çizimi + jsfxr); para ancak
M3'te gerekir — o zamana kadar demo/wishlist gücüyle yayıncı görüşmesi de bir seçenek
(nişe uygun butik yayıncılar: New Blood tarzı retro-severler, Top Hat Studios vb.).

## 6. Bu Depodan Devam Etme Talimatı

1. `prototip/index.html`'i oyna; hissi not al (neresi gergin, neresi sıkıcı?).
2. Godot'u indir; `docs/06` §3'teki öğrenme sırasını izle.
3. Godot projesini bu depoda `godot/` klasörüne başlat; prototipteki konak planını
   TileMap'e taşı (plan `prototip/index.html` içindeki `MAP` dizisinde ASCII olarak duruyor).
4. Her kilometre taşında `docs/`'u güncelle — tasarım dokümanı yaşayan belgedir.
