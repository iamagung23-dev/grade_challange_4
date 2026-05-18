[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/IJWmKOok)
# Graded Challenge 4

_Graded Challenge ini dibuat guna mengevaluasi pembelajaran pada Hacktiv8 Comprehensive Data Analytics Program khususnya pada pemahaman fundamental analisa data dan pengolahan data menggunakan Google Spreadsheet._

---

## General Instructions

- *Graded Challenge 4* dikerjakan dalam **Google Spreadsheet** dan **Google Slide**
- Pengolahan data dilakukan di Google Spreadsheet
- Penjelasan dan pembuatan laporan dikerjakan di dalam Google Slide dengan outline berikut:
  - Judul laporan
  - Latar belakang masalah, tujuan bisnis, dan problem statement (Boleh di-copy paste dari soal)
  - Penjabaran masalah
  - Penjelasan dataset yang digunakan berdasarkan metrik dan key questions (penjelasan mencakup kolom apa yang dibutuhkan, bagaimana kondisi datanya, dan data cleaning apa yang diterapkan jika diperlukan).
  - Hasil pengolahan data beserta insightnya (satu key question satu slide)
  - Kesimpulan (Berisikan kesimpulan analisa data dan ditambahkan dengan actionable insightnya)
---

## Assignment Submission
- Buat file markdown (.md) yang berisikan link Google Spreadsheet dan Google Slide yang sudah dikerjakan dengan nama file `submission.md`.
- Beri Judul masing-masing file dengan: `P1G4-Nama`. Misal `P1G4-Fahmi Iman`.
- Atur sharing access ke `Anyone with the link can edit`.
- Perubahan apapun setelah dikumpulkan, tidak akan dinilai (akan terlihat dari history perubahan).
---

## Assignment Objectives
*Graded Challenge 4* ini dibuat guna mengevaluasi pemahaman fundamental data analytics and penggunaan spreadsheet sebagai berikut:

- Mampu menjabarkan masalah menjadi key questions.
- Mampu melakukan pengolahan dan analisa data dengan Google Spreadsheet.
- Mampu membuat insight dari data yang diolah
- Mampu membuat actionable recommendation dari insight yang ditemukan
- Mampu membuat reporting
---

