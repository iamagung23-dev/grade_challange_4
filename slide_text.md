# Panduan Analisis - Graded Challenge 4
## Portugal Real Estate 2024

> Dokumen ini berisi seluruh isi yang siap di-copy ke Google Slide. Setiap section sudah dipetakan ke slide yang sesuai dengan outline GC4.

---

## SLIDE 1 - Judul

**Analisis Pasar Properti Portugal 2024: Strategi Meningkatkan Penjualan 10% dalam 6 Bulan**

- Nama: [Nama Anda]
- Batch: CODA-RMT-001
- Hacktiv8 Comprehensive Data Analytics Program

---

## SLIDE 2 - Latar Belakang, Tujuan Bisnis, & Problem Statement

**Latar Belakang**
Kota-kota di Portugal mengalami perkembangan pesat dalam sektor perumahan. Sebagai analis di perusahaan real estate, tugas saya adalah mengidentifikasi peluang, tantangan, dan rekomendasi strategis untuk meningkatkan profitabilitas perusahaan.

**Tujuan Bisnis**
Meningkatkan penjualan properti dengan harga sesuai target pasar serta memahami faktor-faktor yang paling memengaruhi harga jual di berbagai kota di Portugal.

**Problem Statement**
Bagaimana cara meningkatkan penjualan properti di Portugal sebesar 10% dalam 6 bulan dengan menganalisis tren pasar dan memahami variabel kunci yang mempengaruhi harga jual properti?

---

## SLIDE 3 - Penjabaran Masalah (Key Questions)

Problem statement dijabarkan menjadi 7 key questions:

1. **KQ1**: Distrik mana yang memiliki harga properti rata-rata tertinggi & terendah di Portugal?
2. **KQ2**: Distrik mana yang paling mahal berdasarkan harga per meter persegi (PricePerSqm)?
3. **KQ3**: Tipe properti apa yang paling banyak dijual dan bagaimana distribusi harganya? *(dijawab dengan column chart)*
4. **KQ4**: Bagaimana pengaruh jumlah kamar tidur terhadap harga properti?
5. **KQ5**: Apakah sertifikat efisiensi energi (EnergyCertificate) mempengaruhi harga jual?
6. **KQ6**: Bagaimana pengaruh umur bangunan terhadap harga properti?
7. **KQ7**: Seberapa besar pengaruh fasilitas (parkir & lift) terhadap harga properti?

**Asumsi & Batasan:**
- Data yang digunakan adalah harga listing (asking price), bukan harga transaksi final.
- Analisis hanya pada properti dengan harga 10.000–50.000.000 EUR (rentang wajar pasar).
- Properti dengan luas 0 atau >10.000 m² dianggap input error.

---

## SLIDE 4 - Penjelasan Dataset & Data Cleaning

**Sumber Data**: Kaggle - Portugal Real Estate 2024 (135.536 baris × 25 kolom)

**Kolom yang Digunakan (13 kolom):**

| Kolom | Tipe | Untuk Key Question |
|---|---|---|
| Price | numerik | Semua KQ |
| District, City | kategorik | KQ1, KQ2 |
| Type | kategorik | KQ3 |
| TotalArea, LivingArea | numerik | KQ2 |
| NumberOfBedrooms, NumberOfBathrooms, NumberOfWC | numerik | KQ4 |
| ConstructionYear | numerik | KQ6 |
| EnergyCertificate | kategorik | KQ5 |
| HasParking, Elevator | boolean | KQ7 |

**Kondisi Data Awal:**
- Banyak missing value (BuiltArea 80%, ConservationStatus 86%, GrossArea 80%)
- Ada 8.913 baris duplikat
- Harga ekstrim: minimum 1 EUR, maksimum 1,38 miliar EUR (outlier)
- Kolom Type, EnergyCertificate punya sedikit NaN

**Tahapan Data Cleaning:**
1. Seleksi 13 kolom relevan, drop kolom missing >70%
2. Hapus 8.913 baris duplikat
3. Hapus baris Price = NaN, filter Price ke rentang 10rb–50jt EUR
4. Hapus 16 baris Type = NaN
5. Imputasi median per Type untuk kolom numerik (TotalArea, jumlah kamar, dll)
6. Isi 'Unknown' untuk EnergyCertificate yang missing
7. Filter outlier TotalArea (0 < area ≤ 10.000 m²)
8. Buat kolom turunan: **PricePerSqm** & **PropertyAge**

**Hasil**: 135.536 → **112.800 baris bersih** siap analisis.

---

## SLIDE 5 - KQ1: Harga Rata-Rata per Distrik

**Metode Spreadsheet**: Pivot Table (Rows: District, Values: AVERAGE of Price)

