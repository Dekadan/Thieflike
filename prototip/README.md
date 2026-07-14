# Prototip: "Kesat Zamanlar" (ön izleme dilimi)

Tek dosyalık, kurulumsuz tarayıcı prototipi. `index.html`'i çift tıkla → oyna.
(Klavye + fare gerekir; ses ilk tuşa bastığında açılır.)

## Görev

Paşa Rüstem'in konağından **en az 450 akçe** çal, sonra **kuzeydeki bahçe kapısından** kaybol.
Haritada toplam 790 akçe var — hangi odaları göze alacağın senin kararın.

## Kontroller

| Tuş | Eylem |
|---|---|
| WASD / oklar | Yürü (varsayılan: temkinli) |
| Shift | Koş — hızlı ama **gürültülü** |
| C | Çömel — yavaş, sessiz, karanlıkta zor görülürsün |
| E | Al / kapı aç-kapa / mumu söndür |
| Sol tık | Çakıl fırlat (imlece) — devriyeyi sesle oyala |
| F veya sağ tık | Matara fırlat — **fenerleri** söndürür (mumlar E ile söner) |
| Space | Arkadan habersiz devriyeyi bayılt |
| M / R | Ses aç-kapa / yeniden başla |

## Sistemin dili (Thief'in çekirdeği)

- **Işık Taşı** (alt ortadaki elmas): parlaksa görünürsün, karanlıksa yoksun.
- **Zemin konuşur:** halı ve çim susar, taş fısıldar, gıcırtılı ahşap ihbar eder
  (mutfak ahşaptır — dikkat). Ses halkanı ekranda görürsün.
- **Devriye halleri:** `?` şüphelendi (sese/silüete bakmaya gelir), `!` alarm (kovalar).
  Kaybederse arar, sonra "Kedidir kedi" deyip döner — ama tetikte kalır.
- **Duvarlar sesi boğar**, kapılar açıkken ses taşar. Kapı açmak da ses çıkarır.
- Bayılttığın asesin cesedini gören devriye alarma geçer.
- **Dereceler:** hiç görünmeden + kimseye dokunmadan bitir → *HAYALET*.

## Bu prototip neyi kanıtlıyor?

`docs/03-oyun-tasarimi-mekanikler.md`'deki çekirdek döngünün — gözle, planla, sız, al,
kaybol — 2D yukarıdan bakışta çalıştığını. Godot'a geçerken bu dosyadaki `buildWorld()`
fonksiyonu kat planının, `updateGuard()` ise devriye durum makinesinin referansıdır.
