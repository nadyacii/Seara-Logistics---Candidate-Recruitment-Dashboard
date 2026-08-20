# Seara Logistics - Candidate Recruitment Dashboard

## 1. Project Overview

Seara Logistics - Candidate Recruitment Dashboard merupakan project analisis data yang dikembangkan sebagai bagian dari Seara Data Project. Seara Logistics merupakan perusahaan fiktif di industri Logistics & Supply Chain yang sedang mengembangkan tim data dan membuka posisi Data Analyst. Dalam proses rekrutmen, HR menghadapi tantangan karena kandidat memiliki latar belakang, keterampilan teknis, tujuan karier, dan lokasi yang beragam. Proses screening secara manual terhadap ratusan kandidat dapat memakan waktu dan berpotensi menghasilkan proses seleksi yang kurang konsisten.

Project ini bertujuan untuk mengubah data kandidat menjadi dashboard screening rekrutmen interaktif yang dapat membantu HR mengidentifikasi kandidat yang memenuhi kualifikasi, memahami pola rekrutmen, serta mendukung pengambilan keputusan berbasis data.

---

## 2. Objective

Project ini bertujuan untuk membantu tim HR dalam meningkatkan proses screening kandidat dengan:

- Mengidentifikasi kandidat yang memenuhi kualifikasi teknis.
- Menganalisis distribusi keterampilan kandidat.
- Mengevaluasi channel rekrutmen.
- Memahami tujuan dan motivasi kandidat.
- Menganalisis persebaran kandidat berdasarkan wilayah.
- Mengidentifikasi kandidat yang sedang aktif mencari pekerjaan.
- Memberikan rekomendasi yang dapat mendukung proses pengambilan keputusan rekrutmen.

---

## 3. Business Questions

Project ini dikembangkan untuk menjawab beberapa pertanyaan bisnis utama:

1. Berapa banyak kandidat yang memenuhi kriteria kualifikasi?
2. Channel rekrutmen mana yang menghasilkan kandidat paling banyak dan berkualitas?
3. Tujuan kandidat apa yang paling berkaitan dengan kandidat yang memenuhi kualifikasi?
4. Seberapa sesuai persebaran kandidat yang memenuhi kualifikasi dengan preferensi lokasi perusahaan?

---

## 4. Dataset

Dataset yang digunakan terdiri dari **681 data kandidat** dan **8 variabel** yang berkaitan dengan proses rekrutmen.

| Variabel | Deskripsi |
|----------|-----------|
| `ID` | Identitas unik untuk setiap kandidat. |
| `Domicile` | Domisili kandidat. |
| `Fresh Graduate Status` | Menunjukkan apakah kandidat merupakan mahasiswa atau fresh graduate. |
| `Employee Skills` | Keterampilan teknis yang dimiliki kandidat, seperti SQL, Python, Excel, dan Power BI. |
| `Career Goal` | Tujuan utama kandidat dalam mengikuti proses rekrutmen. |
| `Recruitment Channel` | Sumber atau channel tempat kandidat mengetahui perusahaan dan lowongan pekerjaan. |
| `Province` | Provinsi tempat tinggal kandidat yang digunakan untuk analisis geografis. |
| `Job Seeking Status` | Menunjukkan apakah kandidat sedang aktif mencari pekerjaan. |

### Variabel yang Digunakan

Analisis difokuskan pada variabel yang secara langsung mendukung analisis rekrutmen:

- Employee Skills
- Recruitment Channel
- Career Goal
- Fresh Graduate Status
- Province
- Job Seeking Status

### Variabel yang Tidak Digunakan

- **Domicile** — tidak digunakan karena informasi `Province` sudah cukup untuk merepresentasikan persebaran geografis kandidat pada tingkat provinsi.

---

## 5. Tools Used

| Tools | Penggunaan |
|------|------------|
| **Microsoft Excel** | Eksplorasi data, pengecekan data, dan persiapan awal dataset. |
| **Power Query** | Data cleaning, transformasi data, pemisahan nilai pada kolom multi-value, dan feature engineering. |
| **Google Looker Studio** | Pengembangan dashboard interaktif dan visualisasi data. |
| **Canva** | Penyusunan presentasi project dan data storytelling. |

---

## 6. Data Cleaning & Transformation

