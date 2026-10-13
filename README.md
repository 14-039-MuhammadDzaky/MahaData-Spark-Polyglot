# Replikasi Eksperimen PolyFuseQL: Evaluasi Performa Hybrid RDBMS & NoSQL Menggunakan PySpark

Repositori ini berisi kode dan artefak replikasi parsial untuk evaluasi performa arsitektur *Polyglot Persistence* (hybrid RDBMS/NoSQL) dengan *query engine* **PySpark SQL**. Eksperimen ini menggunakan dataset standar industri TPC-H ($SF=0.01$).

---

## Ringkasan Eksperimen

- **Artikel Acuan**: *PolyFuseQL: A Unified Polyglot Persistence Query Framework for Hybrid Big Data Systems* | DOI :https://doi.org/10.3390/app16178512
1. **Data Generation (TPC-H SF=0.01)**:
   - Membuat *synthetic transactional dataset* menggunakan `DuckDB` dengan *Scale Factor* $SF = 0.01$.

2. **Database Ingestion & Persistence Simulation**:
   - **RDBMS**: Meng-ingest data ke dalam *In-Memory Relational Engine* (`SQLite`) untuk merepresentasikan struktur SQL/PostgreSQL.
   - **NoSQL**: Mengonversi baris data menjadi *JSON document stream* berformat *Key-Value* (`customer:<id>`) untuk merepresentasikan struktur Redis.

3. **Hybrid Query Engine Processing (PySpark)**:
   - Inisialisasi `SparkSession` lokal untuk mengolah *DataFrame* heterogen.
   - Menjalankan agregasi OLAP paralel menggunakan PySpark SQL pada masing-masing jenis arsitektur penyimpanan.

4. **Performance Benchmark & Export**:
   - Mencatat waktu komputasi dengan fungsi pewaktu presisi tinggi .
   - Merekam metrik evaluasi ke file `execution_time.csv` dan merepresentasikan visualisasi perbandingan melalui grafik batang `hasil_eksperimen.png`.
---

##  Struktur Repositori

```text
.
├── README.md             # Dokumentasi utama eksperimen
├── experiment.ipynb      # Notebook Google Colab (Dataset, PySpark, Metrik & Visualisasi)
├── execution_time.csv    # Tabel output metrik waktu eksekusi
├── hasil_eksperimen.png  # Visualisasi grafik perbandingan performa
└── requirements.txt      # Daftar dependensi Python      
```

---
## Cara Menjalankan Eksperimen
1. Klik tombol Open in Colab di bagian atas README ini.

2. Jalankan semua sel secara berurutan Cell 1 hingga Cell 3.

3. File execution_time.csv dan hasil_eksperimen.png akan dihasilkan secara otomatis di lingkungan kerja Colab.