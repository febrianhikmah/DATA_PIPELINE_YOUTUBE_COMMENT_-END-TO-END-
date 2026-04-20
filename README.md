# 🚀 END-TO-END DATA PIPELINE: KOMENTAR YOUTUBE (ETL + DATA WAREHOUSE)
---
## ✨ Gambaran Umum

Proyek ini merupakan implementasi pipeline data end-to-end untuk mengekstrak, memproses, dan menyimpan data komentar YouTube ke dalam data warehouse yang terstruktur.

Proyek ini berangkat dari pertanyaan sederhana:

>“Bagaimana cara mengubah data komentar YouTube yang tidak terstruktur menjadi dataset yang siap dianalisis?”

Untuk menjawabnya, saya membangun sistem pipeline ETL yang mampu mengambil data langsung dari YouTube, membersihkannya, memodelkannya ke dalam skema data warehouse, dan menyimpannya ke database PostgreSQL.

Seluruh proses berjalan otomatis hanya dengan memasukkan URL video.
---
## ⚙️ Gambaran Pipeline

Pipeline ini terdiri dari 4 tahap utama:

1. Input & Orchestrator
- User memasukkan URL video YouTube melalui aplikasi
- Sistem mengelola seluruh alur pipeline secara otomatis
- Konfigurasi API dan database disimpan terpusat
---
2. Extract Layer
- Mengambil metadata video (judul, channel, dll)
- Mengambil data komentar dan informasi author
- Data disimpan dalam format JSON (raw data)

📂 Output:
```pesta
data/raw/
 video.json
 comments.json
```
---
3. Transform Layer
- Data dibersihkan (missing value, format, dll)
- Dilakukan normalisasi data
- Mapping ke dalam star schema

📂 Output:
```pesta
data/processed/warehouse.json
```
Struktur data mulai dipisahkan menjadi:
- Fact table (komentar)
- Dimension table (video, author, channel, date)
---
4. Load Layer
- Data dimuat ke PostgreSQL sebagai Data Warehouse
- Menggunakan skema bintang (star schema)

📊 Tabel yang dihasilkan:

- fact_comments
- dim_video
- dim_channel
- dim_author
- dim_date
---
## 🧰 Teknologi yang Digunakan
| Layer            | Teknologi                          |
|------------------|-----------------------------------|
| Orchestration    | Python                            |
| Extract          | YouTube API                       |
| Transform        | Python (data cleaning & modeling) |
| Storage          | JSON                              |
| Data Warehouse   | PostgreSQL                        |
| Interface        | Streamlit                         |
---
## 🗂️ Struktur Proyek
```pesta
data/
  raw/
    comments.json
    video.json
  processed/
    warehouse.json

extract/
  comments.py
  video.py

transform/
  cleaning.py
  star_schema.py
  transform.py

load/
  load_to_postgres.py

app.py
config.py
```
---
## 🚀 Cara Kerja Sistem
- User memasukkan URL YouTube melalui aplikasi
- Sistem mengekstrak data komentar & metadata video
- Data mentah disimpan dalam format JSON
- Data dibersihkan dan dimodelkan ke star schema
- Data dimuat ke PostgreSQL sebagai data warehouse
- Data siap digunakan untuk analisis lebih lanjut
---
## 📊 Hasil Output
- Total komentar berhasil dikumpulkan dan diproses
- Data author dan tanggal berhasil dinormalisasi
- Tabel fact dan dimension terbentuk dengan relasi yang jelas
Data siap digunakan untuk:
- Analisis sentimen
- Analisis engagement
- Dashboard BI
---
## 💡 Insight & Nilai Proyek
- Mengubah data semi-structured menjadi structured data warehouse
- Implementasi nyata konsep ETL pipeline
- Penerapan star schema untuk analitik
- Automasi pipeline dari input hingga storage
- Modular pipeline (extract, transform, load terpisah jelas)
---
## 🏁 Kesimpulan

Proyek ini mensimulasikan bagaimana seorang data engineer membangun pipeline data dari sumber eksternal (API) hingga menjadi data warehouse yang siap dianalisis.

Melalui proyek ini, saya memahami pentingnya:

- Data cleaning sebelum analisis
- Desain data warehouse yang efisien
- Pemisahan proses ETL secara modular
- Automasi pipeline untuk efisiensi kerja
