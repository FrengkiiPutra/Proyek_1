# Data-Understanding-Data-Preprocessing
Tugas Minggu 2 - Proyek 1

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
