# İleri Gömülü Sistemler – Laboratuvar Çalışmaları

**Öğrenci:** Berkay Derin – 2510140024  
**Ders:** İleri Gömülü Sistemler (Dr. Murat Sürücü)  
**Kart:** ESP32-S3-N16R8 (DevKitC-1 düzeni), işlemci saati 240 MHz  
**Araçlar:** ESP-IDF v6.1, Windows

## Laboratuvar 2 – GPIO, kesme ve zamanlayıcılar

Rapor: [`lab2/Lab2_Rapor.pdf`](lab2/Lab2_Rapor.pdf)

| Klasör | İçerik |
|---|---|
| `lab2/ortak/` | Register adresleri ve `gpio_cikis_ayarla()` (lab_reg.h) |
| `lab2/lab2_gpio_hiz/` | Görev 1 (register / gpio_config karşılaştırması) ve Görev 2 (üç erişim yönteminin hızı) |
| `lab2/lab2_buton/` | Görev 3 (BOOT düğmesi kesmesi ve sıçrama ölçümü) |
| `lab2/lab2_zamanlayici/` | Görev 4 (GPTimer ve esp_timer karşılaştırması) |
| `lab2/hist_ciz.py` | Görev 4 histogram çizimi |
| `lab2/olcum/` | Monitör kayıtları, objdump çıktısı ve histogram.png |

### Ölçüm dosyaları (`lab2/olcum/`)

| Dosya | Görev |
|---|---|
| `g1_register_karsilastirma.txt` | G1: `GPIO_MODE_OUTPUT` ile açılış registerları |
| `g1_input_output_denemesi.txt` | G1: `GPIO_MODE_INPUT_OUTPUT` denemesi |
| `g2_hiz_olcumu.txt` | G2: sürücü / yapı / register çevrim sayıları |
| `g2_disasm.txt` | G2: `degistir_*` ve `gpio_set_level` derlenmiş kodu |
| `g3_boot_dugmesi_sessizlik20.txt` | G3: BOOT düğmesi, SESSIZLIK_MS = 20 |
| `g3_kablo_sessizlik20.txt` | G3: kablo temasıyla sıçrama, SESSIZLIK_MS = 20 |
| `g3_sessizlik1.txt`, `g3_sessizlik50.txt` | G3: SESSIZLIK_MS = 1 ve 50 karşılaştırması |
| `kayit_wifi_kapali.txt`, `kayit_wifi_acik.txt` | G4: monitör kayıtları |
| `histogram.png` | G4: `python hist_ciz.py kayit_wifi_kapali.txt kayit_wifi_acik.txt` çıktısı |

Ölçümler lojik analizör kullanılmadan, konsol çıktısı, CPU çevrim sayacı (`esp_cpu_get_cycle_count`) ve `esp_timer` ile alınmıştır.

### Derleme

```
cd lab2/lab2_gpio_hiz
idf.py set-target esp32s3
idf.py -p COMx flash monitor
```

## Not

Kod yazarken yapay zekâdan yardım alınmıştır.
