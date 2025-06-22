# Static-Website-AWS-S3

Hosting Static Website Menggunakan Amazon S3 + CloudFront

## 📖 Deskripsi Proyek

Proyek ini adalah simulasi sederhana untuk menghosting website statis menggunakan layanan Amazon S3 dan CloudFront dari AWS. Website ini dirancang untuk menampilkan halaman sambutan yang terhubung ke profil LinkedIn sebagai bagian dari portofolio cloud computing saya.

Proyek ini bertujuan untuk:

* Mempelajari cara membuat bucket di Amazon S3.
* Mengaktifkan dan menonaktifkan static website hosting sesuai kebutuhan.
* Mengatur akses private dengan menggunakan CloudFront.
* Memahami proses deployment website statis di cloud secara aman.

---

## 🛠 Tools dan Teknologi

* **Amazon S3**: Penyimpanan cloud untuk file statis.
* **Amazon CloudFront**: CDN untuk mengakses file secara cepat dan aman.
* **HTML**: Struktur website sederhana menggunakan file `index.html`.
* **AWS Management Console**: Untuk melakukan konfigurasi S3 dan CloudFront.

---

## 🌟 Fitur Website

* Hosting website statis tanpa server.
* Akses cepat dari berbagai lokasi melalui CloudFront.
* Link publik hanya tersedia melalui CloudFront, bukan langsung dari S3.
* Website aman dari akses langsung dan hotlinking.

---

## 🌐 Link Website

Website dapat diakses melalui link berikut:
👉 [https://d1i2ty48obv6fm.cloudfront.net](https://d1i2ty48obv6fm.cloudfront.net)

---

## 🚀 Langkah Pembuatan dan Deployment

### 1. Buat Bucket di Amazon S3

* Masuk ke AWS Management Console → buka layanan Amazon S3.
* Klik **Create bucket**.
* Isi nama bucket (`link-daffa`) → region: Asia Pacific (Singapore).
* Nonaktifkan blokir public access → centang konfirmasi.

### 2. Upload File Website

* Siapkan file `index.html`.
* Upload file ke bucket menggunakan tombol "Upload".

### 3. (Opsional) Aktifkan Static Website Hosting

* **Jika hanya pakai S3**:

  * Buka tab **Properties** → bagian **Static website hosting**.
  * Aktifkan dan isi `index.html` di Index document.

* **Jika menggunakan CloudFront**:

  * **Lewati atau nonaktifkan fitur ini**, karena CloudFront tidak menggunakan endpoint `s3-website`.

### 4. Atur Bucket Policy untuk Akses via CloudFront OAC

Buka tab **Permissions** → klik **Bucket Policy**, lalu masukkan:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::link-daffa/*"
        },
        {
            "Sid": "AllowCloudFrontServicePrincipal",
            "Effect": "Allow",
            "Principal": {
                "Service": "cloudfront.amazonaws.com"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::link-daffa/*",
            "Condition": {
                "ArnLike": {
                    "AWS:SourceArn": "arn:aws:cloudfront::595351379764:distribution/E2QDAWE6E7FASN"
                }
            }
        }
    ]
}
```

### 5. Buat CloudFront Distribution

* Masuk ke layanan **CloudFront** → Create Distribution
* Isi nama distribusi dan pilih tipe: **Single website or app**
* Di bagian **Origin domain**, pilih S3 bucket *bukan versi static website*

  ```
  link-daffa.s3-website-ap-southeast-1.amazonaws.com
  ```
* Aktifkan opsi **Origin Access Control (OAC)**
* Pilih atau buat pengaturan OAC baru
* Di bagian **Default root object**, isi: `index.html`
* Klik **Create distribution**

---

## 📚 Pelajaran yang Didapat

* Membuat dan menghosting website statis di Amazon S3
* Mengelola bucket policy untuk akses **privat via CloudFront**
* Menggunakan CloudFront dengan OAC untuk keamanan tambahan
* Memahami perbedaan antara static website S3 vs CDN (CloudFront)

---

👤 Author

Daffa Satria Adi Dharma

---

## 📌 Catatan

Proyek ini adalah bagian dari portofolio cloud computing saya untuk level pemula.
