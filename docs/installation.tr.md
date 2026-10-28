# Görselleştiriciyi kurma ve kullanma

Kullandığınız ortamı seçin: [KDE Plasma](#kde-plasma) veya [Hyprland / Quickshell](#hyprland--quickshell). Her ikisi de aynı widget düzenlerini ve ayar stüdyosunu kullanır.

## Gereksinimler

- Ses tepkili görseller için `cava` ve çalışan bir PipeWire veya PulseAudio sunucusu.
- Tarayıcı site adları, kuyruk ayrıntıları ve diğer MPRIS üst verileri için Plasma oturumunun `PATH` değişkeninde Python 3 ve `busctl`.
- util-linux paketinden `flock` ve procps paketinden `pkill`.
- KDE Plasma 6 (`kpackagetool6`) veya Hyprland ortamı için Quickshell (`qs`).

MPRIS oynatma bilgileri medya oynatıcınızdan alınır. Hiçbir oynatıcı parça üst verisi yayımlamasa bile ses çubukları çalışabilir.

## KDE Plasma

[KDE Store](https://www.opendesktop.org/p/2359422/) üzerinden kurun veya depoyu klonlayıp paketi yükleyin:

```bash
git clone https://github.com/Muddyblack/audio-wave-visualizer.git
cd audio-wave-visualizer
kpackagetool6 -t Plasma/Applet -i package
```

Plasma'nın **Gereç Ekle** panelinden **Plasma Audio Visualizer** öğesini ekleyin. Elle yapılan kurulumu güncellemek veya kaldırmak için:

```bash
kpackagetool6 -t Plasma/Applet -u package
kpackagetool6 -t Plasma/Applet -r org.muddyblack.plasmaAudioVisualizer
```

Paketlenmiş bir `.plasmoid` oluşturmak için `make pack` kullanın; arşiv depo kök dizinine yazılır.

## Hyprland / Quickshell

Hyprland oturumunda bu depodaki widget'ı çalıştırın:

```bash
make view-hyprland
```

`qs` komutu `PATH` içinde bulunuyorsa `hyprland/run.sh` kullanılır. Aksi hâlde Make hedefi, Quickshell ve bağımlılıklarını sağlamak için Nix flake'i kullanır. KDE Plasma gerekmez. Widget ilk monitörde uygulama pencerelerinin altında başlar; durdurmak için terminalde **Ctrl+C** tuşlarına basın.

**Ayarlar**'ı açmak için widget'a sağ tıklayın. Widget gizliyse `make settings-hyprland` komutunu çalıştırın. Bir monitör veya **Tüm ekranlar** seçeneğini belirleyin, widget'ı konumlandırın ve **Uygula**'ya tıklayın. Tercihler `~/.config/audio-wave-visualizer/hyprland.json` dosyasına (veya `$XDG_CONFIG_HOME` altına) kaydedilir. Tüm ekranlar tek bir ses arka ucunu paylaşır.

Oturum açıldığında başlatmak için Hyprland yapılandırmanıza deponun gerçek yolunu yazarak şu satırı ekleyin:

```ini
exec-once = bash /absolute/path/to/audio-wave-visualizer/hyprland/run.sh
```

Hyprland için varsayılan hız 15 Hz'dir. **Ayarlar → Ses** bölümünde daha az kaynak tüketimi için düşük, daha akıcı hareket için yüksek kare hızı seçin. Varsayılan widget boyutu 360 × 104'tür; konum ve boyut `shell.qml` içinde de ayarlanabilir.

## Ayarlar ve hazır ayarlar

Yerleşik stüdyo, düzenleme sırasında değişiklikleri önizler. **Uygula** veya **Tamam** değişiklikleri kaydeder; **İptal** vazgeçer. Quickshell'de açmak için widget'a sağ tıklayın. Plasma'da widget'ın yapılandırmasını açın.

Bir görünümü paylaşmak için **Hazır ayarlar → Hazır ayarlarım** bölümünde **JSON olarak kopyala** seçeneğini kullanın; ardından diğer arayüzde **JSON içe aktar**'ı seçin. Ayrıntılar için [hazır ayar paylaşımı](sharing-presets.tr.md) belgesine bakın. Yerel dosyalar, LRCLIB, çeviriler ve zamanlama hakkında bilgi için [şarkı sözü kılavuzunu](lyrics.tr.md) inceleyin.

## Sorun giderme

Parça bilgileri çalışıyor ancak çubuklar hareket etmiyorsa `cava` durumunu kontrol edin: MPRIS üst verileri ile ses yakalama birbirinden bağımsızdır. Tanılama komutunu çalıştırın:

```bash
make doctor
```

Kurulu bir Plasma widget'ı için `bash ~/.local/share/plasma/plasmoids/org.muddyblack.plasmaAudioVisualizer/contents/code/doctor.sh` komutunu çalıştırabilirsiniz. Sorun bildirirken çıktıyı ekleyin.

| Belirti | Kontrol |
| --- | --- |
| `cava is not installed` | Dağıtımınızın paket yöneticisiyle `cava` kurun. Widget otomatik olarak yeniden dener. |
| `No usable audio input` | PipeWire veya PulseAudio'nun çalıştığını ve `cava` derlemenizin bunu desteklediğini doğrulayın. |
| Çubuklar sabit veya çok sönük | **Ayarlar → Ses** bölümünde **Hassasiyet** değerini artırın veya **Yumuşatma** değerini azaltın. |
| Hyprland'de widget gizli | `make settings-hyprland` komutunu çalıştırıp monitör ve konum ayarlarını kontrol edin. |

Plasma besleyicisi `cava.log` dosyasını `$XDG_RUNTIME_DIR/audio-wave-widget/` altına yazar. Quickshell durum ve günlük dosyalarını `$XDG_RUNTIME_DIR/audio-wave-quickshell/` altında tutar.
