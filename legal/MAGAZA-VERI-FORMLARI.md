# Mağaza Veri Beyanı — Apple App Privacy + Google Data Safety

Bu dosya, App Store Connect "App Privacy" ve Play Console "Data Safety" formlarını doldururken
kullanılacak **hazır cevaplardır**. Uygulamanın gerçek veri pratiğine göre hazırlanmıştır ve
[Gizlilik Politikası](https://uniqampus.org/privacy) ile **tutarlı olmalıdır** (mağazalar tutarlılık arar).

## Genel cevaplar (her iki mağaza)

- **Hesap gerekiyor mu?** Evet (kişisel e-posta ile kayıt).
- **Üçüncü taraf takip (tracking) / reklam tanımlayıcısı (IDFA/AdID)?** **HAYIR.** Davranışsal reklam
  ağı, çapraz-uygulama takibi yok. → Apple'da **"Data Used to Track You" = Yok** (App Tracking
  Transparency izni gerekmez). Google'da **"third party'lerle paylaşım" = Hayır**.
- **Veri satışı?** Hayır.
- **İletimde şifreleme (encryption in transit)?** **Evet** (HTTPS/TLS — Supabase + Cloudflare).
- **Kullanıcı veri silme talep edebilir mi?** **Evet** → Uygulama içi (Profil > Ayarlar > Hesabımı Sil)
  - web: `https://uniqampus.org/account-deletion`.
- **Üçüncü taraflar (Supabase, Sentry, Cloudflare, Expo):** Bunlar **işleyici/hizmet sağlayıcıdır**
  (sizin adınıza işler) → Google Data Safety'de "shared" (paylaşılan) DEĞİL, "collected" (toplanan)
  olarak işaretlenir.

---

## A) Apple — App Privacy (App Store Connect)

"Data Used to Track You": **NONE.**
"Data Linked to You" (hesaba bağlı, hepsi App Functionality amaçlı; analitik olanlarda Analytics de işaretle):

| Apple Veri Tipi                                                                                                | Topla? | Bağlı? | Amaç                         |
| -------------------------------------------------------------------------------------------------------------- | ------ | ------ | ---------------------------- |
| Contact Info → **Email Address**                                                                               | Evet   | Evet   | App Functionality            |
| User Content → **Photos or Videos** (profil, ilan, kayıp-buluntu, DM medya, öğrenci kimlik görseli)            | Evet   | Evet   | App Functionality            |
| User Content → **Audio Data** (sesli mesaj)                                                                    | Evet   | Evet   | App Functionality            |
| User Content → **Customer Support** (destek mesajları)                                                         | Evet   | Evet   | App Functionality            |
| User Content → **Other User Content** (forum/goygoy gönderileri, hoca değerlendirmeleri, ilan metni, DM metni) | Evet   | Evet   | App Functionality            |
| Identifiers → **User ID**                                                                                      | Evet   | Evet   | App Functionality            |
| Identifiers → **Device ID** (push token / cihaz tanımlayıcı)                                                   | Evet   | Evet   | App Functionality            |
| Usage Data → **Product Interaction** (anonim kullanım istatistiği)                                             | Evet   | Evet   | Analytics, App Functionality |
| Diagnostics → **Crash Data** (Sentry)                                                                          | Evet   | Evet   | App Functionality            |
| Diagnostics → **Performance Data** (Sentry)                                                                    | Evet   | Evet   | App Functionality            |
| **Other Data Types** → T.C. kimlik no, üniversite/bölüm/sınıf bilgisi                                          | Evet   | Evet   | App Functionality            |

> Apple'ın "Sensitive Info" tanımı (ırk, din, cinsel yönelim, biyometrik vb.) **T.C. kimlik numarasını
> kapsamaz**; bu yüzden TC kimlik "Other Data Types" altında beyan edilir. Öğrenci kimlik kartı görseli
> ise "Photos or Videos" altındadır. (Nihai sınıflandırma için avukat görüşü önerilir.)

---

## B) Google — Data Safety (Play Console)

Her veri tipi için: **Collected = Evet**, **Shared = Hayır** (işleyiciler paylaşım sayılmaz),
**Processed ephemerally = Hayır**, ve aşağıdaki amaç. "Required" = kayıt/özellik için gerekli.

| Google Kategorisi → Tip                                                                    | Topla | Gerekli/Ops. | Amaç                                         |
| ------------------------------------------------------------------------------------------ | ----- | ------------ | -------------------------------------------- |
| Personal info → **Email address**                                                          | Evet  | Gerekli      | App functionality, Account management        |
| Personal info → **User IDs**                                                               | Evet  | Gerekli      | App functionality                            |
| Personal info → **Name** (kullanıcı adı/nickname)                                          | Evet  | Gerekli      | App functionality                            |
| Personal info → **Other info** (T.C. kimlik no, üniversite/bölüm/sınıf)                    | Evet  | Gerekli      | App functionality, Fraud prevention/security |
| Photos and videos → **Photos** (profil, ilan, kayıp-buluntu, öğrenci kimlik görseli)       | Evet  | Opsiyonel    | App functionality                            |
| Audio → **Voice or sound recordings** (sesli mesaj)                                        | Evet  | Opsiyonel    | App functionality                            |
| Messages → **Other in-app messages** (DM)                                                  | Evet  | Opsiyonel    | App functionality                            |
| App activity → **Other user-generated content** (forum/goygoy, değerlendirme, ilan)        | Evet  | Opsiyonel    | App functionality                            |
| App activity → **App interactions** (anonim kullanım)                                      | Evet  | Opsiyonel    | Analytics, App functionality                 |
| App info and performance → **Crash logs**                                                  | Evet  | Gerekli      | App functionality                            |
| App info and performance → **Diagnostics**                                                 | Evet  | Gerekli      | App functionality                            |
| Device or other IDs → **Device or other IDs** (push token, cihaz tanımlayıcı, IP güvenlik) | Evet  | Gerekli      | App functionality, Fraud prevention/security |

**Data Safety ek sorular:**

- "Is all of the user data collected by your app encrypted in transit?" → **Evet**.
- "Do you provide a way for users to request that their data is deleted?" → **Evet**
  (`https://uniqampus.org/account-deletion`).

---

## İzin açıklamaları (uygulama içi — Apple reddini önler)

`app.json`'da/Info.plist'te bu izin metinleri net olmalı (zaten çoğu mevcut):

- **Kamera:** "Profil ve ilan fotoğraflarını çekebilmek için kamera izni gerekir."
- **Fotoğraf/Galeri:** "Profil ve ilan fotoğraflarını yüklemek için galeriye erişim izni gerekir."
- **Mikrofon:** "Sesli mesaj gönderebilmek için mikrofon izni gerekir."
- **Bildirimler:** Mesaj, etkinlik ve topluluk bildirimleri için.

## Yayın öncesi tutarlılık kontrolü

- [ ] App Privacy + Data Safety beyanları bu tabloyla ve Gizlilik Politikası ile birebir uyumlu.
- [ ] "Tracking yok / reklam tanımlayıcısı yok" beyanı (ATT promptu yok) doğru.
- [ ] Hesap silme: uygulama içi **ve** web URL'i Play Console "Data deletion" alanına girildi.
- [ ] Tüm yasal URL'ler (privacy/terms/kvkk/account-deletion/support) yayında ve erişilebilir.
