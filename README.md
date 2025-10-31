# 🌏 Global Agriculture Challenge 2025: Prediksi Suhu Masa Depan

![Banner](https://img.shields.io/badge/Project-Climate%20Prediction-blue) ![Status](https://img.shields.io/badge/Status-Qualifying%20Round-green) ![Metric](https://img.shields.io/badge/Metric-MAPE-yellow)

Proyek ini adalah solusi dari tim **"Si data tuh"** untuk **Global Agriculture Challenge 2025: Predicting Our Climate's Future (Tahap Penyisihan)**. Kami membangun model *machine learning* untuk memprediksi suhu rata-rata tahunan (`Suhu_Rata_Rata_C`) berdasarkan data agrikultur dan lingkungan historis.

### 💻 Tech Stack

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white">
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white">
  <img src="https://img.shields.io/badge/Numpy-013243?style=for-the-badge&logo=numpy&logoColor=white">
  <img src="https://img.shields.io/badge/XGBoost-147F9B?style=for-the-badge&logo=xgboost&logoColor=white">
  <img src="https://img.shields.io/badge/LightGBM-4169E1?style=for-the-badge&logo=lightgbm&logoColor=white">
  <img src="https://img.shields.io/badge/CatBoost-FF6600?style=for-the-badge&logo=catboost&logoColor=white">
</p>

---

### 🎯 Tantangan & Misi Proyek

Di tengah ketidakpastian iklim yang mengancam ketahanan pangan global, tantangan kami adalah mengubah data agrikultur dan lingkungan yang kompleks menjadi prediksi yang jelas.

**Misi utama** adalah merancang dan membangun model *machine learning* yang dapat memprediksi variabel kunci iklim: **Suhu Rata-Rata Tahunan (`Suhu_Rata_Rata_C`)** dengan akurasi setinggi mungkin.

---

### 📂 Struktur Direktori

Berikut adalah struktur folderisasi yang digunakan dalam proyek ini:

. ├── data/
- │ ├── train.csv
- │ ├── test.csv
- │ └── sample_submission.csv
- ├── Si data tuh_DataMining_Code_Qualifying.ipynb # Notebook Solusi Tahap Penyisihan
- ├── Si data tuh_DataMining_Report_Qualifying.docx # Laporan Analisis
- ├── submission_qualifying.csv # Hasil Prediksi
- └── README.md

Notebook `Si data tuh_DataMining_Code_Qualifying.ipynb` berisi alur kerja lengkap, mulai dari EDA, *feature engineering*, hingga *modeling* yang menghasilkan submission tahap penyisihan.

---

### 📊 Dataset dan Metrik

#### Deskripsi Dataset
Dataset ini mencakup data historis yang kaya dari berbagai negara, menggabungkan faktor agrikultur, lingkungan, dan geo-temporal.

| Kolom | Deskripsi | Peran |
| :--- | :--- | :--- |
| `Tahun` | Tahun pengumpulan data | Prediktor |
| `Nama_Negara` | Negara tempat data dikumpulkan | Prediktor |
| `Wilayah` | Wilayah geografis | Prediktor |
| `Jenis_Tanaman` | Jenis tanaman yang ditanam | Prediktor |
| `Total_Curah_Hujan_mm` | Curah hujan tahunan (mm) | Prediktor |
| `Emisi_CO2_JT_Ton` | Emisi CO2 (juta ton) | Prediktor |
| `Hasil_Panen_Ton_per_HA`| Hasil panen (ton/hektar) | Prediktor |
| `Kejadian_Cuaca_Ekstrim`| Jumlah kejadian cuaca ekstrem | Prediktor |
| `Akses_Irigasi` | Persentase akses irigasi | Prediktor |
| `Penggunaan_Pestisida_KG_per_HA`| Penggunaan pestisida (kg/hektar) | Prediktor |
| `Penggunaan_Pupuk_KG_per_HA`| Penggunaan pupuk (kg/hektar) | Prediktor |
| `Indeks_Kesehatan_Tanah`| Indeks kesehatan tanah (0-100) | Prediktor |
| `Strategi_Adaptasi` | Strategi adaptasi iklim | Prediktor |
| `Suhu_Rata_Rata_C` | **Suhu rata-rata (°C)** | **Target** |

---

#### Metrik Evaluasi
Metrik evaluasi utama adalah **Mean Absolute Percentage Error (MAPE)**. Skor yang lebih rendah menunjukkan prediksi yang lebih baik. MAPE dipilih karena memberikan gambaran kesalahan relatif (persentase) yang intuitif.

$$MAPE = \frac{100\%}{n}\sum_{i=1}^{n}\left | \frac{y_i - \hat{y}_i}{y_i} \right |$$

- $n$ : jumlah total observasi
- $y_i$ : nilai aktual
- $\hat{y}_i$ : nilai prediksi

Peringkat akhir kompetisi didasarkan pada **Private Leaderboard (63% data uji)**.

---

### 🚀 Metodologi Tahap Penyisihan
*(Analisis berdasarkan `Si data tuh_DataMining_Code_Qualifying.ipynb` dan `...Report_Qualifying.docx`)*

Solusi kami untuk tahap penyisihan berfokus pada *feature engineering* yang mendalam dan seleksi model yang robust.

#### 1. Pra-pemrosesan Data
* **Data Cleansing**: Mengidentifikasi dan menangani nilai-nilai yang hilang (*missing values*) pada berbagai kolom.
* **Analisis Data Eksploratif (EDA)**: Kami melakukan visualisasi untuk memahami hubungan antara variabel prediktor dan variabel target (`Suhu_Rata_Rata_C`), serta menganalisis korelasi antar fitur.
* **Encoding**: Fitur kategorikal seperti `Nama_Negara`, `Wilayah`, `Jenis_Tanaman`, dan `Strategi_Adaptasi` diubah menjadi representasi numerik menggunakan `OrdinalEncoder` atau `OneHotEncoder` setelah analisis kardinalitas.

#### 2. Feature Engineering
* **Fitur Temporal**: Mengekstrak fitur berbasis waktu dari kolom `Tahun` untuk menangkap tren jangka panjang.
* **Fitur Interaksi**: Membuat fitur baru dengan mengkombinasikan faktor-faktor yang diduga memiliki hubungan kuat, seperti interaksi antara `Total_Curah_Hujan_mm` dan `Akses_Irigasi`.
* **Fitur Agregat**: Membuat fitur rata-rata atau total berdasarkan grup geografis (`Wilayah` atau `Nama_Negara`) untuk menangkap karakteristik regional.

#### 3. Pemodelan (Time Series Forecasting)
* **Validasi**: Kami menggunakan strategi validasi *time-series aware*, seperti *K-Fold cross-validation* yang diurutkan berdasarkan waktu, untuk mencegah *data leakage*.
* **Seleksi Model**: Kami melakukan *brute force* dan evaluasi pada beberapa model *tree-based* yang kuat untuk data tabular, termasuk:
    - `LightGBM` (LGBMRegressor)
    - `XGBoost` (XGBRegressor)
    - `CatBoost` (CatBoostRegressor)
* **Model Terbaik**: Berdasarkan skor MAPE pada validasi lokal, kami memilih model dengan performa terbaik untuk dijadikan *submission* akhir.

#### 4. Evaluasi dan Submission
* Model dievaluasi secara ketat menggunakan metrik **MAPE** untuk menyelaraskan dengan kriteria kompetisi.
* File `submission_qualifying.csv` dihasilkan oleh model terbaik yang telah dilatih pada keseluruhan data *training*.

---

### 📦 Cara Menjalankan Kode

1.  **Clone Repositori**:
    ```bash
    git clone https://github.com/GhazyUrbayani/AverageTemperature-MachineLearning-Prediction-intelecta
    cd AverageTemperature-MachineLearning-Prediction-intelecta
    ```

2.  **Siapkan Data**: Tempatkan file `train.csv` dan `test.csv` ke dalam folder `data/`.

3.  **Instalasi Library**: Direkomendasikan menggunakan *virtual environment*.
    ```bash
    pip install pandas numpy scikit-learn lightgbm xgboost catboost matplotlib seaborn jupyter
    ```

4.  **Jalankan Notebook**:
    Buka `Si data tuh_DataMining_Code_Qualifying.ipynb` dan jalankan semua sel untuk mereproduksi hasil.

### 📄 Output

Skrip akan menghasilkan file `submission_qualifying.csv` dalam format yang benar:

| id | Suhu_Rata_Rata_C |
| :--- | :--- |
| 8001 | -4.02 |
| 8002 | 23.23 |
| ... | ... |

---
*Kode dan analisis ini merupakan solusi kami untuk Tahap Penyisihan Global Agriculture Challenge 2025.*
