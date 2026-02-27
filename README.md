# ✈️ SAP ABAP – SmartForms Havayolu Raporu

## 📋 Proje Özeti

Bu proje, **SAP SmartForms** teknolojisi ile geliştirilmiş bir **Havayolu Detaylı Liste Raporu**dur. Standart SAP `SCARR` tablosundan havayolu verilerini çekerek, profesyonel bir baskı formatında çıktı üretir. Rapor; logo, başlık, dinamik tablo, koşullu içerik, barcode ve sayfa numarası gibi SmartForms bileşenlerini içerir.

---

## 🎯 Projenin Amacı

> *"Havayolu bilgilerini SmartForms ile profesyonel bir baskı raporuna dönüştür — para birimi filtreleme, koşullu listeleme, barcode ve dinamik sayfalama ile."*

---

## ⚙️ Teknik Detaylar

| Özellik | Detay |
|---|---|
| **Platform** | SAP ERP (ABAP) |
| **Teknoloji** | SAP SmartForms |
| **Driver Program** | `Z_9124_DRIVER_PRG` |
| **SmartForm Adı** | `Z_9125_SMRT_FRM_PRMT` |
| **Veri Kaynağı** | `SCARR` (Havayolları standart tablo) |
| **Çıktı Formatı** | Print Preview (PDF benzeri) |

### 📊 Veri Kaynağı – `SCARR` Tablosu

| Alan | Açıklama |
|---|---|
| `CARRID` | Havayolu kodu (AA, LH, BA...) |
| `CARRNAME` | Havayolu adı |
| `CURRCODE` | Para birimi (USD, EUR, GBP...) |
| `URL` | Havayolu web sitesi |

---

## 🧠 İş Mantığı

### Driver Program (Z_9124_DRIVER_PRG)
1. **Selection Screen** üzerinden filtreler alınır:
   - `P_ACTIVE` → Aktiflik durumu
   - `S_CODE` → Para birimi kodu filtresi (SELECT-OPTIONS)
2. `SCARR` tablosundan filtreye uygun veriler çekilir.
3. `SSF_FUNCTION_MODULE_NAME` ile SmartForm'un fonksiyon modülü adı alınır.
4. Fonksiyon modülü çağrılarak SmartForm çıktısı üretilir.
5. **Pop-up engelleme**: `no_dialog` ve `preview` parametreleri ile doğrudan ön izleme açılır.

### SmartForm Yapısı (Z_9125_SMRT_FRM_PRMT)
- **HEADER**: Üst başlık + Alt başlık + Logo (resim)
- **GENEL_BILGI**: Kullanıcı, tarih, saat bilgileri + Gizlilik politikası metni
- **DYNAMIC**: Dinamik metin alanı
- **INCD_PARAGRAF**: Include paragraf
- **MAIN (Ana Pencere)**: `TABLE1` – Havayolu detay tablosu (ID, Tanım, PB, URL)
- **DURUM**: `CONDITION4` ile koşullu içerik (Active parametresine göre)
- **EUR_LIST**: `LOOP1` ile EUR para birimli havayollarının ayrı listelenmesi
- **BARCODE**: Barcode çıktısı
- **FOOTER**: Sayfa numarası

---

## 🖥️ Ekran Görüntüleri

### SmartForms Builder – Form Yapısı (Geniş Ekran)

![SmartForms Builder](Resimler/Ekran%20görüntüsü%202026-02-27%20163852.png)

### SE38 – Selection Screen (Driver Program)

![Selection Screen](Resimler/Ekran%20görüntüsü%202026-02-27%20164006.png)

### Çıktı – Hava Yolları Detaylı Liste Raporu

![Çıktı Sayfa 1](Resimler/Ekran%20görüntüsü%202026-02-27%20163943.png)

![Çıktı Sayfa 1 Devamı](Resimler/Ekran%20görüntüsü%202026-02-27%20163948.png)

---

## 🔑 Öne Çıkan Teknik Özellikler

- **🖨️ SAP SmartForms**: Profesyonel baskı çıktısı için form tasarımı (WYSIWYG editör)
- **🖼️ Logo Entegrasyonu**: Form başlığında görsel (resim) kullanımı
- **📊 Dinamik Tablo (TABLE1)**: SCARR verilerini tablo formatında listeleme
- **🔀 Koşullu İçerik (CONDITION)**: `P_ACTIVE` parametresine göre göster/gizle
- **🔁 LOOP İşlemi**: EUR para birimli havayollarını ayrı listede döngüyle gösterir
- **📊 Barcode**: Otomatik barcode üretimi
- **📄 Sayfalama**: Footer'da otomatik sayfa numarası
- **🔍 SELECT-OPTIONS Filtresi**: Para birimi bazında veri filtreleme
- **🚫 Pop-up Engelleme**: `no_dialog` + `preview` ile doğrudan ön izleme
- **🔗 SSF_FUNCTION_MODULE_NAME**: SmartForm-Driver Program arasındaki ara katman

---

## 🛠️ Kullanılan Teknolojiler

`SAP ERP` · `ABAP` · `SmartForms` · `Form Builder` · `SSF Function Module` · `SCARR` · `SELECT-OPTIONS` · `Barcode` · `Print Preview`

---

## 📂 Proje Yapısı

```
SmartForms Projesi
├── Z_9124_DRIVER_PRG          → Driver Program (SE38)
└── Z_9125_SMRT_FRM_PRMT       → SmartForm Tasarımı (SmartForms Builder)
```

---

## 👨‍💻 Geliştirici

Bu proje, SAP ABAP eğitimi kapsamında geliştirilmiştir.

---

> **#SAP #ABAP #SmartForms #PrintReport #Barcode #FormBuilder #SCARR #SAPDevelopment #ERPDevelopment**
