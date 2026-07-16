# GÖLGE OYUNU (kod adı: KUZGUN)

> *"Devleti kalemle soyuyorlar. Ben de kalem işindeyim sayılır."* — Kuzgun

**Yüksek konsept:** Çöken bir imparatorlukta, **imparatorluğu soyanları soyan adam.**
Oyun, Ebüzziya Tevfik'in hiç basılmamış defteri — "yazılamayan fasıl"dır; adları
(şehrinkini bile) o değiştirmiştir. Kurgusal liman payitahtı **Sayeban**'da gelirlere
**Borçhane** (Düyûn Divanı), tütüne ve kandil yağına **Reji İdaresi** el koymuştur:
mühürsüz alev yakmak suçtur. Arkalarındaki sefaretler gerçektir — İngiltere, Fransa,
Rusya. Kuzgun, gizli Şafak Cemiyeti'nin tutanaklara yazılmayan "El"idir; Muharrir
yazar, matbaa basar, El çalar. Sahnede: her biri bir sefarete yaslanan **Dört Paşa** +
Meclisçi Beşinci; peşinde: **Böcekbaşı Mürüvvet Hanım**ın hafiyeleri; kuyuda: "her şey
sayıdır" diyen **Fisagoriler**. (Kanon: `docs/07` v5 + `docs/09`.)

**Thief: The Dark Project / Thief II: The Metal Age** ruhunda, Osmanlı esintili kurgusal bir liman şehrinde geçen, ışık–gölge ve ses üzerine kurulu **birinci şahıs (POV), retro piksel-doku gizlilik oyunu**. Ara sahneleri geleneksel **Karagöz gölge tiyatrosu** estetiğiyle anlatılır — çünkü bu zaten bir "gölge oyunu"dur.

**Tek cümlelik konumlandırma:** *Thief'in ruhu × Karagöz'ün perdesi × Osmanlı gecesi.*

**İmza mekanik — FANUS:** Işığı söndürmezsin, **çalarsın.** Çaldığın alevi fanusta taşır,
istediğin yerde yeniden yakarsın: karanlığı kendin kazar, sahte ışıkla devriyeleri oyalarsın.
(Ayrıntı: `docs/03` §6 — prototipte oynanabilir durumda.)

---

## Depo Haritası

| Yol | İçerik |
|---|---|
| `docs/01-vizyon-ve-konsept.md` | Oyunun ne olduğu, tasarım sütunları, tema kararı ve alternatifler |
| `docs/07-evren-kitabi.md` | **EVREN KİTABI (güncel kanon):** Muahede Devri, Şafak Cemiyeti, ışık tekeli, Sezon 1 "Vade Gecesi" |
| `docs/02-senaryo-dunya-karakterler.md` | İlk evren taslağı (arşiv — çekirdekler 07'ye evrildi) |
| `docs/03-oyun-tasarimi-mekanikler.md` | Çekirdek döngü, ışık/ses sistemleri, yapay zekâ, araçlar, ekonomi |
| `docs/04-sanat-ve-ses-yonetimi.md` | Piksel sanat yönü, palet, Karagöz ara sahneleri, müzik ve SFX |
| `docs/05-hedef-kitle-ve-pazar.md` | Tür analizi (2025–26), hedef kitle segmentleri, Türkiye pazarı, fiyatlama |
| `docs/06-yol-haritasi-ve-araclar.md` | Motor seçimi (Godot), indirilecek araçlar, öğrenme sırası, kilometre taşları |
| `prototip/index.html` | **Oynanabilir POV prototip** — tarayıcıda aç, oyna (kurulum gerektirmez) |
| `prototip/arsiv-ustten-bakis.html` | İlk (üstten bakış) prototip — arşiv/plan aracı |

## Hemen Oyna

`prototip/index.html` dosyasını herhangi bir modern tarayıcıda aç (çift tıklaman yeterli).
Klavye + fare gerekir; fareyle bakmak için oyuna bir kez tıkla. Kontroller başlık ekranında.

Prototip, oyunun **çekirdek iddiasını** kanıtlamak için var: ışıkta görünür, gölgede görünmez
olmak; zemine göre ses çıkarmak; devriyeleri atlatmak; **alevleri fanusla çalıp yeniden
yerleştirmek**; keseni doldurup sırra kadem basmak.

## Durum

- [x] Konsept, dünya ve Sezon 1 senaryosu
- [x] Çekirdek mekanik tasarımı + imza mekanik (**Fanus**)
- [x] Sanat/ses yönü ve pazar analizi
- [x] Oynanabilir **birinci şahıs gerçek 3D** prototip (WebGL; serbest bakış, ışık-gölge, ses, devriye YZ, fanus, bayıltma)
- [x] Prototip v2 "Konak Gecesi": **piksel dokulu low-poly asesler** (zırh gömlek, kaftan, börk; asa/kılıç, diz-dirsek animasyonu), pencerelerden **ay ışığı**, mobilyalı odalar, şadırvanlı avlu, selviler, mazgallı sur; çift kanallı titreşen ışık; **konumsal ses** (rüzgâr, cırcır, çıtırtı, liman çanı, makam dronu, asa tak-tak telegrafı)
- [ ] Godot 4 (3D low-res) projesine geçiş (bkz. `docs/06`)
- [ ] Dikey dilim: "Kesat Zamanlar" görevi

## İlkeler (özet)

1. **Gölge özgürlüktür** — ışık bir kaynak, karanlık bir araçtır.
2. **Ses bir sistemdir** — her zemin, her hız bir karardır.
3. **Şiddet son çaredir** — en yüksek puan, hiç dokunmadan alınır.
4. **Gerçek din yok** — Thief'in Hammerite'ı icat etmesi gibi biz de kurgusal tarikatlar kurarız; tarihî doku var, inanç istismarı yok.
5. **Şehir bir karakterdir** — Sayeban'ın damları, sarnıçları ve loncaları hikâyenin kendisidir.
