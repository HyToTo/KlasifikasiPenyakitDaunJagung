# 🌽 Deteksi Penyakit Daun Jagung Berbasis Hybrid CNN

Proyek ini merupakan sistem **deteksi penyakit daun jagung berbasis Computer Vision** yang menggunakan model **Hybrid CNN** untuk mengklasifikasikan kondisi daun jagung ke dalam tiga kategori, yaitu **Hawar, Karat, dan Sehat**.

Sistem dikembangkan menggunakan **Python, TensorFlow, Flask, MySQL, dan Gemini AI**. Hasil klasifikasi dari model akan ditampilkan melalui aplikasi berbasis web, kemudian Gemini AI digunakan untuk memberikan penjelasan singkat dan saran penanganan berdasarkan hasil prediksi.

## 📌 Fitur

* 🌽 Deteksi kondisi penyakit pada daun jagung.
* 🤖 Klasifikasi menggunakan model Hybrid CNN.
* 🔍 Tiga kelas klasifikasi:

  * **Hawar**
  * **Karat**
  * **Sehat**
* 📊 Menampilkan hasil prediksi dan tingkat confidence.
* 🧠 Menggunakan Gemini AI untuk memberikan penjelasan dan saran penanganan.
* 🗄️ Menyimpan riwayat hasil deteksi ke database MySQL.
* 🌐 Menyediakan antarmuka berbasis web menggunakan Flask.
* 📁 Menyimpan gambar yang diunggah pada folder `static/uploads`.

## 🧠 Teknologi yang Digunakan

| Teknologi          | Kegunaan                                                |
| ------------------ | ------------------------------------------------------- |
| Python             | Bahasa pemrograman utama                                |
| TensorFlow / Keras | Pemrosesan dan penggunaan model CNN                     |
| Hybrid CNN         | Model klasifikasi penyakit daun jagung                  |
| Flask              | Framework aplikasi web                                  |
| MySQL              | Penyimpanan riwayat hasil deteksi                       |
| Gemini AI          | Analisis dan saran penanganan                           |
| NumPy              | Pengolahan data numerik                                 |
| Pillow             | Pemrosesan gambar                                       |
| Ngrok              | Akses aplikasi Flask melalui internet saat pengembangan |

## 🔬 Kelas Deteksi

Model digunakan untuk melakukan klasifikasi terhadap tiga kondisi daun jagung:

### 1. Hawar

Daun jagung yang teridentifikasi mengalami penyakit hawar.

### 2. Karat

Daun jagung yang teridentifikasi mengalami penyakit karat.

### 3. Sehat

Daun jagung yang tidak menunjukkan indikasi penyakit berdasarkan hasil klasifikasi model.

## 🏗️ Alur Sistem

```text
Pengguna
   │
   ▼
Upload Gambar Daun Jagung
   │
   ▼
Preprocessing Gambar
   │
   ▼
Model Hybrid CNN
   │
   ▼
Prediksi Kelas
   │
   ├── Hawar
   ├── Karat
   └── Sehat
   │
   ▼
Confidence Score
   │
   ▼
Gemini AI
   │
   ▼
Penjelasan & Saran Penanganan
   │
   ▼
MySQL
   │
   ▼
Riwayat Hasil Deteksi
```

## 📁 Struktur Repository

Struktur repository yang disarankan:

```text
TugasAkhirKompurel/
│
├── Flask_TugasAkhirKompurel.ipynb
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
│
├── model/
│   └── model_akhir.h5
│
├── static/
│   └── uploads/
│
└── templates/
    └── index.html
```

> **Catatan:** File dataset berukuran besar sebaiknya tidak dimasukkan langsung ke repository GitHub.

## ⚙️ Instalasi

### 1. Clone Repository

```bash
git clone https://github.com/USERNAME/TugasAkhirKompurel.git
cd TugasAkhirKompurel
```

Ganti `USERNAME` dengan username GitHub pemilik repository.

### 2. Buat Virtual Environment

```bash
python -m venv venv
```

Aktifkan environment:

**Windows:**

```bash
venv\Scripts\activate
```

**Linux / macOS:**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 🗄️ Konfigurasi Database

Sistem menggunakan MySQL dengan database:

```text
jagung_db
```

Tabel yang digunakan:

```text
history
```

Struktur tabel:

```text
id
filename
prediction
confidence
solution
created_at
```

Contoh SQL:

```sql
CREATE DATABASE jagung_db;

USE jagung_db;

CREATE TABLE history (
    id INT AUTO_INCREMENT PRIMARY KEY,
    filename VARCHAR(255),
    prediction VARCHAR(100),
    confidence FLOAT,
    solution TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 🔐 Konfigurasi API Gemini

API key **tidak boleh ditulis langsung di dalam source code atau di-upload ke GitHub**.

Gunakan environment variable, misalnya:

```python
import os

API_KEY = os.getenv("GEMINI_API_KEY")
```

Kemudian atur environment variable:

**Windows:**

```bash
set GEMINI_API_KEY=API_KEY_ANDA
```

**Linux / macOS:**

```bash
export GEMINI_API_KEY=API_KEY_ANDA
```

Untuk pengembangan lokal, file `.env` juga dapat digunakan.

Contoh `.env`:

```text
GEMINI_API_KEY=your_api_key
DB_HOST=localhost
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=jagung_db
```

Tambahkan `.env` ke `.gitignore:

```text
.env
```

## ▶️ Menjalankan Aplikasi

Setelah konfigurasi selesai, jalankan Flask:

```bash
python app.py
```

Kemudian buka browser dan akses:

```text
http://127.0.0.1:5000
```

Pengguna dapat mengunggah gambar daun jagung untuk mendapatkan hasil klasifikasi.

## 📊 Hasil Prediksi

Sistem menghasilkan informasi berupa:

* Kelas hasil prediksi.
* Confidence score.
* Probabilitas masing-masing kelas.
* Penjelasan dari Gemini AI.
* Saran penanganan.
* Riwayat deteksi yang disimpan ke MySQL.

Contoh hasil:

```text
Prediksi   : Hawar
Confidence : 94.52%

Analisis:
Daun jagung terdeteksi mengalami penyakit hawar.

Saran:
Lakukan pemantauan tanaman dan penanganan sesuai kondisi
serangan penyakit pada tanaman.
```

## 📓 Google Colab

Notebook pengembangan tersedia pada:

```text
Flask_TugasAkhirKompurel.ipynb
```

Notebook tersebut digunakan untuk proses pengembangan dan pengujian sistem menggunakan Google Colab.

## ⚠️ Keamanan

Jangan mengunggah informasi sensitif ke repository publik, seperti:

* API Key Gemini.
* Password MySQL.
* Token Ngrok.
* Credential database.
* File `.env`.

Gunakan `.env` atau environment variable untuk menyimpan informasi tersebut.

## 🎯 Tujuan Pengembangan

Proyek ini dikembangkan sebagai penerapan teknologi **Computer Vision dan Artificial Intelligence** untuk membantu proses identifikasi penyakit pada daun jagung secara otomatis.

Sistem diharapkan dapat menjadi alat bantu dalam mengenali kondisi tanaman berdasarkan citra daun dan memberikan informasi awal mengenai hasil deteksi.

## 👨‍💻 Pengembang

**Galang Finto Anergi**

Program Studi Teknik Informatika
Universitas Muhammadiyah Ponorogo

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan akademik dan penelitian.
