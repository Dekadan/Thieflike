# Prototip: "Kesat Zamanlar" (birinci şahıs 3D ön izleme)

Tek dosyalık, kurulumsuz **gerçek 3D (WebGL)** tarayıcı prototipi.
`index.html`'i çift tıkla → oyna. (Klavye + fare gerekir; fareyle bakmak için oyuna bir
kez tıkla. Ses ilk tuşla açılır. WebGL destekli güncel tarayıcı ister — hepsi destekler.)

**v2 "Konak Gecesi"** — kutu-gövde görünüm emekliye ayrıldı (Thief 1998 reçetesi:
düşük poligon + piksel doku, bkz. `docs/04`):

- **Dokulu asesler:** incelen (frustum) uzuvlar; zırh gömlek, düğmeli-kaytanlı kaftan,
  kuşak, şalvar, çizme, yüz (kaş-göz-pos bıyık) ve sarıklı börk piksel dokuyla giydirildi.
  Yürüyüşte diz/dirsek bükülür; devriyede **asa** taşır (yere tak-tak vurur — duyarak
  takip et), alarmda **kılıç** çeker. Bayıltınca börkü yana yuvarlanır.
- **Zengin konak:** kafesli pencerelerden içeri **ay ışığı havuzları** düşer (gizlilik
  kuralına dahildir — ayazda da görünürsün); odalarda divanlar, sini sofrası, minderler,
  kitap rafları, sandıklar, mermer kaideler, yolluklar, tavan kirişleri, İznik çini
  bordürlü sıva; avluda **şadırvan**, bahçede **selviler**, surda mazgallar.
- **Çift kanallı ışık:** kandil sıcağı ↔ ay soğuğu ayrı hesaplanır, alevler gerçekçe
  titrer; ışık havuzları 2× çözünürlükte, yumuşak kenarlı.
- **Kulakla oynanır:** tüm efektler **konumsal** (stereo pan + duvar boğması). Rüzgâr,
  cırcır böcekleri, ocak çıtırtısı, uzak liman çanı, baykuş; Nihavend dronu ve
  şüphe/alarmda yükselen gerilim katmanı. Zemine göre ayak sesi setleri; devriyelerin
  adımları ve asa telegrafı görmeden duyulur.

İlk üstten bakış denemesi `arsiv-ustten-bakis.html`'de arşivlidir — devriye rotalarını
kuşbakışı okumak için hâlâ faydalı bir tasarım aracı.

## Görev

Paşa Rüstem'in konağından **en az 450 akçe** çal, sonra **kuzeydeki bahçe kapısından** kaybol.
Haritada toplam 790 akçe var — hangi odaları göze alacağın senin kararın.

## Kontroller

| Girdi | Eylem |
|---|---|
| Fare | Bak (tıklayıp kilitle) |
| WASD | Yürü / yan adım (varsayılan: temkinli) |
| Shift | Koş — hızlı ama **gürültülü** |
| C | Çömel — yavaş, sessiz, alçak |
| E | Al / kapı aç-kapa |
| **E (basılı tut)** | **Alevi fanusla ÇAL** (~1 sn, kımıldamadan) |
| **Sol tık** | **Fanustaki alevi fırlat** — düştüğü yerde yeniden yanar |
| Q / sağ tık | Çakıl fırlat (ses tuzağı) |
| Space | Arkadan habersiz devriyeyi bayılt |
| TAB (basılı) | Kat planı |
| 1 / 2 | Parlaklık azalt / artır (kalıcı; oyun dengesini etkilemez) |
| M / R | Ses aç-kapa / yeniden başla |

## FANUS — imza mekanik

Thief'in su oku ışığı *yok eder*; fanus ışığı **mala çevirir**:

- **Karanlık kaz:** Rotandaki fenerleri sök, geçilmez koridoru geçilir yap.
- **Sahte ışık tuzağı:** Alevi boş odaya fırlat — "Bu ışık da nereden çıktı?" diyen ases
  oraya yürür, sen ters kapıdan geçersin.
- **Bedeli var:** Çalarken 1 sn kımıldayamazsın; ışığın söndüğünü ya da yoktan yandığını
  **gören** devriye şüphelenir; dolu fanus elini aydınlatır.

## Sistemin dili (Thief'in çekirdeği)

- **Işık Taşı** (alt ortadaki elmas): parlaksa görünürsün, karanlıksa yoksun.
- **Zemin konuşur:** halı ve çim susar, taş fısıldar, gıcırtılı ahşap ihbar eder (mutfak!).
- **Devriye halleri:** `?` şüphe (bakmaya gelir) → `!` alarm (kovalar) → arama →
  "Kedidir kedi." Ama artık tetiktedir. Crosshair üstündeki ibre dolarsa görüldün demektir.
- **Duvarlar sesi boğar;** kapılar açıkken ses taşar; kapı açmak da ses çıkarır.
- Bayılttığın asesi gören devriye alarma geçer. Hiç görünmeden + dokunmadan bitir → **HAYALET**.

## Bu prototip neyi kanıtlıyor?

Thief çekirdeğinin (gözle-planla-sız-al-kaybol) gerçek 3D birinci şahısta çalıştığını,
ve **Fanus**'un onun üstüne bir şey kattığını. Godot'a geçerken `buildWorld()` kat planının,
`updateGuard()` devriye durum makinesinin, `computeLight()` çift kanallı ışık sisteminin,
`buildGuardParts()`/`drawGuard()` düşük poligon + piksel doku karakter dilinin,
`audioInit()`/`updateAudio()` ise konumsal ambiyans katmanlarının referansıdır.
