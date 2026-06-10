# Diplomacia Beceri Hesaplayıcı

[Diplomacia](https://diplomacia.com.tr/) oyunundaki **Kışla**, **Savaş Teknikleri** ve **Bilim İnsanı** becerilerinin yükseltme maliyetini ve bekleme süresini hesaplayan ücretsiz web aracı.

🔗 **Canlı:** https://g0khanbey.github.io/diplomacia-statcalculator/

## Özellikler

- 💰 Para ile yükseltme maliyeti (seviye × 250)
- 💎 Elmas ile yükseltme maliyeti (4 kat kısa bekleme süresi)
- ⏱️ Toplam bekleme süresi (gün / saat / dakika)
- 📉 Cooldown azaltma desteği:
  - Eğitim indeksi (puan başına %2, maks. %30)
  - İlmiye sınıfı (−%10)
  - Premium (−%25)
- 📱 Mobil uyumlu, tek HTML dosyası, bağımlılık yok

## Kullanım

`index.html` dosyasını tarayıcıda aç, beceri seç, mevcut ve hedef seviyeyi gir. Sonuçlar anlık hesaplanır.

Yerel sunucuya veya kuruluma gerek yok — vanilla HTML/CSS/JS.

## Beceri Etkileri

| Beceri | Etki |
|---|---|
| Kışla | Askeri güç + kapasite · seviye başına +%0.25 |
| Savaş Teknikleri | Askeri güç · seviye başına +%0.5 |
| Bilim İnsanı | Fabrika üretim geliri · seviye başına +%0.25 |

Maksimum beceri seviyesi: **999**

## Hesaplama Mantığı

```
Para maliyeti  = Σ (L × 250)                    [L = mevcut seviye .. hedef-1]
Para süresi    = Σ max(1, 18 × (L/50)^2.5) × m
Elmas maliyeti = Σ ceil(max(5, ceil(L/10)×5) × 1.5)
Elmas süresi   = Σ max(1, 4.5 × (L/50)^2.5) × m

m = 1 − (eğitim indeksi azaltması + ilmiye + premium) / 100
```

## Notlar

- Bu araç gayri resmidir; Diplomacia ile bir bağlantısı yoktur.
- Formüller oyun içi gözlemlere dayanır, oyun güncellemeleriyle değişebilir. Hata görürsen issue aç.

## Lisans

MIT
