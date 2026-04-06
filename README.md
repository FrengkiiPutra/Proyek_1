# Proyek 1 Magang

Tahap 1: Data-Understanding-Data-Preprocessing
Tugas Minggu 2

Proyek ini merupakan dokumentasi lengkap mengenai proses Data Understanding dan Data Preprocessing yang saya kerjakan pada Minggu ke-2. Fokus utamanya adalah mengubah data mentah menjadi dataset siap latih (model-ready) dengan standar industri, menggunakan dataset Housing.csv (2000 baris).

Link Download Dataset: https://drive.google.com/file/d/1T3xvY-mR6_awNI_FQiedRXGxgZnbwosq/view?usp=sharing

#Tech Stack
Enviroment: Google Colab / Jupyter Notebook
Libraries: Pandas (Data manipulation), Scikit-Learn (Preprocessing & Splitting), Seaborn/Matplotlib (Visualisasi).

Fokus tahap ini: Audit & Preparation 
A. Inti Audit (Menjamin Kualitas)
1. Status Data: 100% Bersih (Tanpa missing values atau duplikat).
2. Analisis Target: Harga rumah (Price) terdistribusi normal/seimbang (Skewness -0.06), sehingga model tidak akan bias.
3. Insight: Variabel Area adalah faktor yang paling punya hubungan jelas dengan harga dibanding variabel numerik lainnya.

B. Inti Preparation (Menjamin Keamanan)
1. Split (80:20): Memisahkan data "belajar" dan data "ujian" agar hasil akurasi nantinya jujur.
2. Encoding: Mengubah kategori (Lokasi & Kondisi) menjadi angka agar bisa dihitung mesin.
3. Scaling: Menyamakan skala semua fitur (misal: luas ribuan vs kamar satuan) agar adil.

C. Anti-Leakage (Poin Spesial)
Proses scaling hanya belajar dari data Training. Ini memastikan data Test tetap rahasia bagi model sampai waktu ujian tiba.

Status Proyek: Data sudah siap dalam variabel X_train_final dan X_test_final. Siap lanjut ke Tahap Modeling.

Cara Menjalankan:
1. Persiapan Lingkungan: Buka file notebook di Google Colab.
2. Impor Dataset: Unggah file House Price Prediction Dataset.csv ke folder penyimpanan sementara di Colab (klik ikon folder di kiri, lalu upload).
3. Sinkronisasi Path: Pastikan nama file di dalam kode pd.read_csv() sudah sesuai dengan nama file yang diunggah.
4. Eksekusi Berurutan: Jalankan sel kode satu per satu dari atas ke bawah (Runtime > Run all) untuk menjaga kesinambungan variabel dan menghindari error NameError.




Tahap 2: Supervised Learning — Regression
Proyek 1: Baseline Modeling & Metric Evaluation (Minggu 3)

Deskripsi Tahap
Setelah data siap di Tahap Preprocessing (Minggu 2), fokus Minggu ke-3 adalah Model Benchmarking. Saya melakukan eksperimen dengan melatih 3 algoritma regresi berbeda secara simultan untuk membandingkan performanya. Tujuannya adalah mengidentifikasi model mana yang paling efektif menangkap pola antara fitur properti dan harga rumah.

A. Implementasi Multi-Model
Saya menggunakan pendekatan Automated Modeling Loop untuk melatih dan mengevaluasi tiga algoritma utama:
1. Linear Regression:Digunakan sebagai baseline (standar dasar) untuk melihat hubungan linear antar variabel.
2. Random Forest Regressor:Algoritma Ensemble (Bagging) yang kuat dalam menangani pola data non-linear dan kompleks.
3. Gradient Boosting Regressor:Algoritma Ensemble (Boosting) yang bekerja secara iteratif untuk meminimalkan kesalahan (error) pada prediksi sebelumnya.

B. Metrik Evaluasi: Instrumen Pengukuran Presisi
Keberhasilan model diukur menggunakan tiga metrik standar industri untuk memastikan validitas hasil:
MAE (Mean Absolute Error):Menghitung rata-rata selisih harga dalam satuan asli (menunjukkan rata-rata tebakan meleset).
RMSE (Root Mean Squared Error):Memberikan bobot lebih pada kesalahan yang besar; sangat penting untuk mendeteksi prediksi yang meleset jauh (outliers).
R² Score (Coefficient of Determination):Menunjukkan persentase variasi harga yang berhasil dijelaskan oleh model. Skor mendekati 1 berarti model sangat cerdas dalam mengenali pola.

C. Hasil & Visualisasi (Actual vs Predicted)
Untuk transparansi hasil, saya menyertakan visualisasi **Scatter Plot** yang membandingkan harga asli (Actual) dengan hasil tebakan model (Predicted).
Garis Diagonal Merah: Melambangkan kondisi ideal (Akurasi 100%).
Persebaran Titik Biru:** Menunjukkan seberapa dekat model dengan kenyataan.

> Status Performa: Berdasarkan pengujian, ditemukan bahwa model mengalami Underfitting. Titik-titik prediksi cenderung mendatar, yang menandakan model kesulitan membedakan harga antar rumah yang berbeda secara akurat.

D. Audit & Insight Profesional (Point of Interest)
Sebagai seorang Data Analyst/Scientist, hasil performa yang "rendah" (skor R² negatif/kecil) adalah temuan riset yang krusial. Berikut adalah analisis teknisnya:
1. Garbage In, Garbage Out: Rendahnya akurasi bukan disebabkan oleh kesalahan algoritma atau kodingan, melainkan Korelasi Lemah. Hasil audit menunjukkan fitur fisik seperti `Area` dan `Bedrooms` memiliki korelasi hampir nol terhadap `Price` pada dataset ini.
2. Karakteristik Data: Dataset ini teridentifikasi sebagai data dengan tingkat noise tinggi (kemungkinan data sintetis/acak), sehingga pola ekonomi tradisional (luas bertambah = harga bertambah) tidak terbaca secara statistik.
3. Kesimpulan Teknis: Model Linear Regression memberikan hasil yang sedikit lebih stabil (error terendah) dibanding model kompleks (Ensemble), yang membuktikan bahwa pada data tanpa pola yang jelas, algoritma sederhana justru lebih tahan terhadap overfitting yang ekstrem.


Cara Menjalankan Evaluasi:
1. Pastikan tahap Preprocessing sudah dijalankan.
2. Eksekusi blok kode **Modeling Loop** secara berurutan.
3. Tabel `df_performa` akan muncul secara otomatis yang mengurutkan model dari yang terbaik hingga terburuk berdasarkan skor evaluasi.

---
*💡 Repository ini disusun untuk menunjukkan alur kerja end-to-end Data Science, mulai dari pembersihan data hingga diagnosa model secara kritis dan analitis.*
