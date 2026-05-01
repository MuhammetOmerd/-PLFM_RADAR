# PLFM RADAR Sistemi
**Yazar ve Baş Donanım Tasarımcısı:** muham

## Projeye Genel Bakış
Bu depo, özel yüksek frekanslı bir PLFM (Faz Kilitli Frekans Modülasyonu - Phase-Locked Frequency Modulation) Radar sistemi için eksiksiz donanım tasarımını, sistem mimarisini ve elektromanyetik simülasyonları içerir. Sıfırdan tasarlanan bu sistem X-bandında (yaklaşık 10.5 GHz) çalışmaktadır ve ilk RF/Mikrodalga simülasyonlarından nihai PCB dizilimi ve Gerber üretim dosyalarına kadar tüm aşamaları kapsamaktadır.

## Temel Alt Sistemler ve Mimari
Radar sistemi, gürültüyü en aza indirmek ve RF performansını artırmak için son derece modüler bir yapıda tasarlanmış olup birkaç özel karta bölünmüştür:

1. **Ana Kart (Main Board):** Temel veri işleme, ADC/DAC (Analog-Dijital / Dijital-Analog) dönüşümleri ve genel sistem kontrolünü yönetir.
2. **Frekans Sentezleyici Kartı (Frequency Synthesizer Board):** RF mikser için hassas chirp sinyalleri ve lokal osilatör (LO) frekansları üretmekten sorumludur.
3. **Güç Yükseltici Kartı (Power Amplifier - PA Board):** İletim anteni için modüle edilmiş RF sinyalini yükseltir.
4. **Güç Yönetim Kartı (Power Management Board):** Tüm hassas RF ve dijital bileşenlere temiz, düşük gürültülü güç dağıtımı sağlar.
5. **Antenler:** Yüksek yönlülük (directivity) için özel olarak tasarlanmış 10.5 GHz quartz yarıklı dalga kılavuzu (slotted waveguide) antenleri.

## Kullanılan Araçlar ve Yöntemler
- **PCB Tasarımı ve Şemalar:** Hassas empedans uyumuna sahip gelişmiş çok katmanlı yığınlar (RO4350B tabanlar).
- **EM Simülasyonları:** Yarıklı dalga kılavuzu ve via çit (via fencing) tasarımlarının 3D elektromanyetik simülasyonları için openEMS kullanılmıştır.
- **Sinyal İşleme:** Temel bant analizi, DAC yeniden yapılandırması ve chirp sinyali üretimi için Python (NumPy, Pandas, Matplotlib).

## Dizin Yapısı (Klasörler)
- `1_Project_Description/`: Detaylı sistem gereksinimleri ve teknik özellikler.
- `2_Functional Diagram & Interconnection Matrices/`: Sistem düzeyinde blok şemalar ve pin bağlantı matrisleri.
- `3_Power Management/`: Güç ağacı hesaplamaları ve voltaj regülatörü tasarımları.
- `4_Schematics and Boards Layout/`: Eksiksiz devre şemaları, kart dizilimleri ve üretim dosyaları (Gerber, BOM, Pick & Place).
- `5_Simulations/`: IF (Ara Frekans) filtreleri, Örtüşme Önleyici (Anti-Aliasing) filtreler ve 3D anten simülasyonları için veri ve kod dosyaları.

## Simülasyonların Çalıştırılması
Sinyal işleme simülasyonlarını sorunsuz çalıştırmak için bir Python sanal ortamı (`.venv`) yapılandırılmıştır. Çoklu rampa DAC chirp sinyali çıktısı üretmek için aşağıdaki komutu çalıştırabilirsiniz:
```bash
python 5_Simulations/DAC_ReconstructionFilter/Generate_ChirpcsvFile.py
```

---
*Tüm sistem tamamen bu bilgisayarda muham tarafından tasarlanmış ve geliştirilmiştir.*
