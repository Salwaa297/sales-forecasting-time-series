# Sales Forecasting Using ARIMA

## Deskripsi Proyek

Proyek ini berfokus pada analisis pola revenue penjualan dan forecasting menggunakan metode **Autoregressive Integrated Moving Average (ARIMA)**. Analisis dilakukan pada data transaksi retail yang diagregasi menjadi data time series mingguan untuk memahami pola perubahan revenue serta memperkirakan pendapatan pada periode mendatang.

## Tujuan

- Menganalisis karakteristik dan pola perubahan revenue penjualan.
- Membangun model time series menggunakan metode ARIMA.
- Melakukan forecasting revenue untuk 12 minggu mendatang.
- Mengevaluasi performa model berdasarkan metrik kesalahan prediksi.

## Dataset

Dataset yang digunakan adalah **Global Retail Sales Dataset** dari Kaggle.

- **Sumber:** [Global Retail Sales Dataset – Kaggle](https://www.kaggle.com/datasets/hamza0027/global-retail-sales-dataset)
- **Jumlah transaksi:** 5.000 data
- **Periode:** Januari 2023–Juni 2025
- **Jumlah observasi setelah agregasi:** 130 periode mingguan
- **Variabel utama:** `order_date` dan `revenue`
- **File dataset:** `real_world_sales_dataset_5000.csv`

Data transaksi diolah menjadi data revenue mingguan sebagai dasar analisis dan forecasting.

## Tahapan Analisis

1. **Data Preprocessing**: Memeriksa missing value dan data duplikat, mengubah tipe data tanggal, mengurutkan transaksi berdasarkan waktu, mengagregasi revenue mingguan, serta mendeteksi outlier menggunakan metode Interquartile Range (IQR).
2. **Exploratory Data Analysis (EDA)**: Menganalisis statistik deskriptif, distribusi revenue, tren mingguan, dan fluktuasi penjualan melalui visualisasi.
3. **Train-Test Split**: Membagi data secara kronologis dengan proporsi 80% data training dan 20% data testing.
4. **Uji Stasioneritas**: Menggunakan Augmented Dickey-Fuller (ADF) Test untuk menguji stasioneritas data.
5. **Identifikasi dan Pemodelan ARIMA**: Mengidentifikasi parameter melalui grafik ACF dan PACF serta membandingkan kandidat model berdasarkan Akaike Information Criterion (AIC).
6. **Forecasting dan Evaluasi**: Melakukan prediksi revenue dan mengevaluasi model menggunakan MAE, RMSE, MAPE, serta Ljung-Box Test.

## Hasil Analisis

Model terbaik yang diperoleh adalah **ARIMA(1,0,1)** berdasarkan nilai AIC terendah dari kandidat model yang diuji.

| Metrik | Hasil |
|---|---:|
| ADF p-value | 0,002309 |
| AIC | 2512,303 |
| MAE | 38.649,69 |
| RMSE | 50.108,36 |
| MAPE | 24,89% |
| Ljung-Box p-value | 0,730 |

Hasil pengujian ADF menunjukkan bahwa data revenue mingguan telah stasioner sehingga tidak memerlukan differencing tambahan (\(d=0\)).

Evaluasi model menghasilkan MAPE sebesar 24,89%. Hasil Ljung-Box Test menunjukkan tidak terdapat autokorelasi residual yang signifikan pada tingkat signifikansi 5%.

Forecasting untuk 12 minggu mendatang menunjukkan bahwa revenue diperkirakan berada pada kisaran **192.000–193.500 per minggu**, dengan kecenderungan menurun secara perlahan. Model dapat memberikan gambaran umum revenue jangka pendek, tetapi belum sepenuhnya menangkap fluktuasi ekstrem pada data aktual.

## Tools dan Teknologi

- **Programming Language:** Python
- **Data Processing:** Pandas, NumPy
- **Data Visualization:** Matplotlib
- **Time Series Modeling:** Statsmodels
- **Model Evaluation:** Scikit-learn
- **Development Environment:** Google Colab

## Struktur Repository

- `README.md`: Dokumentasi proyek.
- Notebook kode Python: Implementasi preprocessing, EDA, pemodelan ARIMA, forecasting, dan evaluasi.
- Laporan proyek: Dokumentasi metodologi, hasil analisis, dan kesimpulan.
- `real_world_sales_dataset_5000.csv`: Dataset transaksi penjualan.

## Cara Menjalankan

1. Clone atau unduh repository ini.
2. Buka notebook proyek menggunakan Google Colab atau Jupyter Notebook.
3. Pastikan dataset tersedia dan sesuaikan lokasi file pada kode jika diperlukan.
4. Jalankan setiap bagian notebook secara berurutan untuk mereproduksi proses analisis hingga forecasting.

## Kontributor

- Putri Sofiyatus Salwa
- Cintiya Agustin Nareswari
- Nadine Putri Aulia
