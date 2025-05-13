Customer Segmentation and Classification

Deskripsi Proyek

Proyek ini bertujuan untuk melakukan segmentasi pelanggan melalui **clustering** dan membangun model **klasifikasi multi-kelas** berdasarkan hasil clustering. Proyek terdiri dari dua tahap:

1. **Tahap 1: Clustering** (diasumsikan selesai): Mengelompokkan data pelanggan ke dalam klaster menggunakan algoritma clustering, menghasilkan kolom `Cluster` dan `Target` dalam dataset.
2. **Tahap 2: Klasifikasi**: Membangun model klasifikasi untuk memprediksi label `Target` (nilai 1–6) menggunakan algoritma Decision Tree, Random Forest, dan XGBoost, dengan evaluasi performa dan hyperparameter tuning.

Dataset yang digunakan adalah `data_clustering.csv`, yang berisi fitur pelanggan seperti jumlah transaksi, usia, saldo akun, lokasi, pekerjaan, dan kanal transaksi. Proyek ini memenuhi kriteria **Skilled** (implementasi sederhana dengan Decision Tree) dan **Advanced** (model ensemble dan tuning).

Struktur Dataset

Dataset `data_clustering.csv` memiliki **2228 baris** dan **61 kolom**, termasuk:

- **Fitur Numerik**: `TransactionAmount`, `CustomerAge`, `TransactionDuration`, `LoginAttempts`, `AccountBalance` (sudah distandarisasi).
- **Fitur Kategorikal (One-Hot Encoded)**: `TransactionType_Debit`, `Location_Atlanta`, `Location_Austin`, ..., `CustomerOccupation_Engineer`, `CustomerOccupation_Student`, `Channel_Branch`, `Channel_Online`.
- **Fitur Hasil Binning/Encoding**: `CustomerAge_bin`, `TransactionAmount_bin`, `CustomerAge_bin_encoded`, `TransactionAmount_bin_encoded`.
- **Fitur Hasil Clustering**: `Cluster` (klaster dari Tahap 1), `Target` (label klasifikasi 1–6).
- **Kolom Tanggal**: `TransactionDate`, `PreviousTransactionDate` (tidak digunakan untuk klasifikasi).

Kolom `Target` digunakan sebagai label untuk klasifikasi multi-kelas, dengan distribusi kelas yang tidak seimbang (kelas 4 terbanyak, kelas 3 paling sedikit).

Prasyarat

- Python 3.8 atau lebih tinggi
- Pustaka Python:
  - `pandas`
  - `scikit-learn`
  - `xgboost`
  - `joblib`
- Lingkungan: Jupyter Notebook (direkomendasikan) atau Python IDE

Hasil

- **Model yang Dihasilkan**:
  - `decision_tree_model.h5`: Model Decision Tree (Skilled).
  - `RandomForest_classification.h5`: Model Random Forest (Advanced).
  - `XGBoost_classification.h5`: Model XGBoost (Advanced).
  - `tuning_classification.h5`: Model Random Forest yang dituning (Advanced).
- **Evaluasi Performa**:

  - Tabel metrik (akurasi, presisi, recall, F1-score) untuk Decision Tree, Random Forest, dan XGBoost.
  - Contoh output tabel:

    Hasil Evaluasi Model:\
     Model Accuracy Precision Recall F1-Score\
    0 Decision Tree 0.784753 0.786214 0.784753 0.785234\
    1 Random Forest 0.825112 0.827345 0.825112 0.825678\
    2 XGBoost 0.838565 0.840123 0.838565 0.838912

  - Hasil tuning Random Forest, misalnya:

    Parameter Terbaik: {'max_depth': 20, 'min_samples_split': 2, 'n_estimators': 200}\
    Akurasi: 0.8296\
    Presisi: 0.8312\
    Recall: 0.8296\
    F1-Score: 0.8301

Lisensi
Dilisensikan di bawah MIT License.

Regard,
Faizal Riza
