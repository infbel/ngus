# 🛡️ NGUS - UnShort

Repository NGUS ini berisi data konfigurasi untuk mendeteksi **link phishing, scam, situs berbahaya, shortlink, dan lainnya** yang digunakan oleh Worker UnShort.

---

## 📁 Daftar File Konfigurasi

| File | Fungsi |
|------|--------|
| [detectPhishing.json](./detectPhishing.json) | Blacklist phishing (domain jahat, kata kunci, TLD, brand) |
| [cleanUrl.json](./cleanUrl.json) | Daftar parameter tracking yang akan dihapus dari URL |
| [isFinalUrl.json](./isFinalUrl.json) | Domain yang dianggap final (bukan shortlink) |
| [detectLinkRotator.json](./detectLinkRotator.json) | Keyword untuk mendeteksi link rotator/content locker |
| [shortlinkDomains.json](./shortlinkDomains.json) | Daftar domain shortener yang akan di-expand |
| [problematicServices.json](./problematicServices.json) | Shortener bermasalah yang butuh bypass khusus |

---

## 🤝 Cara Berkontribusi

1. **Daftar GitHub** (gratis)
2. **Berikan username/email ke Admin** untuk diundang sebagai collaborator
3. **Cek email undangan** dari `infbel/ngus`
4. **Accept invitation**
5. Mulai edit file konfigurasi!

---

## 📋 Panduan Isi Setiap File

### 1. [detectPhishing.json](./detectPhishing.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| `malicious_domains` | Domain jahat (phishing, scam, malware) | `"bca-verifikasi.cfd"` |
| `bad_words` | Kata-kata yang sering muncul di domain phishing | `"verify"`, `"login"`, `"klaim"` |
| `bad_tlds` | Ekstensi domain yang sering dipakai phishing | `".cfd"`, `".top"`, `".xyz"` |
| `brands` | Nama brand yang sering dipalsukan untuk phishing | `"bca"`, `"shopee"`, `"paypal"` |
| `safeDomainsForEncoding` | Domain besar yang boleh punya banyak parameter encoding | `"google.com"`, `"amazon.com"` |
| `suspicious_paths` | Path di URL yang sering dipakai phishing | `"/login"`, `"/verify"` |
| `redirectParams` | Parameter URL yang digunakan untuk redirect ke website lain | `"redirect"`, `"url"`, `"next"` |

### 2. [cleanUrl.json](./cleanUrl.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| `trackingParams` | Parameter iklan/tracking yang akan dihapus dari URL | `"utm_source"`, `"fbclid"`, `"gclid"` |

**Kapan nambahin:** Ketika menemukan parameter iklan/tracking di URL yang tidak terhapus.

### 3. [isFinalUrl.json](./isFinalUrl.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| `finalDomains` | Domain tujuan akhir (bukan shortlink) | `"whatsapp.com"`, `"shopee.com"` |

**Kapan nambahin:** Ketika menemukan domain yang sudah final (tidak perlu di-expand lagi).

### 4. [detectLinkRotator.json](./detectLinkRotator.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| `rotatorKeywords` | Kata kunci yang menandakan link rotator/content locker | `"please wait"`, `"loading"`, `"captcha"` |

**Kapan nambahin:** Ketika menemukan halaman dengan kata-kata baru yang menandakan link rotator.

### 5. [shortlinkDomains.json](./shortlinkDomains.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| `shortlinkDomains` | Domain shortener yang akan di-expand (diikuti redirect-nya) | `"bit.ly"`, `"t.co"`, `"sfl.gl"` |

**Kapan nambahin:** Ketika menemukan layanan shortener baru yang belum terdaftar.

### 6. [problematicServices.json](./problematicServices.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| `problematicServices` | Shortener bermasalah yang butuh bypass khusus | `"ln.run"`, `"short.link"`, `"linkvertise.com"` |

**Kapan nambahin:** Ketika menemukan shortener yang membutuhkan metode khusus untuk di-expand.

---

## ✏️ Cara Edit File

1. Buka file yang ingin diedit di repository ini
2. Klik tombol **pensil (Edit)** di pojok kanan atas
3. Tambahkan data baru di bagian yang sesuai
4. Klik **"Commit changes..."** (tombol hijau)
5. Isi commit message (contoh: "Menambahkan domain phishing baru")
6. Pilih **"Create a new branch"** dan **"Start a pull request"**
7. Klik **"Propose changes"**
8. Tunggu Admin **review dan merge**