Tahap Data Cleaning & Transformation dilakukan untuk memastikan data kandidat memiliki struktur yang konsisten dan siap digunakan untuk analisis serta pengembangan dashboard.

### 1. Data Validation

Melakukan pengecekan terhadap dataset untuk memastikan tidak terdapat missing value dan duplicate record pada data kandidat.

Dataset awal terdiri dari **681 kandidat unik**.

### 2. Data Standardization

Beberapa kolom disesuaikan agar lebih relevan dengan konteks recruitment analysis:

- `Tools yang Ingin Dipelajari` → `Kemampuan Karyawan`
- `Target Join Komunitas` → `Target Masuk Perusahaan`
- `Tau Seara Data Dari Mana?` → `Mengetahui Perusahaan Dari Mana`
- `Cari Kerja` → `Aktif Cari Kerja`

Nilai `belum ada mapping` pada kolom `Provinsi` juga diperbaiki agar dapat digunakan dalam analisis geografis.

### 3. Multi-Value Data Transformation

Kolom `Kemampuan Karyawan` dan `Target Masuk Perusahaan` memiliki beberapa nilai dalam satu record.

Menggunakan **Power Query**, nilai tersebut dipisahkan menjadi baris individual agar setiap skill dan target dapat dianalisis secara terpisah.

Hasil transformasi menghasilkan **10.129 baris data**, dengan tetap mempertahankan **681 ID kandidat unik**.

### 4. Feature Engineering

Dibuat fitur baru berupa `qualified` untuk mengklasifikasikan kandidat berdasarkan kriteria teknis yang dibutuhkan untuk posisi Data Analyst.

Hasil klasifikasi:
- **460 kandidat Qualified**
- **221 kandidat Not Qualified**

### 5. Final Dataset

Dataset akhir kemudian digunakan sebagai dasar untuk Exploratory Data Analysis (EDA) dan pengembangan dashboard interaktif menggunakan Google Looker Studio.

---

## 7. Exploratory Data Analysis (EDA)

Tahap Exploratory Data Analysis (EDA) dilakukan untuk memahami karakteristik kandidat, mengidentifikasi pola dalam data, serta menjawab business questions yang telah ditentukan.

Analisis dilakukan berdasarkan beberapa aspek utama:

### a. Candidate Qualification

Menganalisis status kualifikasi kandidat berdasarkan kriteria teknis posisi Data Analyst.

Dari **681 kandidat**, sebanyak **460 kandidat (67,5%)** dikategorikan sebagai Qualified, sedangkan **221 kandidat (32,5%)** termasuk Not Qualified.

### b. Candidate Skills

Menganalisis keterampilan teknis yang dimiliki kandidat.

Skill yang paling banyak ditemukan adalah:
- SQL — 1.593 records
- Python — 1.546 records
- Excel — 1.491 records
- Power BI — 1.462 records
- Databases — 1.425 records

Hasil ini menunjukkan bahwa SQL, Python, Excel, dan Power BI merupakan keterampilan yang paling dominan dalam candidate pool.

### c. Recruitment Channel

Menganalisis sumber kandidat dalam mengetahui perusahaan.

Hasil eksplorasi menunjukkan:
- LinkedIn — 8.273 records
- Teman — 1.169 records
- Instagram — 687 records

LinkedIn menjadi channel dengan jangkauan kandidat terbesar.

### d. Career Goal

Menganalisis tujuan kandidat dalam mengikuti proses rekrutmen.

Tujuan yang paling banyak dipilih adalah:
- Upskill — 3.277 records
- Networking — 2.854 records
- Cari Kerja — 2.503 records
- Switch Career — 1.495 records

Hal ini menunjukkan bahwa upskill dan networking menjadi motivasi utama kandidat.

### e. Candidate Background

Menganalisis komposisi kandidat berdasarkan status mahasiswa dan fresh graduate untuk memahami karakteristik talent pool.

### f. Job Seeking Status

Menganalisis status kandidat yang sedang aktif mencari pekerjaan.

Dari hasil transformasi data, terdapat **8.058 records** dengan status aktif mencari kerja dan **2.071 records** yang tidak aktif mencari kerja.

### g. Geographic Distribution

Menganalisis persebaran kandidat berdasarkan provinsi.

Wilayah dengan jumlah records tertinggi antara lain:
- Jawa Barat — 2.759 records
- Jakarta — 1.738 records
- Jawa Timur — 1.362 records
- Jawa Tengah — 1.094 records
- Banten — 809 records

