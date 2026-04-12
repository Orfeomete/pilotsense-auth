# PilotSense AUTH

> **CDSA Projesi — Aşama 1 · Kriptografik Çoklu İmza**
> Biyometrik veriye bağımsız otorite onayıyla erişim simülatörü

🔗 **Canlı Demo:** [orfeomete.github.io/pilotsense-auth](https://orfeomete.github.io/pilotsense-auth)

---

## Hakkında

PilotSense AUTH, havacılık kazalarında pilota ait biyometrik verilerin yalnızca bağımsız ve yetkili otoritelerin **eşzamanlı onayı** ile açılabilmesini sağlayan kriptografik çoklu imza mimarisini simüle eden bir web uygulamasıdır.

Uçuş sırasında toplanan SpO₂, HRV ve stres indeksi gibi kişisel biyometrik veriler AES-256-GCM şifresiyle korunur. Bu verilere erişmek için **3/3 eşik şeması** gereklidir: SHGM, IFALPA ve NTSB gibi birbirinden bağımsız üç tarafın kurumsal yetki kodu ile eşzamanlı onay vermesi zorunludur.

Bu mimari, **Tamamlayıcı Tanısal Emniyet Yaklaşımı (CDSA)** kapsamında mahremiyet ile uçuş emniyeti arasındaki dengeyi kuran temel protokolü oluşturmaktadır.

---

## Özellikler

- 🔐 **AES-256-GCM şifreleme** — endüstri standardı veri koruması
- 👥 **3/3 eşik şeması** — tek tarafın onayı yeterli değildir
- 🌍 **Bağımsız taraflar** — SHGM, IFALPA, NTSB
- 📋 **Kriptografik imza** — SHA-256 hash ile doğrulama
- 🕒 **Canlı sistem logu** — tüm erişim girişimleri kayıt altında
- 🌐 **TR/EN dil desteği** — log mesajları dahil tam dil değişimi
- ✅ **Kilit açılım paneli** — 3/3 onay sonrası tanısal bulguların görünümü

---

## Mimari

```
Pilot Saati
    │
    ▼ AES-256-GCM şifreleme
Şifreli Biyometrik Veri (14.7 MB)
    │
    ▼ Shamir Gizli Paylaşım
┌───────────┬───────────┬───────────┐
│   SHGM    │  IFALPA   │   NTSB    │
│ Ankara,TR │Montreal,CA│Washington │
└───────────┴───────────┴───────────┘
    │           │           │
    └───────────┴───────────┘
                │ 3/3 Eşzamanlı Onay
                ▼
        Veri Erişimi Açılır
        (Tanısal bulgular)
```

---

## Araştırma Bağlamı

Pilotun kaza anındaki akut stres, gizli hipoksi veya mikro-uyku gibi içsel fizyolojisini ölçen biyometrik verilerin kaza soruşturmalarında kullanılabilmesi için iki kritik sorun çözülmelidir: **veri güvenliği** ve **bireysel mahremiyet**.

Kriptografik çoklu imza protokolü bu sorunu şu şekilde çözer:
- Pilot verileri hiçbir zaman açık formatta saklanmaz
- Tek bir kurumun tek başına erişimi mümkün değildir
- Yalnızca kaza soruşturması gibi meşru bir gerekçeyle, bağımsız tarafların ortak kararıyla veri açılabilir

> *"Kriptografik çoklu imza protokolüyle kilitlenen biyometrik verilerin sadece bağımsız otoriteler ve temsilciler onayıyla deşifre edilebilmesi, mahremiyet ile uçuş emniyeti arasındaki hassas teraziyi dengeleyen en uygulanabilir model olarak görülmüştür."*
> — Cantekin, M. (2025), CDSA

---

## CDSA Ekosistemi

```
PilotO2          →  Hipoksi ve risk tahmini
PilotGuard       →  Uçuş öncesi hazırlık ve stres izleme
PilotReflect EFB →  Uçuş sonrası kişisel değerlendirme
PilotSense AUTH  →  Kriptografik çoklu imza (bu repo) ← Aşama 1
PilotSense OPS   →  Anonim filo izleme (Aşama 2)
```

---

## Teknik Altyapı

- Saf HTML/CSS/JS — harici framework yok
- Plus Jakarta Sans & IBM Plex Mono tipografisi
- **GitHub Pages** — Statik hosting
- Tek dosya (`index.html`)

---

## Kullanım (Demo)

Uygulamada üç tarafın yetki kodları:

| Taraf | Yetki Kodu |
|-------|-----------|
| SHGM | `SHGM-2026` |
| IFALPA | `IFAL-2026` |
| NTSB | `NTSB-2026` |

Tüm kodlar girildiğinde sistem kilidi açar ve tanısal bulgular görünür hale gelir.

---

## Kaynak

- Cantekin, M. (2025). *Tamamlayıcı Tanısal Emniyet Yaklaşımı (CDSA) Kapsamında Giyilebilir Teknolojiler ve Uçuş Emniyeti Optimizasyonu*.
- Cantekin, M. (2025). *Mekanikten Yapay Zekaya Evrilen Pilot Saatlerinin Uçuş Emniyetindeki Yeni Rolü*. ATAConf'25, Yayın No: 10232620.
- ICAO. (2016). *Annex 13 — Aircraft Accident and Incident Investigation* (11th ed.).
- European Parliament. (2016). *GDPR — Article 9*.

---

> ⚠️ **Sadece eğitim ve araştırma amaçlıdır.** Tüm veriler sentetiktir.

*CDSA Projesi · ICAO Ek-13 · GDPR Madde 25*