### ✅ Contoh penambahan yang BENAR (semua pakai koma kecuali data terakhir):

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd",
  "login-secure.top"
]
```

### ❌ Contoh yang SALAH (lupa koma selain data terakhir):

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd"
  "login-secure.top"
]
```

### ❌ Contoh yang SALAH (pakai koma di semua data):

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd",
  "login-secure.top",
]
```

## ⏱️ Proses Update

- Setelah Pull Request di-merge oleh Admin
- Worker UnShort akan mengambil data baru dalam maksimal 1 jam
- Perubahan akan otomatis berlaku untuk semua pengguna

## 💡 Yang JANGAN Ditambahkan

| Jangan tambahkan | Ke file | Alasannya |
|------------------|---------|-----------|
| `google.com` | `detectPhishing.json` (malicious_domains) | Domain resmi, nanti kena false positive |
| `facebook.com` | `detectPhishing.json` (malicious_domains) | Domain resmi, nanti kena false positive |
| `whatsapp.com` | `detectPhishing.json` (malicious_domains) | Domain resmi, nanti kena false positive |
| `.com` | `detectPhishing.json` (bad_tlds) | Terlalu umum, website bagus juga pakai .com |
| `.org` | `detectPhishing.json` (bad_tlds) | Terlalu umum, website bagus juga pakai .org |
| `.net` | `detectPhishing.json` (bad_tlds) | Terlalu umum, website bagus juga pakai .net |
| `.id` | `detectPhishing.json` (bad_tlds) | Domain resmi Indonesia, banyak website bagus |
| Path `/about` | `detectPhishing.json` (suspicious_paths) | Tidak mencurigakan |
| Path `/contact` | `detectPhishing.json` (suspicious_paths) | Tidak mencurigakan |
| Path `/privacy` | `detectPhishing.json` (suspicious_paths) | Tidak mencurigakan |
| Domain yang belum jelas kebenarannya | `detectPhishing.json` (malicious_domains) | Bisa kena false positive |
| Domain resmi (whatsapp.com, google.com, dll) | `shortlinkDomains.json` | Domain final bukan shortener |
| Parameter `q` (search query) | `cleanUrl.json` | Parameter pencarian yang penting |
| Parameter `id` (biasanya) | `cleanUrl.json` | Bisa jadi ID konten yang penting |

### Aturan Sederhana:

> **"Jika ragu, JANGAN tambahkan. Tanyakan ke Admin dulu."**

## 📝 Ringkasan File dan Kapan Mengeditnya

| Jika menemukan... | Edit file... | Bagian yang diedit |
|------------------|--------------|-------------------|
| Domain jahat baru | `detectPhishing.json` | `malicious_domains` |
| Kata kunci mencurigakan baru | `detectPhishing.json` | `bad_words` |
| Ekstensi domain berbahaya baru | `detectPhishing.json` | `bad_tlds` |
| Brand baru yang sering dipalsukan | `detectPhishing.json` | `brands` |
| Domain besar yang aman untuk encoding | `detectPhishing.json` | `safeDomainsForEncoding` |
| Path URL mencurigakan baru | `detectPhishing.json` | `suspicious_paths` |
| Parameter redirect baru | `detectPhishing.json` | `redirectParams` |
| Parameter tracking/iklan baru | `cleanUrl.json` | `trackingParams` |
| Domain final baru (bukan shortener) | `isFinalUrl.json` | `finalDomains` |
| Keyword link rotator baru | `detectLinkRotator.json` | `rotatorKeywords` |
| Layanan shortener baru | `shortlinkDomains.json` | `shortlinkDomains` |
| Shortener bermasalah (butuh bypass) | `problematicServices.json` | `problematicServices` |

---

## 🙏 Terima Kasih

Setiap kontribusi yang Anda berikan **sangat berarti** dan membantu banyak orang terhindar dari:

- 🎣 Penipuan phishing
- 💰 Pencurian data keuangan
- 🔐 Peretasan akun
- 📱 Penyebaran malware

**Bersama kita lawan penipuan online!**

---

Ada pertanyaan? Jangan ragu untuk menghubungi Admin.

Terima kasih sudah berkontribusi! 🎉