Analisis geografis digunakan untuk memahami konsentrasi kandidat dan mendukung strategi recruitment berdasarkan lokasi.

---
## 8. Key Insights

### 1. Sebagian Besar Kandidat Memenuhi Kualifikasi

Sebanyak **460 dari 681 kandidat (67,5%)** memenuhi kriteria teknis yang ditetapkan untuk posisi Data Analyst. Hal ini menunjukkan bahwa candidate pool memiliki potensi yang cukup besar untuk melanjutkan ke tahap seleksi berikutnya.

### 2. LinkedIn Menjadi Channel Rekrutmen Utama

**LinkedIn menyumbang lebih dari 80% kandidat**, sehingga menjadi channel dengan jangkauan terbesar dalam menarik kandidat. Namun, tingginya jumlah kandidat dari LinkedIn tidak secara otomatis menunjukkan kualitas kandidat yang lebih tinggi dibandingkan channel lainnya.

### 3. Active Job Seeker Memiliki Keterkaitan dengan Kualifikasi

Kandidat yang aktif mencari pekerjaan menunjukkan proporsi kandidat qualified yang lebih tinggi dibandingkan kandidat yang tidak aktif mencari pekerjaan. Status pencarian kerja dapat menjadi salah satu informasi tambahan dalam proses screening.

### 4. Upskill Menjadi Tujuan Kandidat yang Dominan

Upskill menjadi salah satu tujuan yang paling banyak dipilih kandidat. Hal ini menunjukkan tingginya minat kandidat terhadap pengembangan keterampilan dan peningkatan kompetensi.

Namun, karena tujuan upskill juga banyak ditemukan pada kandidat qualified maupun not qualified, variabel ini sebaiknya tidak digunakan sebagai satu-satunya dasar dalam menentukan kandidat.

### 5. Kandidat Banyak Terkonsentrasi di Pulau Jawa

Provinsi Jawa Barat, Jakarta, Jawa Timur, Jawa Tengah, dan Banten menjadi wilayah dengan jumlah kandidat terbesar. Persebaran ini menunjukkan bahwa candidate pool masih cukup terkonsentrasi di wilayah Pulau Jawa.

### 6. SQL Menjadi Keterampilan yang Paling Dominan

SQL menjadi salah satu keterampilan teknis yang paling banyak dimiliki kandidat, diikuti oleh Python, Excel, Power BI, dan Database. Hal ini menunjukkan bahwa candidate pool memiliki dasar kompetensi yang cukup relevan dengan kebutuhan posisi Data Analyst.

---

## 9. Business Recommendations

### 1. Mempertahankan LinkedIn sebagai Channel Utama

HR dapat tetap memprioritaskan LinkedIn sebagai channel utama untuk menjangkau kandidat, sekaligus mengoptimalkan channel lain seperti referral dan Instagram untuk memperluas jangkauan kandidat.

### 2. Menggunakan Qualification Flag untuk Screening Awal

HR dapat menggunakan `qualified` sebagai salah satu filter pada tahap screening awal untuk mempercepat proses identifikasi kandidat yang memenuhi persyaratan teknis.

### 3. Menggunakan Active Job Seeker sebagai Informasi Pendukung

Status aktif mencari kerja dapat digunakan sebagai informasi tambahan dalam menentukan prioritas kandidat, tetapi tetap dikombinasikan dengan kualifikasi teknis dan faktor lainnya.

### 4. Menerapkan Skill-Based Recruitment

Proses seleksi sebaiknya lebih berfokus pada keterampilan teknis yang relevan, seperti SQL, Python, Excel, dan BI Tools, dibandingkan hanya mempertimbangkan jumlah kandidat atau channel asal kandidat.

### 5. Memanfaatkan Potensi Fresh Graduate

Proporsi fresh graduate yang cukup besar dapat menjadi peluang bagi perusahaan untuk mengembangkan program seperti **internship, graduate development, mentoring, dan structured onboarding**.

### 6. Memperluas Jangkauan Rekrutmen Secara Geografis

Meskipun kandidat banyak terkonsentrasi di Pulau Jawa, HR dapat mempertimbangkan perluasan employer branding dan recruitment outreach ke wilayah lain untuk membangun candidate pool yang lebih beragam.
