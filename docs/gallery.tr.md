# Hazır ayar galerisi

Bu galeride sabit örnek sesle, gerçek QML bileşeninden alınmış ekran görüntüleri bulunur. Her pano tek yakalamadır: hazır ayarlar ortak bir duvar kâğıdı üzerinde 2× çözünürlükte birlikte çizilir; sonradan ölçekleme veya birleştirme yapılmaz.

`make gallery` komutuyla galeriyi yeniden oluşturun. Yakalamalar Qt'nin yazılım çizicisini kullanır; yalnızca GPU'da çalışan bulanıklık, yansıma ve gölgelendirici efektleri gösterilmez. Masaüstünde OpenGL yakalamaları için `make gallery GALLERY_FLAGS="--backend opengl --platform wayland"` komutunu çalıştırın.

## Klasik kartlar

- **Classic** — Varsayılan görünüm; mevcut kullanıcılar için değişiklik yok.
- **Glass Classic** — Alışıldık düzen, buzlu cam kart ve yumuşak yükselti efekti.
- **Cover Art** — Albüm kapağı kartı doldurur; keskin küçük görsel üstte kalır.
- **Neon Night** — Koyu renk tonu, aynalı çubuklar ve parlayan nabız çubuğu.

## Yüzeyler ve oynatıcılar

- **Soft Solid** — Sıcak mineral yüzey ve net koyu metin; bulanıklık gerekmez.
- **CD Player** — Dönen disk görseli, kıvrımlı arama çubuğu ve parça ayrıntıları için ters dönen kart.
- **Vinyl** — Çalarken dönen plak, parıltılar ve kapaktan alınan renkler.
- **Arcade** — Yüksek tepe değerli LED ölçer, keskin görsel ve yalnızca süre göstergesi.

## Katmanlı cam

- **Liquid Glass** — İşaretçiyi izleyen ince kenarlı şeffaf cam; renkler kapaktan alınır.
- **Quiet Glass** — Ön planda parça adı, sakin aynalı çubuklar, tek yumuşak vurgu ve yuvarlak oynat düğmesi.
- **Album Atmosphere** — Kapak renkleri karta yayılır ve vurgu rengini belirler.
- **Lyrics Card** — Sanatçının altında eşzamanlı söz satırı, Ribbon dalgası ve kapak renk paleti.

## Posterler ve öne çıkan görünümler

- **Poster** — Büyük başlık, arka planda yumuşak müzik dokusu ve büyük saat.
- **Poster · Hanging bars** — Üst kenardan sarkan çubukların önünde ortalanmış iki satırlı başlık.
- **Stalactites** — Tepe çubukları üst kenardan sarkıp başlığa doğru uzanır; buz renk paleti.
- **Hero Wave** — Görselleştirici merkezde, parça bilgileri altında.

## Yörüngeler ve şarkı sözleri

- **Orbit** — Ortada kapak; çevresinde yavaşça dönen çubuklar ve basla birlikte büyüyüp küçülen kapak.
- **Halo** — Yumuşak şerit hâlesi içindeki dönen plak ve ilerleme halkası; Iris renk paleti.
- **Sunburst** — Her vuruşta kapaktan kıvılcımlar saçılır; koyu ton üzerinde Ember paleti.
- **Lyrics only** — Okuma alanı, çevredeki satırlar, belirgin geçerli satır ve otomatik kaydırma. LRCLIB'den çevrim içi sözler.

## İnce ve minimal

- **Slim Strip** — Ekranın alt kısmı için geniş ve alçak çubuk.
- **Mirrored Minimal** — Sağda görsel, noktalı ilerleme, kart yok; denetimler üzerine gelince görünür.
- **Compact** — Görsel sütunu yok; yalnızca görselleştirici, ilerleme ve parça adı.
- **Silk Ribbon** — Bas şeridi kalınlaştırır, orta frekanslar büker, tizler lifleri aydınlatır.

## Panel düzenleri

- **Panel Pill** — Plasma panelleri için sade metin kapsülü. Statik EQ; animasyon maliyeti yok.
- **Ribbon Pill** — Panel içinde parıltılı ipek şerit; Aurora paleti.
- **Bar Icon** — Hyprland çubuğu için ilerleme halkalı kapak görseli.
- **Orbit Icon** — Çubukta, kapak çevresinde küçük radyal halka.
