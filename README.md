# Lokma 🍽️

**Fotoğrafını çek, ne yediğini Türkçe anlasın.**
Türk mutfağını tanıyan, öğrencilere özel, yapay zekâ destekli kalori ve beslenme koçu.

*[English below](#english)*

> ENGR 4451 Generative AI dersi kapsamında geliştirildi. Cal AI'dan ilham alındı. Cal AI, aylık milyonlarca dolar gelir elde eden ve MyFitnessPal tarafından satın alınan bir fotoğraflı kalori takip uygulaması.

## Canlı demo

👉 **https://emrehanvural.github.io/lokma/**

Telefonda açıp ana ekrana ekleyebilirsin. Kurulum gerekmez.

## Özellikler

| Özellik | Açıklama |
|---|---|
| 📸 **Fotoğraftan kalori** | Tabağın fotoğrafını çek; yapay zekâ yemekleri tanır, kalori, protein, karbonhidrat ve yağ tahmini verir. Mantı, karnıyarık, menemen, lahmacun gibi Türk yemeklerini doğru adlarıyla tanır. |
| 🍽️ **Sofra modu** | Ortaya konan meze, pide ya da lahmacun tabağında kaç kişi olduğunu seç, sana düşen payı hesaplasın. |
| ✍️ **Yazarak ekleme** | "Kahvaltıda iki yumurtalı menemen, bir simit" yazman yeterli. |
| 🏫 **Yemekhane modu** | Haftalık menüden tek dokunuşla ekle. Hedefine göre "en iyi seçim" işaretlenir. |
| 👤 **Adım adım profil** | Cinsiyet, yaş, boy, kilo, aktivite, hedef, hedef kilo, tempo, beslenme tarzı ve zorlandığın şeyler sorulur; hedefe ne zaman ulaşacağın hesaplanır. |
| 🧠 **Beslenme koçu** | Profiline, bugün yediklerine ve yemekhane menüsüne bakarak kısa, uygulanabilir öneriler verir. |
| 🌙 **Ramazan modu** | Öneriler sahur ve iftara göre bölünür. |
| 🌐 **Türkçe / İngilizce** | Tek dokunuşla dil değişir; yapay zekâ yanıtları da seçilen dilde gelir. |
| 🌓 **Açık / koyu tema** | Telefonun temasını takip eder. |

## Yapay zekâ kurulumu (ücretsiz)

Fotoğraf analizi ve beslenme koçu için bir **Google Gemini API anahtarı** gerekir:

1. [aistudio.google.com/apikey](https://aistudio.google.com/apikey) adresine git ve Google hesabınla anahtar oluştur.
2. Lokma'da **Profil** sekmesine gir, anahtarı **Yapay zekâ bağlantısı** alanına yapıştır, **Kaydet**'e bas.

Anahtar yalnızca senin cihazında (tarayıcının yerel depolamasında) saklanır ve sadece Google'a gönderilir. **Anahtarını bu depoya ya da koda asla ekleme.**

Anahtar olmadan da öğünleri elle ya da yemekhaneden ekleyebilirsin.

## Hesaplama nasıl yapılıyor?

- **Bazal metabolizma (BMR):** Mifflin-St Jeor formülü
  - Erkek: `10 × kilo + 6,25 × boy − 5 × yaş + 5`
  - Kadın: `10 × kilo + 6,25 × boy − 5 × yaş − 161`
- **Günlük harcama (TDEE):** BMR × aktivite katsayısı (1,2 – 1,9)
- **Hedef:** 1 kg yağ ≈ 7700 kcal kabul edilir. Haftalık tempoya göre günlük açık ya da fazla eklenir.
- **Makrolar:** Protein kilo başına 1,4–2,2 g (hedefe ve beslenme tarzına göre), yağ kalorinin %27'si (Akdeniz tipinde %32), kalanı karbonhidrat.

**Güvenlik kuralları:**
- Günlük kalori kadınlarda 1200, erkeklerde 1500 kcal'nin altına inmez.
- 18 yaş altında kilo verme hedefi sunulmaz.
- Hedef kilo, boya göre sağlıklı alt sınırın (VKİ 18,5) altına inemez.

## Teknik yapı

- Tek dosya: `index.html` (HTML + CSS + JavaScript). Derleme ya da sunucu gerekmez.
- Veriler (profil, öğünler, dil, API anahtarı) tarayıcının `localStorage` alanında tutulur.
- Yapay zekâ: Claude içinde açıldığında Claude, diğer her yerde Google Gemini API (`gemini-flash-latest`).

### Kendi bilgisayarında çalıştırma

```bash
git clone https://github.com/emrehanvural/lokma.git
cd lokma
python3 -m http.server 8000
# tarayıcıda http://localhost:8000 adresini aç
```

### GitHub Pages ile yayınlama

**Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main`, klasör: `/ (root)`** seçip kaydet. Birkaç dakika içinde site `https://<kullanıcı-adın>.github.io/lokma/` adresinde yayında olur.

## Yol haritası

- [ ] Menü okuyucu: restoran menüsünün fotoğrafından hedefe uygun yemek önerisi
- [ ] Sesle öğün kaydı
- [ ] Öğrenci bütçesi: TL başına protein
- [ ] Gerçek üniversite yemekhanesi menüsü entegrasyonu
- [ ] Haftalık ilerleme grafiği ve kilo takibi

## Uyarı

Lokma tıbbi tavsiye vermez. Değerler yapay zekâ tahminidir. Sağlık sorunun, hamileliğin ya da yeme bozukluğu geçmişin varsa bir diyetisyene danış.

---

## English

**Snap your plate, get calories that understand Turkish food.**
An AI-powered calorie tracker and nutrition coach for students, built around Turkish cuisine. Inspired by Cal AI.

**Live demo:** https://emrehanvural.github.io/lokma/

**Features:** photo-based calorie and macro estimates · table mode for shared plates · describe-to-log · one-tap cafeteria menu with a "best pick" · step-by-step onboarding with goal weight, pace and target date · AI nutrition coach · Ramadan mode · Turkish/English · light/dark theme.

**AI setup (free):** create a Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey), then paste it into **Profile → AI connection**. The key is stored only in your browser and sent only to Google. Never commit your key to this repository.

**Run locally:** clone the repo and serve the folder (`python3 -m http.server 8000`), then open `http://localhost:8000`.

**Disclaimer:** Lokma does not give medical advice. All values are AI estimates.
