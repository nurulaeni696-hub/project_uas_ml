# 🟣 Smart City - Flood Risk Clustering Dashboard (UAS Machine Learning)

Aplikasi web interactive ini adalah dashboard analisis data mitigasi bencana banjir tingkat kecamatan di Provinsi Jawa Barat berbasis **Machine Learning (Clustering)**. Dikembangkan khusus untuk memenuhi kriteria penilaian tingkat tinggi (UAS) dengan desain premium bertema **dark-purple** yang responsif dan siap dideploy.

---

## 🔐 Kredensial Login Sistem (Sesi Aktif)
Aplikasi diamankan menggunakan session state login sederhana:
- **Username**: `admin`
- **Password**: `123`

---

## ⚡ Fitur Utama Dashboard
1. **🏠 Dashboard**: Ringkasan statistik eksekutif (Total Kecamatan, Rata-rata tahunan, Kabupaten terbanyak) disajikan dalam kartu metrik modern yang interaktif, dilengkapi penjelasan pilar *Smart Environment* & *Smart Governance*.
2. **📊 Dataset**: Eksplorasi interaktif dataframe historis, ringkasan statistik deskriptif otomatis, serta uji kualitas kualitas data (Missing Value analysis). Mendukung pengunggahan dataset kustom (.csv).
3. **⚙️ Clustering**: Pemodelan real-time dengan standardisasi data (`StandardScaler`) otomatis untuk 3 algoritma:
   - **K-Means Clustering** (Jumlah klaster & random state dinamis)
   - **Agglomerative Hierarchical Clustering** (Jumlah klaster & kriteria linkage dinamis)
   - **DBSCAN Clustering** (Epsilon & min-samples dinamis)
4. **🏆 Evaluasi**: Pengukuran performa model menggunakan metrik ilmiah **Silhouette Score** dan **Davies-Bouldin Score** yang disajikan secara komparatif bersisian beserta mahkota penentu model terbaik.
5. **🔮 Prediksi**: Form pendeteksian risiko wilayah baru dengan inputCurah Hujan, Ketinggian Air, dan Jumlah Kejadian. 
   > **Catatan Teknis**: Karena DBSCAN dan Agglomerative Clustering tidak memiliki fungsi `.predict()` bawaan untuk data baru, sistem ini menyertakan implementasi **K-Nearest Neighbors (KNN) Classifier** sebagai proxy terlatih untuk memprediksi cluster wilayah baru secara real-time.
6. **📈 Visualisasi**: Plot 2D Scatter sebaran klaster, diagram batang sebaran anggota, pie chart persentase risiko, dan heatmap korelasi fitur menggunakan grafik **Matplotlib & Seaborn** yang disesuaikan secara visual dengan background gelap dashboard.
7. **💡 Smart City Analysis**: Matriks perumusan aksi tanggap cepat per-klaster risiko (Prioritas I - Merah, Prioritas II - Kuning, Prioritas III - Hijau) untuk mendukung pengambilan kebijakan berbasis data (*Data-Driven Policy*).

---

## 🛠️ Langkah Menjalankan Aplikasi Secara Lokal

### 1. Prasyarat
Pastikan Anda sudah menginstal Python (versi 3.8 ke atas) di perangkat Anda.

### 2. Kloning / Ekstrak Folder Project
Masuk ke direktori utama folder project:
```bash
cd project_uas_ml
```

### 3. Instalasi Dependensi
Instal pustaka Python yang dibutuhkan menggunakan file `requirements.txt` yang telah disediakan:
```bash
pip install -r requirements.txt
```

### 4. Menjalankan Dashboard Streamlit
Jalankan perintah berikut pada terminal atau PowerShell:
```bash
streamlit run app.py
```

Aplikasi akan otomatis terbuka pada browser Anda di alamat lokal `http://localhost:8501`.

---

## 📂 Struktur File Utama
- `app.py`: Source code utama implementasi Streamlit, UI CSS, algoritma clustering, evaluasi, dan model prediksi.
- `hasil_cluster_banjir_uts.csv`: Dataset utama yang berisi riwayat kejadian banjir di Jawa Barat.
- `requirements.txt`: Daftar pustaka Python prasyarat.
- `README.md`: Panduan dokumentasi proyek ini.
