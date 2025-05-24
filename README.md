# Çöp Adam Hareket Oyunu

## Proje Hakkında

Bu proje, 8086 Assembly dilinde yazılmış interaktif bir konsol oyunudur. ASCII art kullanarak çöp adam karakterini ekranda hareket ettirmeyi sağlar ve "kavuşamayan aşk" temasını programatik olarak işler.

### Oyun Mekaniği

* Erkek Karakter: 5 birim sağa-sola hareket kabiliyeti
* Kadın Karakter: Sabit konumda bekleyen hedef
* Engel Sistemi: 10 birim mesafe kaldığında yaklaşım engellenir
* Kontrol: A/D tuşları ile hareket, ESC ile çıkış

## Özellikler

* ASCII Art karakterler
* 80x25 metin modu grafikleri
* Klavye kontrolleri (A/D hareket, ESC çıkış)
* Sınır kontrolü ve collision detection
* Dinamik ekran güncellemesi
* "Kavuşamama" teması ile duygusal oyun mekaniği

## Teknik Özellikler

* Platform: DOS (16-bit)
* İşlemci: 8086/8088 uyumlu
* Bellek Modeli: Small model
* Ekran Modu: 80x25 karakter metin modu
* Stack Boyutu: 256 byte

## Kurulum ve Çalıştırma

### Gereksinimler

* DOS işletim sistemi veya DOSBox
* MASM/TASM assembler
* 8086/8088 uyumlu işlemci

### Derleme Adımları

```bash
# MASM ile derleme
masm stickman.asm
link stickman.obj
stickman.exe

# TASM ile derleme
tasm stickman.asm
tlink stickman.obj
stickman.exe
```

### DOSBox ile Çalıştırma

```bash
# DOSBox'ta
mount c: /path/to/game/folder
c:
stickman.exe
```

## Oynanış

1. Program başlatıldığında ekranda iki çöp adam karakteri görünür
2. A tuşu ile sola hareket edin
3. D tuşu ile sağa hareket edin
4. Kadın karaktere yaklaşmaya çalışın
5. 10 birim mesafe kaldığında sistem sizi durduracak
6. ESC tuşu ile oyundan çıkın

## Karakter Tasarımı

```
Erkek Çöp Adam:      Kadın Çöp Adam:
     o                    o    
    /|\                  -|-   
    / \                  / \   
```

## Kod Yapısı

### Ana Fonksiyonlar

* `draw_stickman()`: Erkek karakter çizimi
* `draw_girl()`: Kadın karakter çizimi
* `clear_old_stickman()`: Eski pozisyon temizleme
* `draw_path()`: Yol çizimi
* `move_left()`: Sola hareket kontrolü
* `move_right()`: Sağa hareket kontrolü (yaklaşım engeli dahil)

### BIOS Interrupt Kullanımı

* INT 10h: Video servisleri (ekran kontrolü)
* INT 16h: Klavye servisleri (giriş kontrolü)
* INT 21h: DOS servisleri (program sonlandırma)

## Oyun Teması

Proje, "kavuşamayan aşk" temasını teknik düzeyde kodlar:

* Erkek karakter sürekli hedefe doğru ilerler
* Kadın karakter sabit konumda bekler
* `minDistance` değişkeni (10 birim) engeli temsil eder
* `move_right` fonksiyonu yaklaşımı programatik olarak engeller

## Performans Optimizasyonları

* Minimal bellek kullanımı
* Seçici ekran güncellemesi
* Efficient karakter temizleme
* Otomatik yol onarım sistemi
