# UniQampüs — Web (uniqampus.org)

Bu klasör, `uniqampus.org` üzerinde sunulması gereken **derin link (deep link) altyapısını**
ve yasal sayfa içeriklerini barındırır. Tanıtım sitesi ayrıca profesyonelleştirilecek;
bu dosyalar o sitenin **kök dizinine** yerleştirilmelidir.

## 1) Davet linki altyapısı — `https://uniqampus.org/r/<kod>`

Uygulama zaten `applinks:uniqampus.org` (iOS) ve `https://uniqampus.org/r` (Android) için
yapılandırılmış. Eksik olan **yalnızca web tarafı**. Aşağıdaki dosyalar siteye konunca:
kullanıcı linke tıklar → **uygulama kuruluysa doğrudan açılır** (davet kodu yakalanır);
**kurulu değilse** `r/index.html` kullanıcıyı doğru mağazaya yönlendirir.

| Dosya | Sunulacağı URL | Not |
|---|---|---|
| `.well-known/apple-app-site-association` | `https://uniqampus.org/.well-known/apple-app-site-association` | **Uzantısız**, `Content-Type: application/json`, HTTPS, yönlendirmesiz, kimlik doğrulamasız sunulmalı. |
| `.well-known/assetlinks.json` | `https://uniqampus.org/.well-known/assetlinks.json` | `Content-Type: application/json`. SHA‑256 doldurulmalı (aşağıya bak). |
| `r/index.html` | `https://uniqampus.org/r/<kod>` | `/r/*` tüm yolları bu sayfaya yönlenmeli (aşağıya bak). |

### 1a) Android SHA‑256 parmak izlerini doldur (`assetlinks.json`)
`assetlinks.json` içindeki iki placeholder gerçek değerlerle değiştirilmeli:

- **Play App Signing anahtarı (zorunlu):** Play Console → İlgili uygulama → **Test ve yayınla
  → Uygulama bütünlüğü → Uygulama imzalama anahtarı sertifikası** → `SHA-256` değerini kopyala.
- **EAS upload (yükleme) anahtarı (önerilir):** terminalde
  `eas credentials` → **Android** → **production** → keystore bilgisinde görünen `SHA-256`.
  (Play henüz yeniden imzalamadan, internal/EAS dağıtımlarında da doğrulama çalışsın diye.)

İkisini de `sha256_cert_fingerprints` dizisine koy (büyük harf, iki nokta ayraçlı —
`AB:CD:...` formatında). Birden fazla parmak izi tutmak güvenlidir.

> iOS tarafında ek değer gerekmez — `apple-app-site-association` zaten gerçek
> `appID = KBBF52FD8L.com.uniqampus.app` ile hazır.

### 1b) `/r/*` yönlendirmesi (host'a göre)
`/r/<kod>` gibi dinamik yollar tek bir `r/index.html`'e düşmeli. Host'una göre **birini** uygula:

- **Netlify / Cloudflare Pages** — site köküne `_redirects` dosyası:
  ```
  /r/*  /r/index.html  200
  ```
- **Vercel** — `vercel.json`:
  ```json
  { "rewrites": [{ "source": "/r/(.*)", "destination": "/r/index.html" }] }
  ```
- **Apache** (`.htaccess`):
  ```
  RewriteEngine On
  RewriteRule ^r/.*$ /r/index.html [L]
  ```
- **nginx**:
  ```
  location /r/ { try_files $uri /r/index.html; }
  ```
- **GitHub Pages (bu projenin host'u)** — wildcard desteklemez. Çözüm hazır:
  kök `404.html` davet linklerini (`/r/<kod>`) yakalar. Ayrıca Jekyll `.` ile başlayan
  klasörleri yok saydığı için `_config.yml`'e şunu **eklemek zorunlu**:
  ```yaml
  include:
    - .well-known
  ```

> Önemli: `.well-known/apple-app-site-association` dosyası bazı statik host'larda
> uzantısız olduğu için `text/plain` döner — Apple `application/json` ister. Gerekirse
> host header kuralı ekle (Netlify `_headers`, Vercel `headers`, nginx `types`).

### 1c) Doğrulama
- iOS: `https://app-site-association.cdn-apple.com/a/v1/uniqampus.org` (Apple CDN cache'i
  AASA'yı gösterir) veya Xcode "Associated Domains" diagnostiği.
- Android: [Statement List Generator & Tester](https://developers.google.com/digital-asset-links/tools/generator)
  → `uniqampus.org` + `com.uniqampus.app` + SHA‑256 ile test et. Cihazda:
  `adb shell pm verify-app-links --re-verify com.uniqampus.app` sonra
  `adb shell pm get-app-links com.uniqampus.app` (hepsi `verified` olmalı).

## 2) Yasal sayfalar
`legal/` altındaki metinler şu URL'lerde yayınlanacak (uygulama ve mağaza bu adresleri kullanır):

| Sayfa | URL |
|---|---|
| Gizlilik Politikası | `https://uniqampus.org/privacy` |
| Kullanım Koşulları | `https://uniqampus.org/terms` |
| KVKK Aydınlatma Metni | `https://uniqampus.org/kvkk` |
| Hesap & Veri Silme | `https://uniqampus.org/account-deletion` |
| Destek | `https://uniqampus.org/support` |

Tüm bağlantılar ve e‑postalar **uniqampus.org** alan adına göre normalize edilecektir.
