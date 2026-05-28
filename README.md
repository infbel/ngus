# 🛡️ NGUS - UnShort

Repository NGUS ini berisi data untuk mendeteksi **link phishing, scam, situs berbahaya, daftar putih dan lainnya** yang digunakan oleh Worker UnShort.

## 🤝 Cara Berkontribusi: detectPhishing.json

Cukup edit file `detectPhishing.json` dan tambahkan data.

## 📋 Panduan Isi Setiap Bagian

| Field | Artinya | Contoh |
|-------|---------|--------|
| malicious_domains | Domain jahat (phishing, scam, malware) | "bca-verifikasi.cfd" |
| bad_words | Kata-kata yang sering muncul di domain phishing | "verify", "login", "klaim" |
| bad_tlds | Ekstensi domain yang sering dipakai phishing | ".cfd", ".top", ".xyz" |
| brands | Nama brand yang sering dipalsukan untuk phishing | "bca", "shopee", "paypal" |
| safeDomainsForEncoding | Domain besar yang boleh punya banyak parameter encoding | "google.com", "amazon.com" |
| suspicious_paths | Path di URL yang sering dipakai phishing | "/login", "/verify" |
| redirectParams | Parameter URL yang digunakan untuk redirect ke website lain | "redirect", "url", "next" |

## 🔍 Cara Mendeteksi Link Phishing

Ciri-ciri link mencurigakan:

- Domain acak/tidak jelas (contoh: hjsd83jksd.top)
- Ekstensi murah (.cfd, .click, .top, .xyz)
- Mirip brand terkenal tapi beda dikit (contoh: paypal-verify.xyz)
- Berisi kata "login", "verify", "klaim" (contoh: bca-verifikasi.cfd)
- Dapat dari SMS/WA tidak dikenal

## ✏️ Cara Edit File

1. Buka file `detectPhishing.json` di repository ini
2. Klik tombol pensil (Edit) di pojok kanan atas
3. Tambahkan data baru di bagian yang sesuai
4. Klik "Commit changes" (tombol hijau)

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

- Setelah kamu edit file dan commit, admin akan melakukan review terlebih dahulu
- Jika data valid, admin akan menyetujui perubahan (merge)
- Setelah disetujui, Worker akan mengambil data baru dalam waktu maksimal 1 jam

## 💡 Yang JANGAN Ditambahkan

| Jangan tambahkan | Alasannya |
|------------------|-----------|
| google.com | Ini domain resmi, nanti kena false positive |
| .com ke bad_tlds | Terlalu umum, website bagus juga pakai .com |
| Path /about | Tidak mencurigakan |
| Domain yang belum jelas kebenarannya | Bisa kena false positive |

## 📢 Cara Kirim Laporan (Pull Request)

Ikuti langkah-langkah ini untuk mengusulkan perubahan:

1. **Fork repository ini** (klik tombol Fork di pojok kanan atas)

2. **Edit file `detectPhishing.json`** di fork kamu:
   - Klik file `detectPhishing.json`
   - Klik tombol pensil (Edit)
   - Tambahkan data baru sesuai format
   - Klik "Commit changes" (simpan di fork kamu)

3. **Buat Pull Request (PR)** ke repository utama:
   - Buka tab "Pull Requests"
   - Klik "New Pull Request"
   - Pilih branch fork kamu → branch utama
   - Klik "Create Pull Request"
   - Beri judul dan deskripsi singkat (contoh: "Menambahkan domain phishing baru")
   - Klik "Create Pull Request" lagi

4. **Tunggu admin review**:
   - Admin akan memeriksa data kamu
   - Jika valid, akan di-merge (disetujui)
   - Jika kurang jelas, admin akan bertanya di kolom komentar

## 🙏 Terima Kasih

Setiap kontribusi kamu membantu orang lain terhindar dari penipuan online. Setiap Pull Request akan direview secepat mungkin.

Ada pertanyaan? Hubungi admin.