**Top 5 Distrik Termahal:**
| Rank | District | Avg Price (EUR) |
|---|---|---|
| 1 | Lisboa | 569.862 |
| 2 | Faro | 530.511 |
| 3 | Setúbal | 397.947 |
| 4 | Porto | 339.912 |
| 5 | Évora | 302.588 |

**Distrik Termurah**: Guarda, Castelo Branco, Bragança (rata-rata <100rb EUR)

**Insight**: Pasar properti Portugal sangat terkonsentrasi di Lisboa (ibukota) dan Faro (kawasan turis Algarve). Selisih harga distrik termahal vs termurah bisa mencapai **6x lipat**. Ini menunjukkan pasar yang tersegmentasi jelas berdasarkan lokasi geografis.

---

## SLIDE 6 - KQ2: Distrik Termahal per Meter Persegi

**Metode Spreadsheet**: Pivot Table (Rows: District, Values: AVERAGE of PricePerSqm)

**Top 5 Distrik dengan PricePerSqm Tertinggi:**
| Rank | District | PricePerSqm (EUR/m²) |
|---|---|---|
| 1 | Lisboa | 3.815,85 |
| 2 | Évora | 3.733,42 |
| 3 | Faro | 2.863,11 |
| 4 | Setúbal | 2.462,15 |
| 5 | Porto | 2.187,79 |

**Insight**: Lisboa & Évora menjadi distrik premium dengan harga per m² >3.700 EUR. Évora menarik karena bukan kota terbesar tapi PricePerSqm tinggi (kemungkinan UNESCO heritage city → properti langka & terbatas). PricePerSqm adalah metrik yang lebih adil untuk membandingkan nilai antar distrik karena menghilangkan bias ukuran properti.

---

## SLIDE 7 - KQ3: Distribusi Tipe Properti (DENGAN CHART)

**Metode Spreadsheet**: Pivot Table + **Column Chart**

**Distribusi Tipe Properti (Top 6):**
| Tipe | Jumlah Listing | % |
|---|---|---|
| Apartment | 40.023 | 35,5% |
| House | 33.140 | 29,4% |
| Land | 23.497 | 20,8% |
| Store | 4.934 | 4,4% |
| Building | 2.356 | 2,1% |
| Farm | 2.313 | 2,0% |

**→ Buat Column Chart di Google Spreadsheet untuk visualisasi ini**

**Avg Price per Tipe (Top 5):**
- Mansion: 3.044.185 EUR
- Estate: 2.840.385 EUR
- Hotel: 2.373.946 EUR
- Apartment: 373.853 EUR
- House: 408.759 EUR

**Insight**: 85% pasar didominasi 3 tipe: Apartment, House, dan Land. Apartment menjadi tipe paling likuid (volume tertinggi) dengan harga rata-rata moderate (~374rb EUR). Properti premium (Mansion, Estate) volumenya kecil tapi nilai per unit tinggi → strategi penjualan harus berbeda untuk dua segmen ini.

---

## SLIDE 8 - KQ4: Jumlah Kamar Tidur vs Harga

**Metode Spreadsheet**: Pivot Table (Rows: NumberOfBedrooms, Values: AVERAGE Price)

| Jumlah Kamar | Avg Price (EUR) |
|---|---|
| 1 kamar | 287.380 |
| 2 kamar | 333.256 |
| 3 kamar | 397.215 |
| 4 kamar | 624.975 |
| 5 kamar | 845.276 |
| 6 kamar | 907.074 |

**Insight**: Setiap penambahan 1 kamar tidur menaikkan harga rata-rata signifikan, dengan **lonjakan terbesar dari 3 → 4 kamar (+57%)**. Ini menandakan properti dengan 4+ kamar masuk segmen premium (target keluarga besar / investor). Tipe 2–3 kamar adalah "sweet spot" volume tertinggi yang cocok untuk first-time buyer.

---

## SLIDE 9 - KQ5: Energy Certificate vs Harga

**Metode Spreadsheet**: Pivot Table (Rows: EnergyCertificate, Values: AVERAGE Price)

| Sertifikat Energi | Avg Price (EUR) |
|---|---|
| A (paling efisien) | 641.514 |
| B | 607.251 |
| A+ | 586.108 |
| C | 405.558 |
| D | 369.572 |
| E | 318.382 |
| F | 262.055 |
| G (paling boros) | 300.221 |

**Insight**: Ada **korelasi kuat antara efisiensi energi & harga**. Properti bersertifikat A/B harganya rata-rata **2x lebih mahal** dari sertifikat E/F. Pembeli Portugal modern semakin sadar biaya energi → sertifikat hijau jadi value proposition penting untuk pricing premium.

---

## SLIDE 10 - KQ6: Umur Bangunan vs Harga