## Dataset
Kamu dapat mengakses data dari link [ini](https://www.kaggle.com/datasets/luvathoms/portugal-real-estate-2024) berikut dengan penjelasan informasi masing-masing kolomnya. Pastikan sudah sign up ke Kaggle.

Dataset didownload dengan ekstensi `.csv`, lalu import ke Google Spreadsheet.

---

## Assignment Instructions and Cases

**Latar Belakang**: Kota-kota di Portugal mengalami perkembangan pesat dalam sektor perumahan. Sebagai seorang analis di perusahaan real estate, tugas Anda adalah mengidentifikasi peluang, tantangan, dan membuat rekomendasi strategis untuk meningkatkan profitabilitas perusahaan berdasarkan tren dan pola data perumahan.

**Tujuan Bisnis**: Perusahaan ingin meningkatkan penjualan properti dengan harga yang sesuai target pasar serta memahami faktor-faktor yang paling memengaruhi harga jual di berbagai kota di Portugal.

**Problem Statement**: Bagaimana cara meningkatkan penjualan properti di Portugal sebesar 10% dalam 6 bulan dengan menganalisis tren pasar dan memahami variabel kunci yang mempengaruhi harga jual properti?

Tugas kamu menganalisa data berdasarkan latar kelakang, tujuan bisnis, dan problem statement. Outputnya adalah memberikan insight dan actionable recommendation dari hasil analisa data kamu. Untuk melakukannya, ikuti langkah-langkah berikut:

1. **Menjabarkan masalah ke dalam key questions**
   - Jabarkan problem statement ke minimal 7 key questions. Pastikan key questions sangat berkaitan dengan latar belakang, tujuan bisnis, dan problem statement yang ingin diselesaikan. Jika diperlukan, tambahkan asumsi dan batasan.
   - Paling tidak ada satu key questions yang nantinya dapat dijawab dengan menggunakan visualisasi data (paling tidak column atau line chart)
   - Selanjutnya, dari masing-masing key questions, tentukan metrik-metrik yang diperlukan. Pastikan metrik tersedia di dalam data.

2. **Data Cleaning**
  - Identifikasi dan lakukan pembersihan data untuk memastikan tidak ada duplikasi, missing value, atau data tidak sesuai yang dapat mempengaruhi analisis.
  - Kamu bisa menggunakan jupyter notebook untuk membantu kamu dalam melakukan data cleaning apabila kamu lebih nyaman dengan Python. Jika menggunakan Google Spreadsheet, mohon jelaskan bagaimana cara melakukan data cleaningnya di slide bagian `Data Cleaning`. (**Kumpulkan juga jupyter notebooknya dengan format data_cleaning_nama.ipynb**)

3. **Pengolahan dan Analisa Data**
   - Jawab key questions dengan pengolahan data dan data visualisasi dengan menggunakan metode dan chart apapun seperti basic formula, conditional, pivot table, vlookup, hlookup, dsb.
   - Poin nomor 3 **hanya dikerjakan di dalam Google Spreadsheet**
  
4. **Membuat Insight dan Actionable Recommendation**
   - Buat insight dari jawaban key questions yang kamu sudah cari. Tampilkan jawaban dan insightnya di slide dengan menyantumkan visualisasi (tabel, chart, dsb) beserta penjelasan insightnya
   - Buat actionable recommendation berdasarkan insight-insight yang kamu dapatkan. Pastikan bahwa actionable recommendation menjawab problem statement dan sesuai dengan tujuan dan konteks bisnis.
---

## Assignment Rubrics

|**Key Component**|**Description**|**Points**|
|---|---|---|
|Problem Understanding|Siswa mampu menjabarkan permasalahan berupa key questions dari problem statement, latar belakang masalah, dan bisnis konteks yang sudah ditentukan |15 pts|
|Data Cleaning|Siswa mampu melakukan seleksi data sesuai kebutuhan, eksplorasi data, menentukan tahapan data cleaning, dan melakukan proses data cleaning sesuai dengan kondisi data |10 pts|
|Spreadsheet|Siswa mampu melakukan pengolahan data dengan menggunakan Google Spreadsheet beserta pembuatan data visualisasinya |21 pts (3 pts each)|
|Insight|Siswa dapat membuat insight dari jawaban key questions yang telah ditentukan secara singkat, jelas, dan padat |21 pts (3 pts each)|
|Actionable Recommendation|Siswa dapat membuat actionable insight berdasarkan insight yang didapatkan dan menentukan batasan dan asumsi yang diperlukan|7 pts|
|Reporting|Siswa dapat membuat laporan yang jelas, runut, dan mudah dipahami|6 pts|

**Total: 80 pts**

### Detail
Poin yang dinilai:
1. Problem Understanding
   - Jumlah key questions minimal 7
   - Kesesuaian key questions dengan konteks bisnis, tujuan bisnis, dan problem statement
   - Metrik ditentukan sesuai dengan key questions
   - Penentuan kolom yang digunakan sesuai dengan metrik masing-masing key questions
2. Data Cleaning
   - Seleksi data berdasarkan kolom-kolom yang dibutuhkan
   - Eksplorasi data
   - Penjelasan kondisi masing-masing kolom dan penentuan tahapan data cleaning
3. Spreadsheet
   - Ketepatan penggunaan metode untuk menyelesaikan masing-masing key questions
   - Jika terdapat paling tidak satu key questions yang dijawab dengan chart/data visualisasi
5. Insight
   - Masing-masing jawaban key questions diberikan insight
   - Insight ditulis dengan singkat, padat, dan jelas. Tidak bertele-tele
7. Actionable Recommendation
   - Actionable recommendation ditulis berdasarkan insight yang ditemukan dari masing-masing key questions
   - Memberikan asumsi dan batasan
   - Sesuai dengan konteks bisnis, tujuan bisnis, dan problem statement
---

## Score Reduction

Jika Student terlambat mengumpulkan dengan waktu yang ditentukan, maka Graded Challenge akan diberi poin nol.

---
