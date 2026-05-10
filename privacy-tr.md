# Vaelis — Gizlilik Politikası

**Yürürlük tarihi:** 8 Mayıs 2026

Bu politika, Vaelis mobil uygulamasını kullandığında hangi verileri topladığımızı, neden topladığımızı, kimlerle paylaştığımızı ve haklarını anlatır. Türkiye Kişisel Verilerin Korunması Kanunu (KVKK) ve Avrupa Genel Veri Koruma Tüzüğü (GDPR) standartlarına göre yazılmıştır.

## 1. Veri sorumlusu

Eren Yalçın — Türkiye  
İletişim: **eren-yalcin2010@hotmail.com**

## 2. Toplanan veriler

### a. Hesap verileri (kayıt olduğunda)
- E-posta adresi
- Parolanın güvenli hash'i (PBKDF2-HMAC-SHA256, açık metin saklanmaz)
- Hesap oluşturma + son giriş zaman damgaları

### b. Kullanıcı içeriği (sen yüklediğinde)
- Stil analizi için yüklediğin fotoğraflar
- Dolap parça fotoğrafları ve metadataları (isim, kategori, renk, marka, beden)
- Kaydedilen kombinler (fotoğraf + analiz çıktısı)
- Günlük girdileri (fotoğraf + opsiyonel not)
- Stil profili (cinsiyet, undertone, tercih edilen arketipler)

### c. Yapay zekâ üretim verileri
- Yüklediğin görsel ve metin için yapay zekâ tarafından üretilen analizler, kombin önerileri, brief metinleri ve haftalık özetler
- Bu çıktılar prompt versiyonu ile birlikte saklanır (kalite takibi için)

### d. Kullanım analitiği
- Anonim olay kayıtları (örn: ekran açılışları, paywall görüntülenmesi, abonelik dönüşümü) — PostHog (EU bölgesi) üzerinden
- Kişisel veri içermez; her kullanıcı için tek yönlü hash ile takma kimlik üretilir

### e. Hata raporları
- Uygulama çökmesi durumunda kırılma noktası, cihaz modeli, iOS sürümü, Vaelis sürümü — Sentry üzerinden
- Otomatik olarak çıplak veri (parola, fotoğraf vb.) gönderilmez

### f. Abonelik durumu
- Apple StoreKit'ten gelen abonelik durumu (aktif, deneme, sona erdi)
- Apple `original_transaction_id` (abonelik takibi için)

## 3. Veriyi nasıl kullanırız

- Yapay zekâ analizi, kombin önerisi ve haftalık özet üretmek için **OpenAI** API'sine fotoğraflarını + metin bağlamını göndeririz
- Hesabını yönetmek, oturum açmak, abonelik durumunu kontrol etmek
- Cihazlar arası senkronizasyon (Cloudflare D1 + R2)
- Servis kalitesini takip etmek (anonim kullanım analitiği)
- Çökmeleri tanılayıp düzeltmek (anonim hata raporları)

Verini reklama, üçüncü taraf pazarlamasına veya satışa konu etmiyoruz.

## 4. Üçüncü taraf hizmetler

| Hizmet | Amaç | Veri konumu | Politika |
|---|---|---|---|
| **OpenAI** | Yapay zekâ üretimi (vision + text) | ABD | openai.com/policies |
| **Cloudflare** (Workers, D1, R2, KV) | Backend, veritabanı, fotoğraf depolama | Küresel edge | cloudflare.com/privacypolicy |
| **PostHog** | Anonim kullanım analitiği | AB (eu.i.posthog.com) | posthog.com/privacy |
| **Sentry** | Çökme raporları | AB (sentry.de) | sentry.io/privacy |
| **Apple App Store** | Abonelik yönetimi | ABD/Apple altyapısı | apple.com/privacy |

OpenAI, kullanıcı sözleşmesi gereği API üzerinden gönderilen verileri model eğitiminde kullanmaz (default opt-out).

## 5. Veri saklama

- **Hesap verileri:** hesabını silene kadar tutulur. Sildiğinde anında silinir.
- **Kullanıcı içeriği (fotoğraf, dolap, kombin, günlük):** hesap silinince tüm sunucu kopyaları (D1 + R2) anında silinir; cihazındaki yerel kopyalar uygulama silindiğinde silinir.
- **Anonim analitik:** PostHog'da 12 ay tutulur, sonra agregeye dönüşür.
- **Hata raporları:** Sentry'de 30 gün, sonra silinir.

## 6. Hesap silme + veri silme

Uygulama içinden tek tıkla hesap silebilirsin: **Profil → Hesabım → Hesabı Sil**. Onay sonrası D1 + R2'deki tüm verin sunucudan silinir, KV'deki oturumun iptal edilir, cihaz tarafı yerel veriler temizlenir. İşlem geri alınamaz.

## 7. Kullanıcı hakları (KVKK + GDPR)

Yasal hakların:
- **Erişim:** verilerin hakkında bilgi alma
- **Düzeltme:** yanlış veriyi düzeltme
- **Silme:** verilerinin silinmesini isteme (uygulama içinden tek tıkla)
- **Taşınabilirlik:** verilerinin kopyasını isteme (e-posta ile talep)
- **İtiraz:** belirli işleme türlerine itiraz
- **Şikayet:** Türkiye Veri Koruma Kurumu (KVKK) veya AB üye devleti veri koruma otoritesine başvuru hakkı

Talepler için: **eren-yalcin2010@hotmail.com** — 30 gün içinde yanıt verilir.

## 8. Çocukların gizliliği

Vaelis 13 yaş altı kullanıcıları kabul etmez. 13 yaş altı bir çocuğun veri yüklediğini fark edersen lütfen bize bildir; veriyi sileriz.

## 9. Güvenlik

- TLS 1.2+ ile uçtan uca şifreli bağlantı
- Parolalar PBKDF2-HMAC-SHA256, 100.000 iterasyon ile hash'lenir
- Fotoğraflar Cloudflare R2'de erişim kontrolü ile saklanır; kullanıcı yetki kontrolü her istekte yapılır
- Token tabanlı oturum yönetimi (90 gün TTL)

Mutlak güvenlik garantisi mümkün değildir; ihlal durumunda 72 saat içinde KVKK ve etkilenen kullanıcılara bildirim yaparız.

## 10. Politika değişiklikleri

Bu politikayı güncellersek yürürlük tarihini değiştirir, uygulama içinden bildirim göndeririz. Önemli değişikliklerde açık onay alınır.

## 11. İletişim

Sorular ve talepler için: **eren-yalcin2010@hotmail.com**
