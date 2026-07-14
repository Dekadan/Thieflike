# GÖLGE OYUNU (kod adı: KUZGUN)

> *"Sayeban'da gece iki tür insana aittir: aseslere ve benim gibilere."* — Kuzgun

**Thief: The Dark Project / Thief II: The Metal Age** ruhunda, Osmanlı esintili kurgusal bir liman şehrinde geçen, ışık–gölge ve ses üzerine kurulu **2D piksel sanat gizlilik (stealth) oyunu**. Ara sahneleri geleneksel **Karagöz gölge tiyatrosu** estetiğiyle anlatılır — çünkü bu zaten bir "gölge oyunu"dur.

**Tek cümlelik konumlandırma:** *Thief'in ruhu × Karagöz'ün perdesi × Osmanlı gecesi.*

---

## Depo Haritası

| Yol | İçerik |
|---|---|
| `docs/01-vizyon-ve-konsept.md` | Oyunun ne olduğu, tasarım sütunları, tema kararı ve alternatifler |
| `docs/02-senaryo-dunya-karakterler.md` | Sayeban dünyası, fraksiyonlar, karakterler, Sezon 1 senaryosu (8 görev) |
| `docs/03-oyun-tasarimi-mekanikler.md` | Çekirdek döngü, ışık/ses sistemleri, yapay zekâ, araçlar, ekonomi |
| `docs/04-sanat-ve-ses-yonetimi.md` | Piksel sanat yönü, palet, Karagöz ara sahneleri, müzik ve SFX |
| `docs/05-hedef-kitle-ve-pazar.md` | Tür analizi (2025–26), hedef kitle segmentleri, Türkiye pazarı, fiyatlama |
| `docs/06-yol-haritasi-ve-araclar.md` | Motor seçimi (Godot), indirilecek araçlar, öğrenme sırası, kilometre taşları |
| `prototip/index.html` | **Oynanabilir prototip** — tarayıcıda aç, oyna (kurulum gerektirmez) |

## Hemen Oyna

`prototip/index.html` dosyasını herhangi bir modern tarayıcıda aç (çift tıklaman yeterli).
Klavye + fare gerekir. Kontroller başlık ekranında yazıyor.

Prototip, oyunun **çekirdek iddiasını** kanıtlamak için var: ışıkta görünür, gölgede görünmez olmak;
zemine göre ses çıkarmak; devriyeleri atlatmak; fenerleri söndürmek; keseni doldurup sırra kadem basmak.

## Durum

- [x] Konsept, dünya ve Sezon 1 senaryosu
- [x] Çekirdek mekanik tasarımı
- [x] Sanat/ses yönü ve pazar analizi
- [x] Oynanabilir tarayıcı prototipi (ışık-gölge, ses, devriye YZ, bayıltma, loot)
- [ ] Godot 4 projesine geçiş (bkz. `docs/06`)
- [ ] Dikey dilim: "Kesat Zamanlar" görevi

## İlkeler (özet)

1. **Gölge özgürlüktür** — ışık bir kaynak, karanlık bir araçtır.
2. **Ses bir sistemdir** — her zemin, her hız bir karardır.
3. **Şiddet son çaredir** — en yüksek puan, hiç dokunmadan alınır.
4. **Gerçek din yok** — Thief'in Hammerite'ı icat etmesi gibi biz de kurgusal tarikatlar kurarız; tarihî doku var, inanç istismarı yok.
5. **Şehir bir karakterdir** — Sayeban'ın damları, sarnıçları ve loncaları hikâyenin kendisidir.
