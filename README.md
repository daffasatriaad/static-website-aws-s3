# Static-Website-AWS-S3
Hosting Static Website Menggunakan Amazon S3

## 📖 Deskripsi Proyek
Proyek ini adalah simulasi sederhana untuk menghosting website statis menggunakan layanan Amazon S3 dari AWS. Website ini dirancang untuk menampilkan halaman sambutan yang terhubung ke profil LinkedIn sebagai bagian dari portofolio cloud computing saya.

Proyek ini bertujuan untuk:
- Mempelajari cara membuat bucket di Amazon S3.
- Mengaktifkan fitur static website hosting.
- Mengatur bucket agar dapat diakses publik.
- Memahami proses deployment website di cloud secara sederhana.

---

## 🛠 Tools dan Teknologi
- *Amazon S3*: Penyimpanan cloud yang digunakan sebagai hosting website statis.
- *HTML*: Struktur website sederhana menggunakan file index.html.
- *AWS Management Console*: Untuk melakukan konfigurasi S3.

---

## 🌟 Fitur Website
- Hosting website statis tanpa memerlukan server.
- Endpoint publik yang dapat diakses siapa saja.
- Menampilkan halaman sambutan dan tombol LinkedIn.
- Dapat digunakan untuk latihan dan portofolio AWS.

---

## 🌐 Link Website
Website dapat diakses melalui link berikut:
👉 [Klik untuk mengunjungi website](http://web-portofolio-daffa.s3-website-ap-southeast-1.amazonaws.com)

---

## 🚀 Langkah Pembuatan dan Deployment

### 1. Buat Bucket di Amazon S3
- Masuk ke AWS Management Console → buka layanan Amazon S3.
- Klik *Create bucket*.
- Isi nama bucket (contoh: web-portofolio-daffa) → region: Asia Pacific (Singapore).
- Nonaktifkan blokir public access → Centang konfirmasi.

### 2. Upload File Website
- Siapkan file index.html.
- Upload file ke bucket.

### 3. Aktifkan Static Website Hosting
- Buka tab *Properties* di bucket.
- Scroll ke bagian *Static website hosting* → klik *Edit*.
- Pilih *Enable* → isi index.html di Index document.
- Save changes.

### 4. Atur Bucket Policy Menjadi Public
- Buka tab *Permissions* → klik *Bucket Policy*.
- Masukkan policy berikut:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::web-portofolio-daffa/*"
    }
  ]
}
```

### 5. Mengakses Website

- Dapatkan bucket website endpoint di tab Properties.
- Buka link tersebut di browser.

---

## 📚 Pelajaran yang Didapat

- Membuat dan menghosting website statis di Amazon S3.
- Mengelola bucket policy untuk akses publik.
- Memahami konsep hosting tanpa server (serverless).

---

👤 Author

Daffa Satria Adi Dharma

---