**Metode Spreadsheet**: Buat kolom kategori umur dengan IF, lalu Pivot Table

| Kategori Umur | Avg Price (EUR) |
|---|---|
| Baru (0–10 thn) | 575.734 |
| Muda (11–30 thn) | 389.916 |
| Tua (31–50 thn) | 261.620 |
| Sangat Tua (>50 thn) | 315.695 |

**Insight**: Properti baru (0–10 tahun) bernilai **~2x lipat** properti tua (31–50 tahun). Menariknya, properti "sangat tua" (>50 thn) justru lebih mahal dari "tua" — kemungkinan karena banyak properti heritage di pusat kota Lisboa/Porto yang punya nilai historis. Properti usia 31–50 tahun adalah segmen termurah → peluang renovasi & flipping.

---

## SLIDE 11 - KQ7: Fasilitas (Parkir & Lift) vs Harga

**Metode Spreadsheet**: AVERAGEIF / Pivot Table dengan filter HasParking & Elevator

| Fasilitas | Ada | Tidak Ada | Selisih |
|---|---|---|---|
| Parkir | 466.343 EUR | 222.731 EUR | **+109%** |
| Lift | 466.515 EUR | 315.656 EUR | **+48%** |

**Insight**: Properti dengan parkir harganya **2x lipat** properti tanpa parkir. Ini fasilitas dengan dampak harga paling besar. Lift menambah nilai ~48% — relevan terutama untuk apartemen di gedung tinggi. Kedua fasilitas ini high-ROI feature yang harus jadi prioritas saat seleksi listing.

---

## SLIDE 12 - Kesimpulan & Actionable Recommendation

### Kesimpulan Utama
Pasar properti Portugal sangat **tersegmentasi**: secara geografis (Lisboa-Porto-Faro premium vs interior), tipe (Apartment-House dominan), dan kualitas (energi & fasilitas).

### Actionable Recommendations untuk Mencapai Target +10% Penjualan dalam 6 Bulan

**1. Fokus pada Sweet Spot Pasar (Volume Strategy)**
- Prioritaskan listing **Apartment & House 2–3 kamar** di harga 200rb–390rb EUR (range Q1–Q3 pasar).
- Segmen ini punya volume terbesar & permintaan paling stabil.

**2. Strategi Geografis Dua Jalur**
- **Premium**: Lisboa & Faro → target buyer high-end & investor asing. Margin tinggi per transaksi.
- **Volume**: Setúbal, Porto, Braga → target first-time buyer lokal. Volume transaksi tinggi.

**3. Push "Green Premium" Listing**
- Properti dengan sertifikat **A/B** terbukti dijual ~2x lebih mahal. Lakukan upgrade sertifikat (renovasi insulasi, panel surya) pada listing yang masih C/D sebelum dipasarkan.

**4. Prioritaskan Listing dengan Fasilitas**
- Saat seleksi inventaris, prioritaskan properti dengan **parkir & lift** (impact +109% dan +48%). Jika tidak ada, pertimbangkan investasi penambahan parkir untuk properti di area padat.

**5. Manfaatkan Properti Tua (31–50 thn) untuk Flipping**
- Beli properti usia 31–50 tahun di harga rendah, renovasi (terutama upgrade energi & tambah fasilitas), jual sebagai properti "modern-classic". Margin renovasi 30–50% sangat feasible.

**6. Target Segmen 4+ Kamar untuk High-Ticket Sales**
- Lonjakan harga 3→4 kamar (+57%) menunjukkan demand premium untuk keluarga besar / investor. Sediakan tim sales khusus segmen ini untuk personalized service.

### Asumsi & Batasan Recommendation
- Asumsi: tren pasar relatif stabil 6 bulan ke depan (tidak ada krisis ekonomi besar).
- Batasan: dataset adalah harga listing, bukan harga transaksi → recommendation harus divalidasi dengan data penjualan aktual.
- Asumsi: perusahaan punya kapasitas operasional untuk eksekusi multi-strategi (premium + volume secara paralel).

---

## CATATAN TEKNIS UNTUK GOOGLE SPREADSHEET

**Formula Penting yang Digunakan:**
- `=AVERAGEIF(District, "Lisboa", Price)` — rata-rata per kondisi
- `=COUNTIF(Type, "Apartment")` — hitung distribusi
- Pivot Table — untuk semua agregasi (Insert > Pivot Table)
- `=IF(PropertyAge<=10, "Baru", IF(PropertyAge<=30, "Muda", IF(PropertyAge<=50, "Tua", "Sangat Tua")))` — kategori umur
- Chart: Insert > Chart > Column Chart untuk KQ3

**Total Score yang Ditargetkan: 80/80 pts**
