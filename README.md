# 🛒 Customer Segmentation — Data Mining UAS
### Segmentasi Pelanggan E-Commerce Menggunakan K-Means Clustering & PCA

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" />
  <img src="https://img.shields.io/badge/Framework-CRISP--DM-orange" />
  <img src="https://img.shields.io/badge/Method-K--Means%20%2B%20PCA-green" />
  <img src="https://img.shields.io/badge/Silhouette%20Score-0.8446%20✅-brightgreen" />
  <img src="https://img.shields.io/badge/Dataset-8.000%20rows-lightgrey" />
</p>

---

## 🔗 Link Penting

| Platform | Link |
|----------|------|
| 🌐 **Google Sites (Website Portofolio)** | (https://sites.google.com/global.ac.id/putrisofiatunmuzofar) |
| 🎥 **Video Presentasi YouTube** | (https://youtu.be/idD7UMOg3MU) |


---

## 👤 Identitas Mahasiswa

| | |
|---|---|
| **Nama** | PUTRI SOFIATUN MUZOFAR |
| **NIM** | 1224160108 |
| **Program Studi** | Sistem Informasi |
| **Institusi** | Institut Teknologi & Bisnis Bina Sarana Global |
| **Mata Kuliah** | Konsep Data Warehouse & Mining |
| **Dosen** | Agus Rifaldi, S.Kom |
| **Tahun Akademik** | 2025 – 2026 |

---

## 📌 Deskripsi Project

Project ini merupakan tugas akhir (UAS) mata kuliah **Konsep Data Warehouse & Mining** yang menerapkan metode **Clustering** untuk melakukan segmentasi pelanggan e-commerce Indonesia.

Menggunakan dataset RFM (Recency, Frequency, Monetary) dengan **8.000 data pelanggan**, project ini mengidentifikasi **5 segmen pelanggan** yang bermakna secara bisnis menggunakan algoritma **K-Means Clustering** yang dikombinasikan dengan **Principal Component Analysis (PCA)** sebagai teknik reduksi dimensi.

### 🎯 Tujuan
- Mengelompokkan pelanggan berdasarkan perilaku belanja dan data demografis
- Mencapai Silhouette Score ≥ 0.80 sebagai kriteria keberhasilan
- Menghasilkan rekomendasi strategi marketing yang actionable per segmen

---

## 🗂️ Struktur Repository

```
📦 customer-segmentation-datamining
 ┣ 📓 CustomerSegmentation.ipynb   ← Source code utama (Jupyter Notebook)
 ┣ 📊 customer_segmentation_rfm.csv ← Dataset yang digunakan
 ┣ 📄 README.md                    ← File ini
```

---

## 📊 Dataset

| Atribut | Detail |
|---------|--------|
| **Nama Dataset** | Customer Segmentation RFM |
| **Sumber** | [Kaggle — Customer Segmentation Tutorial](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python) |
| **Jumlah Data** | 8.000 baris × 10 kolom |
| **Missing Values** | 0 (tidak ada) |

### Variabel Dataset
| No | Variabel | Deskripsi | Tipe |
|----|----------|-----------|------|
| 1 | CustomerID | ID unik pelanggan | Kategorik |
| 2 | Gender | Jenis kelamin (Male/Female) | Kategorik |
| 3 | Age | Usia pelanggan (tahun) | Numerik |
| 4 | City | Kota asal pelanggan | Kategorik |
| 5 | AnnualIncome_juta | Pendapatan tahunan (juta rupiah) | Numerik |
| 6 | SpendingScore | Skor belanja 1–100 | Numerik |
| 7 | Recency_hari | Hari sejak transaksi terakhir | Numerik |
| 8 | Frequency_bulan | Rata-rata transaksi per bulan | Numerik |
| 9 | MonetaryValue_ribu | Total nilai transaksi (ribu rupiah) | Numerik |
| 10 | PreferredCategory | Kategori produk favorit | Kategorik |

---

## ⚙️ Tahapan CRISP-DM

### 1️⃣ Business Understanding
Perusahaan e-commerce menghadapi tantangan dalam memahami perilaku pelanggan yang beragam. Tanpa segmentasi yang tepat, anggaran pemasaran terbuang percuma karena kampanye bersifat generik. Project ini bertujuan mengidentifikasi kelompok pelanggan berdasarkan pola belanja mereka untuk mendukung strategi marketing yang lebih personal dan efektif.

### 2️⃣ Data Understanding
- Eksplorasi awal: preview data, tipe data, statistik deskriptif
- Pemeriksaan missing values → **0 missing values**
- Visualisasi distribusi variabel kategorik dan numerik
- Analisis korelasi antar variabel (heatmap)
- Deteksi outlier menggunakan metode IQR (boxplot)

### 3️⃣ Data Preparation
- **Seleksi Fitur**: 6 variabel numerik (Age, Income, SpendingScore, Recency, Frequency, Monetary)
- **Normalisasi**: StandardScaler → Z-Score (mean≈0, std≈1)
- **Reduksi Dimensi**: PCA 2 komponen → menjelaskan **≥94% variance** data asli

### 4️⃣ Modeling
Dua algoritma clustering diterapkan dan dibandingkan:

| Model | Algoritma | Parameter |
|-------|-----------|-----------|
| Model 1 | K-Means Clustering | K=5, n_init=20, max_iter=500 |
| Model 2 | Agglomerative Hierarchical | K=5, linkage='ward' |

Penentuan K optimal menggunakan **Elbow Method (SSE)** dan **Silhouette Score** pada ruang PCA.

### 5️⃣ Evaluation

| Metrik | K-Means | Agglomerative |
|--------|---------|---------------|
| **Silhouette Score ↑** | **0.8446 ✅** | ~0.82 ✅ |
| **Davies-Bouldin Index ↓** | **0.2162** | ~0.25 |
| Status (target ≥ 0.80) | **LULUS** | LULUS |

> 🏆 **Model terbaik: K-Means + PCA** dengan Silhouette Score **0.8446** — melampaui target evaluasi 80%.

### 6️⃣ Deployment
5 Segmen pelanggan yang berhasil ditemukan:

| Cluster | Segmen | Karakteristik |
|---------|--------|---------------|
| 0 | 🏆 **Champions** | Income & spending tinggi, aktif, monetary besar |
| 1 | 💙 **Loyal Customers** | Income menengah, konsisten, frekuensi baik |
| 2 | ⚠️ **At Risk** | Recency mulai panjang, frekuensi menurun |
| 3 | 🌱 **New Customers** | Usia muda, income rendah, baru bergabung |
| 4 | 😴 **Lost Customers** | Sangat lama tidak transaksi, butuh win-back |

---

## 🛠️ Library yang Digunakan

```python
pandas       # Manipulasi data
numpy        # Komputasi numerik
matplotlib   # Visualisasi dasar
seaborn      # Visualisasi statistik
scikit-learn # KMeans, PCA, StandardScaler, metrik evaluasi
scipy        # Hierarchical clustering & dendrogram
```

---

## 📈 Hasil Akhir

- ✅ **5 segmen pelanggan** berhasil diidentifikasi
- ✅ **Silhouette Score 0.8446** — melampaui target ≥ 0.80
- ✅ **Davies-Bouldin Index 0.2162** — mendekati 0, cluster sangat baik
- ✅ **PCA ≥94% variance** — kompresi dimensi tanpa kehilangan informasi
- ✅ Rekomendasi strategi marketing per segmen tersedia

---

## 📝 Lisensi

Project ini dibuat untuk keperluan akademik — Ujian Akhir Semester mata kuliah Konsep Data Warehouse & Mining, Institut Teknologi & Bisnis Bina Sarana Global, TA 2025–2026.
