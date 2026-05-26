---
title: Gizlilik Politikası
layout: default
permalink: /privacy-policy/
---

# UniQampus Gizlilik Politikası

**Yürürlük Tarihi**: [GG.AA.2026 — yayın tarihinde doldurulacak]
**Son Güncelleme**: [GG.AA.2026]

> ⚠️ **Avukat onayı bekleniyor** — bu taslak metni KVKK ve dijital platform uzmanı avukata gönderip onayını aldıktan sonra yayınlayın. Köşeli parantezli alanları (`[...]`) kendi bilgilerinizle değiştirin.

## 1. Veri Sorumlusu ve İletişim

UniQampus ("biz", "uygulamamız", "platformumuz"), 6698 sayılı Kişisel Verilerin Korunması Kanunu ("KVKK") ve Avrupa Birliği Genel Veri Koruma Tüzüğü ("GDPR") kapsamında kişisel verilerinizin işlenmesinden sorumludur.

- **Veri Sorumlusu**: [Ad Soyad / Şirket Ünvanı]
- **Adres**: [Açık posta adresi]
- **E-posta**: support@uniqampus.app
- **VERBİS Sicil Numarası**: [Varsa kayıt numarası; yoksa bu satırı silin]

## 2. Topladığımız Kişisel Veriler

### 2.1 Hesap Verileri
- Üniversite e-posta adresi (`.edu.tr` uzantılı)
- Kullanıcı adı (nickname)
- Şifre (bcrypt algoritması ile şifrelenmiş; düz metin saklanmaz)
- Üniversite, bölüm, sınıf bilgisi
- Profil fotoğrafı (opsiyonel)
- Hesap oluşturma tarihi

### 2.2 Kullanıcı İçeriği
- Forum gönderileri, yanıtlar, oylar, anketler
- Marketplace ilanları (görsel + açıklama)
- Kayıp/Buluntu ilanları
- Aktivite ve ulaşım ilanları
- Hoca değerlendirmeleri
- Goygoy (bölüm içi anonim duvar) gönderileri
- Mesajlar ve mesaj ekleri

### 2.3 Otomatik Toplanan Veriler
- Cihaz tipi, işletim sistemi sürümü
- IP adresi (yalnızca güvenlik amacıyla; 30 gün sonra anonimleştirilir)
- Çökme raporları (Sentry hizmeti üzerinden)
- Push bildirimi token'ı
- Uygulama içi etkileşim verisi (anonim analytics; reklam amaçlı kullanılmaz)

### 2.4 İzin Tabanlı Veriler
Aşağıdaki veriler yalnızca ilgili özellik kullanılmak istendiğinde sorulan açık izinle toplanır:
- **Kamera**: Profil veya ilan fotoğrafı çekmek için
- **Galeri**: Cihazdan fotoğraf seçmek için
- **Mikrofon**: Sohbette sesli mesaj kaydetmek için
- **Konum** (opsiyonel): İlan veya aktivite oluşturma sırasında, kullanıcı izin verdiği takdirde
- **Bildirimler**: Uygulama içi olaylar için push bildirim göndermek

## 3. Verileri İşleme Amacı ve Hukuki Dayanak (KVKK Madde 5)

| Amaç | Hukuki Dayanak |
|---|---|
| Hesap oluşturma ve kimlik doğrulama | Madde 5/2-c: Sözleşmenin kurulması ve ifası |
| Kampüs özelliklerinin sunulması (forum, ilan, mesaj, aktivite vb.) | Madde 5/2-c |
| Push bildirimleri | Madde 5/1: Açık rıza |
| Güvenlik, dolandırıcılık önleme, bot tespiti | Madde 5/2-f: Meşru menfaat |
| Yasal yükümlülükler (5651 sayılı kanun uyarınca log saklama, savcılık talepleri) | Madde 5/2-ç: Hukuki yükümlülük |
| Hesap silme, KVKK talep yanıtlama | Madde 5/2-a: Veri sahibinin talebi |

## 4. Verileri Paylaştığımız Üçüncü Taraflar

Aşağıdaki hizmet sağlayıcılarla veri paylaşımımız, hizmetin sunulması için zorunludur:

| Sağlayıcı | Paylaşılan Veri | Amaç | Konum |
|---|---|---|---|
| Supabase Inc. (ABD) | Tüm uygulama verisi | Veritabanı, depolama, kimlik doğrulama | AWS, Frankfurt (eu-central-1) |
| Sentry Inc. (ABD) | Çökme raporları, hata logları | Hata raporlama ve uygulama stabilitesi | EU bölgesi |
| Cloudflare Inc. (ABD) | IP, cihaz parmak izi | Bot koruması (Turnstile CAPTCHA) | Global |
| Expo (ABD) | Push token | Bildirim iletimi | ABD |
| Apple Inc. ve Google LLC | Cihaz tanımlayıcısı | Uygulama dağıtımı, push bildirim altyapısı | Global |

