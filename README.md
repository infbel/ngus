# 🛡️ NGUS - UnShort

Repository NGUS ini berisi data untuk mendeteksi **link phishing, scam, situs berbahaya, daftar putih dan lainnya** yang digunakan oleh Worker UnShort.

# 🤝 Cara Berkontribusi

- Daftar github
- Berikan username/email ke Admin dan tunggu konfirmasi
- Silahkan cek email undangan dari infbel/ngus
- View invitation lalu Accept

## 📋 Panduan Isi Setiap Bagian | [detectPhishing.json](./detectPhishing.json)

| Field | Artinya | Contoh |
|-------|---------|--------|
| malicious_domains | Domain jahat (phishing, scam, malware) | "bca-verifikasi.cfd" |
| bad_words | Kata-kata yang sering muncul di domain phishing | "verify", "login", "klaim" |
| bad_tlds | Ekstensi domain yang sering dipakai phishing | ".cfd", ".top", ".xyz" |
| brands | Nama brand yang sering dipalsukan untuk phishing | "bca", "shopee", "paypal" |
| safeDomainsForEncoding | Domain besar yang boleh punya banyak parameter encoding | "google.com", "amazon.com" |
| suspicious_paths | Path di URL yang sering dipakai phishing | "/login", "/verify" |
| redirectParams | Parameter URL yang digunakan untuk redirect ke website lain | "redirect", "url", "next" |

## ✏️ Cara Update Data

1. Buka file `detectPhishing.json` di repository ini
2. Klik tombol pensil (Edit) di pojok kanan atas
3. Tambahkan data baru di bagian yang sesuai
4. Klik "Commit changes" (tombol hijau)
5. Isi commit message dan Extended description (opsional)

### Contoh penambahan yang BENAR (semua pakai koma kecuali data terakhir):

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd",
  "login-secure.top"
]
```

### Contoh yang SALAH (lupa koma selain data terakhir):

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd"
  "login-secure.top"
]
```

### Contoh yang SALAH (pakai koma di semua data):

```json
"malicious_domains": [
  "acswwajz.cfd",
  "bca-verifikasi.cfd",
  "login-secure.top",
]
```

## ⏱️ Proses Update

- Setelah tambah data dan commit, Worker UnShort akan mengambil data baru dalam waktu maksimal 1 jam

## 💡 Yang JANGAN Ditambahkan

| Jangan tambahkan | Alasannya |
|------------------|-----------|
| google.com | Ini domain resmi, nanti kena false positive |
| .com ke bad_tlds | Terlalu umum, website bagus juga pakai .com |
| Path /about | Tidak mencurigakan |
| Domain yang belum jelas kebenarannya | Bisa kena false positive |

## 🙏 Terima Kasih

Setiap kontribusi membantu pengguna UnShort terhindar dari penipuan online.

Ada pertanyaan? Hubungi Admin.
