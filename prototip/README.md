# Prototip: "Kesat Zamanlar" (birinci şahıs ön izleme)

Tek dosyalık, kurulumsuz **POV** tarayıcı prototipi. `index.html`'i çift tıkla → oyna.
(Klavye + fare gerekir; fareyle bakmak için oyuna bir kez tıkla. Ses ilk tuşla açılır.)

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

Thief çekirdeğinin (gözle-planla-sız-al-kaybol) POV'de, ve **Fanus**'un onun üstüne
bir şey kattığını. Godot'a geçerken `buildWorld()` kat planının, `updateGuard()` devriye
durum makinesinin, `computeLight()` ışık sisteminin referansıdır.