Bu transferler için GDPR kapsamında Standart Sözleşme Hükümleri (SCC) uygulanır. Kişisel verileriniz pazarlama amacıyla **üçüncü taraflarla paylaşılmaz veya satılmaz**.

## 5. Veri Saklama Süreleri

| Veri Türü | Saklama Süresi |
|---|---|
| Aktif hesap verileri | Hesap aktif kaldığı sürece |
| Silinmiş hesap | 30 gün geri alma süresi + ardından kalıcı silme |
| Mesajlar | Hesap silinene kadar |
| Çökme raporları (Sentry) | 30 gün |
| Audit log (KVKK ve 5651 sayılı kanun gereği) | 2 yıl |
| IP adresi | 30 gün (sonra anonimleştirilir) |
| Anonim analytics | 13 ay |

## 6. Çocukların Verileri

UniQampus, **13 yaşın altındaki** çocuklara yönelik bir hizmet değildir. 13-18 yaş arası kullanıcıların yasal velilerinin izniyle kullanması beklenmektedir. 13 yaşın altında bir kullanıcı tespit edilirse hesabı derhal silinir.

## 7. KVKK Madde 11 Kapsamındaki Haklarınız

Kişisel verilerinizle ilgili olarak aşağıdaki haklara sahipsiniz:

- (a) Verilerinizin işlenip işlenmediğini öğrenme
- (b) İşlenmişse buna ilişkin bilgi talep etme
- (c) İşleme amacını ve amacına uygun kullanılıp kullanılmadığını öğrenme
- (ç) Yurt içi/yurt dışındaki üçüncü kişileri bilme
- (d) Eksik veya yanlış işlenmiş verilerin düzeltilmesini isteme
- (e) Verilerin silinmesini veya yok edilmesini isteme
- (f) (d) ve (e) işlemlerinin verilerin aktarıldığı üçüncü kişilere bildirilmesini isteme
- (g) Otomatik sistemlerle analiz edilmiş bir karara itiraz etme
- (h) Verilerin kanuna aykırı işlenmesi nedeniyle zarara uğranılmışsa tazminat isteme

**Talep yolu**: support@uniqampus.app — Tüm talepler 30 gün içinde yanıtlanır. Talep formu için: [legal sayfanız varsa bağlantı].

## 8. Veri Güvenliği

- TLS 1.3 protokolü ile şifrelenmiş veri iletimi
- AES-256 ile veritabanı şifreleme (rest)
- Şifreler bcrypt ile hashlenmiş (saltlı)
- Supabase Row-Level Security (RLS) ile yetkilendirme
- Düzenli güvenlik denetimi ve sızma testleri
- Çift yönlü doğrulama (2FA) seçeneği (yakında)

## 9. Hesabınızı Silme

Uygulama içinden: **Profil → Ayarlar → Hesabımı Sil**. 30 günlük geri alma süresi sonrası tüm kişisel verileriniz kalıcı olarak silinir.

İstisna: 5651 sayılı kanun ve KVKK kapsamında yasal saklama süreleri içerisindeki log kayıtları anonimleştirilerek saklanmaya devam edilebilir.

## 10. Çerezler ve Tracking

UniQampus mobil uygulaması **çerez kullanmaz**. Uygulama içinde reklam ağı, IDFA/AdId benzeri reklam tanımlayıcıları **kullanılmaz**. Üçüncü taraf takip teknolojileri yoktur.

## 11. Politika Değişiklikleri

Önemli değişiklikler kullanıcılara uygulama içi bildirim ve e-posta ile duyurulur. Devam eden kullanım, güncellenmiş politikayı kabul anlamına gelir.

## 12. İletişim

Bu politika veya verileriniz hakkında sorularınız için:

- **E-posta**: support@uniqampus.app
- **Posta**: [Açık adres]

KVKK kapsamında veri sorumlusuna başvurunuza 30 gün içinde yanıt verilmemesi halinde Kişisel Verileri Koruma Kurulu'na ([www.kvkk.gov.tr](https://www.kvkk.gov.tr)) şikayet hakkınız vardır.

---

*Bu Gizlilik Politikası Türkçe yazılmış ve Türk hukukuna tabidir. İngilizce çevirisi referans amaçlıdır; uyuşmazlık halinde Türkçe metin geçerlidir.*
