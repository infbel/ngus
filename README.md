# 🛡️ NGUS - UnShort

Repository NGUS ini berisi data konfigurasi untuk mendeteksi **link phishing, scam, situs berbahaya, tracking dan lainnya** yang digunakan oleh Worker UnShort.

---

## 📁 Daftar File Konfigurasi

| File                                                   | Fungsi                                                    |
| ------------------------------------------------------ | --------------------------------------------------------- |
| [detectPhishing.json](./detectPhishing.json)           | Blacklist phishing (domain jahat, kata kunci, TLD, brand) |
| [cleanUrl.json](./cleanUrl.json)                       | Membersihkan URL dari tracking & manipulasi tertentu      |
| [isFinalUrl.json](./isFinalUrl.json)                   | Domain yang dianggap final (bukan shortlink)              |
| [detectLinkRotator.json](./detectLinkRotator.json)     | Keyword untuk mendeteksi link rotator/content locker      |
| [problematicServices.json](./problematicServices.json) | Shortener bermasalah yang butuh bypass khusus             |

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

| Field                    | Artinya                                                     | Contoh                           |
| ------------------------ | ----------------------------------------------------------- | -------------------------------- |
| `malicious_domains`      | Domain jahat (phishing, scam, malware)                      | `"bca-verifikasi.cfd"`           |
| `bad_words`              | Kata-kata yang sering muncul di domain phishing             | `"verify"`, `"login"`, `"klaim"` |
| `bad_tlds`               | Ekstensi domain yang sering dipakai phishing                | `".cfd"`, `".top"`, `".xyz"`     |
| `brands`                 | Nama brand yang sering dipalsukan untuk phishing            | `"bca"`, `"shopee"`, `"paypal"`  |
| `safeDomainsForEncoding` | Domain besar yang boleh punya banyak parameter encoding     | `"google.com"`, `"amazon.com"`   |
| `suspicious_paths`       | Path di URL yang sering dipakai phishing                    | `"/login"`, `"/verify"`          |
| `redirectParams`         | Parameter URL yang digunakan untuk redirect ke website lain | `"redirect"`, `"url"`, `"next"`  |

---

### 2. [cleanUrl.json](./cleanUrl.json)

| Field                 | Artinya                                                      | Contoh                     |
| --------------------- | ------------------------------------------------------------ | -------------------------- |
| `trackingParams`      | Parameter iklan/tracking yang akan dihapus dari URL          | `"utm_source"`, `"fbclid"` |
| `removeNumericSuffix` | Menghapus angka tambahan di akhir URL tertentu               | `true`                     |
| `numericSuffixPaths`  | Path yang sering ditambahkan angka untuk tracking/manipulasi | `"/login"`, `"/register"`  |

**Kapan nambahin:**

* Jika menemukan URL dengan angka tambahan yang tidak penting
* Jika path tersebut sering digunakan untuk manipulasi atau tracking

---

### 3. [isFinalUrl.json](./isFinalUrl.json)

| Field          | Artinya                               | Contoh                           |
| -------------- | ------------------------------------- | -------------------------------- |
| `finalDomains` | Domain tujuan akhir (bukan shortlink) | `"whatsapp.com"`, `"shopee.com"` |

**Kapan nambahin:** Ketika menemukan domain yang sudah final (tidak perlu di-expand lagi).

---

### 4. [detectLinkRotator.json](./detectLinkRotator.json)

| Field             | Artinya                                                | Contoh                                    |
| ----------------- | ------------------------------------------------------ | ----------------------------------------- |
| `rotatorKeywords` | Kata kunci yang menandakan link rotator/content locker | `"please wait"`, `"loading"`, `"captcha"` |

**Kapan nambahin:** Ketika menemukan halaman dengan kata-kata baru yang menandakan link rotator.

---

### 5. [problematicServices.json](./problematicServices.json)

| Field                 | Artinya                                       | Contoh                     |
| --------------------- | --------------------------------------------- | -------------------------- |
| `problematicServices` | Shortener bermasalah yang butuh bypass khusus | `"ln.run"`, `"short.link"` |

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

### ✅ Contoh penambahan yang BENAR

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd",
  "login-secure.top"
]
```

### ❌ Contoh yang SALAH

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd"
  "login-secure.top"
]
```

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd",
  "login-secure.top",
]
```

---

## ⏱️ Proses Update

* Setelah Pull Request di-merge oleh Admin
* Worker UnShort akan mengambil data baru dalam maksimal 1 jam
* Perubahan akan otomatis berlaku untuk semua pengguna

---

## 💡 Yang JANGAN Ditambahkan

| Jangan tambahkan   | Ke file                          | Alasannya             |
| ------------------ | -------------------------------- | --------------------- |
| `google.com`       | `detectPhishing.json`            | Domain resmi          |
| `.com`             | `detectPhishing.json` (bad_tlds) | Terlalu umum          |
| Path `/about`      | `detectPhishing.json`            | Tidak mencurigakan    |
| Domain belum jelas | `detectPhishing.json`            | Risiko false positive |
| Parameter `q`      | `cleanUrl.json`                  | Parameter penting     |
| Parameter `id`     | `cleanUrl.json`                  | Bisa ID konten        |

---

### Aturan Sederhana:

> **"Jika ragu, JANGAN tambahkan. Tanyakan ke Admin dulu."**

---

## 📝 Ringkasan File dan Kapan Mengeditnya

| Jika menemukan...                      | Edit file...               | Bagian yang diedit    |
| -------------------------------------- | -------------------------- | --------------------- |
| Domain jahat baru                      | `detectPhishing.json`      | `malicious_domains`   |
| Parameter tracking baru                | `cleanUrl.json`            | `trackingParams`      |
| URL dengan angka tambahan mencurigakan | `cleanUrl.json`            | `numericSuffixPaths`  |
| Domain final baru                      | `isFinalUrl.json`          | `finalDomains`        |
| Keyword rotator baru                   | `detectLinkRotator.json`   | `rotatorKeywords`     |
| Shortener bermasalah                   | `problematicServices.json` | `problematicServices` |

---

## 🙏 Terima Kasih

Setiap kontribusi **sangat berarti** dan membantu banyak orang terhindar dari:

* 🎣 Penipuan phishing
* 💰 Pencurian data keuangan
* 🔐 Peretasan akun
* 📱 Penyebaran malware

**Bersama kita lawan penipuan online!**

---

Ada pertanyaan? Jangan ragu untuk menghubungi Admin.

Terima kasih sudah berkontribusi!
