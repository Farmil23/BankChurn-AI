
# 🏦 Customer Bank Subscription Prediction

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![MLOps](https://img.shields.io/badge/Structure-Modular_Pipeline-purple?style=for-the-badge&logo=githubactions&logoColor=white)]()

> **End-to-End Machine Learning Project untuk memprediksi apakah nasabah akan berlangganan deposito berjangka (Term Deposit).**

Repositori ini berisi implementasi lengkap sistem Machine Learning yang dibangun dengan prinsip **MLOps** dan **Modular Coding**. Sistem ini mencakup seluruh siklus hidup ML mulai dari pengambilan data (*ingestion*), validasi, transformasi, hingga pelatihan model.

---

## 🎯 Latar Belakang Masalah

Kampanye pemasaran langsung (*Direct Marketing*) adalah strategi umum di perbankan. Namun, menghubungi semua nasabah memakan biaya dan waktu.

**Tujuan Proyek:**
Membangun model klasifikasi yang dapat memprediksi apakah seorang nasabah akan berlangganan produk deposito berjangka (Yes/No) berdasarkan data demografis dan riwayat kampanye sebelumnya. Hal ini membantu bank menargetkan nasabah yang tepat dan meningkatkan efisiensi pemasaran.

---

## 🏗️ Arsitektur Proyek

Proyek ini tidak ditulis dalam satu file `main.py` raksasa, melainkan dipecah menjadi komponen-komponen modular agar mudah dipelihara dan diskalakan (*scalable*).

### Struktur Folder Utama
```bash
customer-bank-subscription-prediction/
├── bankmarketing/          # Source Code Utama (Package)
│   ├── components/         # Komponen Pipeline ML
│   │   ├── data_ingestion.py
│   │   ├── data_validation.py
│   │   ├── data_transformation.py
│   │   └── model_trainer.py
│   ├── pipeline/           # Orkestrasi Pipeline (Training/Prediction)
│   ├── entity/             # Definisi Struktur Data (Config & Artifacts)
│   ├── utils/              # Fungsi Bantuan (Helper Functions)
│   ├── logging/            # Sistem Pencatatan Log Custom
│   └── exception/          # Penanganan Error Custom
├── data_schema/            # Definisi Skema Data (schema.yaml)
├── bank-data/              # Data Mentah (CSV)
├── main.py                 # Entry Point Aplikasi
├── push_data.py            # Script upload data ke MongoDB
└── requirements.txt        # Daftar Dependensi

```

---

## 🔄 Alur Pipeline (Workflow)

Sistem bekerja secara berurutan melalui beberapa tahapan (*Pipeline*):

1. **💾 Data Ingestion**:
* Mengambil data dari database **MongoDB**.
* Membagi data menjadi *Train* dan *Test set*.


2. **✅ Data Validation**:
* Memvalidasi skema data menggunakan `schema.yaml`.
* Mendeteksi *Data Drift* (perubahan distribusi data) untuk memastikan kualitas data.


3. **🛠️ Data Transformation**:
* Menangani nilai yang hilang (*Missing Values*).
* Melakukan *Encoding* pada fitur kategorikal.
* Melakukan *Scaling* pada fitur numerik.
* Menyimpan objek *preprocessor* untuk digunakan saat prediksi nanti.


4. **🤖 Model Training**:
* Melatih berbagai algoritma klasifikasi.
* Mengevaluasi performa model dan menyimpannya sebagai artefak.



---

## 🛠️ Teknologi & Tools

* **Bahasa**: Python
* **Database**: MongoDB (Atlas/Local)
* **ML Libraries**: Scikit-learn, Pandas, NumPy
* **Utilities**: PyYAML, Dil (untuk serialisasi objek)
* **Konsep**: Exception Handling, Custom Logging, Artifact Management

---

## 🚀 Cara Menjalankan (Local)

Ikuti langkah-langkah ini untuk menjalankan proyek di komputer Anda:

### 1. Clone Repositori

```bash
git clone [https://github.com/Farmil23/customer-bank-subscription-prediction.git](https://github.com/Farmil23/customer-bank-subscription-prediction.git)
cd customer-bank-subscription-prediction

```

### 2. Setup Environment

Buat virtual environment agar dependensi terisolasi.

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate

```

### 3. Install Dependensi

```bash
pip install -r requirements.txt

```

### 4. Konfigurasi MongoDB

Proyek ini mengambil data dari MongoDB. Anda perlu mengatur variabel lingkungan (*Environment Variable*) untuk URL koneksi MongoDB Anda.
Buat file `.env` atau export langsung di terminal:

```bash
export MONGO_DB_URL="mongodb+srv://<username>:<password>@cluster0.mongodb.net/?retryWrites=true&w=majority"

```

### 5. Push Data ke Database (Pertama Kali)

Gunakan script yang tersedia untuk mengunggah dataset CSV lokal ke MongoDB.

```bash
python push_data.py

```

### 6. Jalankan Training Pipeline

Jalankan file utama untuk memulai proses training dari awal.

```bash
python main.py

```

---

## 📊 Hasil & Artefak

Setelah proses training selesai, sistem akan menghasilkan folder `Artifacts/` yang berisi:

* `data_ingestion/`: File train.csv dan test.csv.
* `data_validation/`: Laporan validasi data.
* `data_transformation/`: Objek preprocessor (`preprocessor.pkl`) dan array numpy.
* `model_trainer/`: Model yang sudah dilatih (`model.pkl`).

---

## 🤝 Kontribusi

Proyek ini terbuka untuk pengembangan lebih lanjut (misalnya: menambahkan Deployment ke AWS/Azure, atau menambahkan frontend UI). Silakan buat *Pull Request*!

---

<div align="center">
<small>Developed by Farhan Kamil Hermansyah - 152024150</small>
</div>

```

```
