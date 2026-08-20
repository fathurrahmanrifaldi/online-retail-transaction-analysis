# UK Online Retail: End-to-End Sales Performance & Customer RFM Analysis (Excel-Based)

![Excel](https://img.shields.io/badge/Tools-Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Focus](https://img.shields.io/badge/Analysis-Data%20Cleaning%20%7C%20Pivot%20Tables%20%7C%20RFM%20Analysis-orange?style=for-the-badge)

---

##  1. Ringkasan Proyek (Project Overview)
Proyek ini merupakan studi kasus analisis data penjualan ritel berbasis di Inggris (*UK-based online giftware & household items retailer*) yang mencakup data transaksi periode **1 Desember 2010 hingga 9 Desember 2011**.

Analisis ini sepenuhnya dirancang dan diproses menggunakan **Microsoft Excel** dengan fokus pada:
1. Menghitung dan memodelkan metrik utama performa bisnis (*Key Performance Indicators*).
2. Melakukan audit serta pembersihan data transaksi skala besar (>500.000 baris).
3. Melakukan analisis tren musiman, kontribusi geografis, efisiensi operasional jam belanja, dan segmentasi pelanggan (Prinsip Pareto & Analisis RFM).
4. Menyusun rekomendasi bisnis strategis berdasarkan temuan data.

---

##  2. Metrik Utama Bisnis (Key Performance Indicators)

Berdasarkan dataset transaksi yang telah dibersihkan:
* **Total Pendapatan (Revenue)**: **£10.259.030,24** (~£10,26 Juta)
* **Total Transaksi (Distinct Invoices)**: **19.776 order**
* **Average Order Value (AOV)**: **£518,76** per order
* **Pelanggan Teridentifikasi**: **4.334 Customer Unik** (tidak termasuk transaksi *guest*)
* **Katalog Produk**: **3.914 SKU Unik**
* **Cakupan Pasar**: **38 Negara**
* **Potensi Pendapatan Hilang (Cancelled Orders)**: **£893.979,73** (1,74% dari total order)

---

##  3. Audit & Log Pembersihan Data (Data Cleaning)
Untuk menjaga integritas data sebelum proses analisis, dilakukan serangkaian tahapan pembersihan dan pemisahan data transaksi:

| No | Tahapan Pembersihan | Alasan Metodologis | Baris Terdampak | Baris Tersisa |
|:--:|:--------------------|:-------------------|:---------------:|:-------------:|
| **1** | Hapus duplikasi persis (*Exact Duplicates*) | Mencegah pencatatan ganda (*double-entry*) pada transaksi yang identik | 5.268 | 536.641 |
| **2** | Pemisahan transaksi batal (Invoice prefix `"C"`) | Bukan penjualan riil; diisolasi ke lembar kerja khusus untuk analisis tingkat pembatalan | 9.251 | 527.390 |
| **3** | Filter `UnitPrice <= 0` | Mengeliminasi data *stock adjustment* & *write-off* internal | 2.512 | 524.878 |
| **4** | Filter `Quantity <= 0` | Mengeliminasi transaksi anomali dengan jumlah nol atau negatif | 0 | 524.878 |
| **5** | Filter kode administratif / non-produk | Mengeluarkan kode biaya operasional (`POST`, `DOT`, `BANK CHARGES`, `AMAZONFEE`, dll.) | 2.307 | **522.571** |

> **Catatan Metodologi:**
> * **Transaksi Guest (~25%)**: Transaksi tanpa `CustomerID` tetap disertakan untuk analisis total omzet, tren bulanan, dan produk, namun **dikeluarkan** saat melakukan analisis perilaku pelanggan / segmentasi RFM.
> * **Outlier Transaksi**: Terdeteksi 1 transaksi grosir ekstrem (*wholesale*) pada produk `23843` (80.995 unit dalam satu faktur) yang diidentifikasi terpisah agar tidak mendistorsi pola penjualan ritel umum.

---

##  4. Temuan & Insight Utama

### 1. Pola Musiman Penjualan (Seasonality)
* Terjadi lonjakan penjualan yang sangat signifikan pada kuartal keempat (September–November 2011), mencapai puncak tertingginya di **November 2011 (~£1,45 Juta)** akibat periode belanja Natal.
* *Catatan teknis*: Data Desember 2011 berakhir pada tanggal 9 (bukan satu bulan penuh), sehingga penurunan nominal di bulan tersebut bukan mencerminkan kemunduran performa bisnis.

### 2. Konsentrasi Pasar (Geografis)
* **United Kingdom** mendominasi **85,16% dari total pendapatan**.
* Pasar internasional dipimpin oleh **Belanda (Netherlands)** (£283k) dan **Irlandia (EIRE)**, yang menunjukkan adanya potensi pasar grosir/B2B lintas batas di kawasan Eropa.

### 3. Distribusi Pelanggan & Prinsip Pareto (80/20 Rule)
* **20% pelanggan teratas (866 orang)** menyumbang **74,6% dari total pendapatan**.
* Sebanyak **26,1% pelanggan (1.133 orang)** sudah menghasilkan **80% total revenue**. Ini menunjukkan perputaran bisnis sangat terkonsentrasi pada segmen pembeli bervolume tinggi.

### 4. Waktu Operasional & Pola Belanja
* Jam belanja paling aktif berada pada rentang **10:00 – 15:00** (puncak transaksi terjadi pada pukul 12:00 siang).
* **Tidak ada transaksi pada hari Sabtu**, yang mengindikasikan operasional gudang/pemrosesan pesanan libur pada akhir pekan.

---

##  5. Rekomendasi Bisnis Strategis

1. **Retensi & Program Loyalitas Khusus Top Customer:**  
   Fokuskan anggaran retensi pemasaran untuk **Top ~20% Pelanggan** (berdasarkan analisis RFM). Pemberian insentif harga grosir, *dedicated account support*, atau program loyalitas eksklusif akan berdampak jauh lebih besar pada pendapatan dibanding akuisisi pelanggan secara acak.
2. **Kesiapan Rantai Pasok Menjelang Natal:**  
   Siapkan kapasitas inventaris dan staf gudang sebelum bulan September. Pertimbangkan kampanye *pre-order* atau *early-bird* di bulan Agustus untuk meratakan beban operasional pada puncak belanja akhir tahun.
3. **Konversi Pelanggan Guest Menjadi Akun Terdaftar:**  
   Dorong 25% pembeli *guest* untuk mendaftar akun dengan insentif kupon belanja pertama. Hal ini penting agar riwayat pembelian mereka dapat dilacak untuk analisis personalisasi di masa depan.
4. **Mitigasi Kerugian Pesanan Batal:**  
   Lakukan investigasi operasional terkait pesanan batal yang mencapai nilai potensi **~£894rb (1,7% total order)** guna mengidentifikasi apakah penyebabnya terkait kehabisan stok, kendala pembayaran, atau faktor lainnya.

---

##  6. Struktur Workbook Excel

File `Analisis_Online_Retail.xlsx` disusun secara modular dengan struktur lembar kerja (*sheets*) berikut:
* `Ringkasan & Insight` : Ringkasan KPI eksekutif, metodologi, dan rekomendasi bisnis.
* `Log_Pembersihan_Data`: Dokumentasi audit tahapan pembersihan data langkah demi langkah.
* `Pivot_Bulanan`       : Analisis agregasi tren pendapatan, volume order, dan AOV per bulan.
* `Pivot_Negara`        : Distribusi pendapatan dan pangsa pasar geografis.
* `Pivot_Produk`        : Pemetaan peringkat 15 produk terlaris berdasarkan revenue & volume.
* `Pivot_Customer`      : Tabel segmentasi pelanggan menggunakan metrik *Recency, Frequency, Monetary* (RFM).
* `Pola_Waktu`          : Distribusi transaksi berdasarkan jam belanja dan hari operasional.
* `Data_Cleaned (Sample)`: Sampel data transaksi bersih untuk keperluan pengecekan/audit.
* `Data_Cancelled`      : Kumpulan data transaksi batal untuk analisis tingkat pembatalan.

---
*Dianalisis dan disusun oleh: **Fathur Rahman Rifaldi** — https://www.linkedin.com/in/fathurrahmanrifaldi/*
