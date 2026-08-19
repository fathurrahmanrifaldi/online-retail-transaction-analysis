# 📊 UK Online Retail: End-to-End Sales Performance & Customer RFM Analysis

![Excel](https://img.shields.io/badge/Tools-Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Python](https://img.shields.io/badge/Tools-Python%20(Pandas)-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Focus](https://img.shields.io/badge/Analysis-EDA%20%7C%20RFM%20%7C%20Business%20Insights-orange?style=for-the-badge)

---

## 📌 1. Project Overview
Proyek ini menganalisis dataset transaksi ritel daring multinasional (*UK-based online giftware & household items retailer*) yang mencakup periode transaksi dari **1 Desember 2010 hingga 9 Desember 2011**. 

Tujuan utama analisis ini adalah:
1. Menilai performa bisnis melalui metrik penjualan utama (KPI).
2. Melakukan audit dan pembersihan data skala besar (>540.000 baris).
3. Mengidentifikasi tren musiman, konsentrasi geografis, dan perilaku pembelian pelanggan.
4. Menyusun rekomendasi bisnis berbasis data yang dapat dieksekusi secara nyata.

---

## 🔑 2. Key Performance Indicators (KPI Utama)

Setelah pembersihan data dari transaksi tidak valid dan pembatalan:
* **Total Revenue**: **£10.259.030,24** (~£10,26 Juta)
* **Total Transaksi (Distinct Invoices)**: **19.776 order**
* **Average Order Value (AOV)**: **£518,76** per order
* **Pelanggan Teridentifikasi**: **4.334 Customer Unik**
* **Katalog Produk**: **3.914 SKU Unik**
* **Cakupan Pasar**: **38 Negara**
* **Potensi Pendapatan Hilang (Cancelled Orders)**: **£893.979,73** (1,74% dari total order)

---

## 🛠️ 3. Data Cleaning & Integrity Log
Pembersihan data dilakukan secara ketat menggunakan Python terhadap dataset mentah berukuran **541.909 baris** untuk memastikan integritas analisis:

| No | Tahapan Pembersihan | Alasan Metodologis | Baris Terdampak | Baris Tersisa |
|:--:|:--------------------|:-------------------|:---------------:|:-------------:|
| **1** | Hapus duplikasi persis (*Exact Duplicates*) | Mencegah *double-entry* pada transaksi identik | 5.268 | 536.641 |
| **2** | Pemisahan transaksi batal (Invoice prefix `"C"`) | Bukan penjualan riil; dianalisis terpisah pada sheet *Data Cancelled* | 9.251 | 527.390 |
| **3** | Filter `UnitPrice <= 0` | Mengeliminasi data *stock adjustment* & *write-off* internal | 2.512 | 524.878 |
| **4** | Filter `Quantity <= 0` | Mengeliminasi anomali kuantitas non-penjualan | 0 | 524.878 |
| **5** | Filter kode administratif/non-produk | Mengeluarkan kode `POST`, `DOT`, `BANK CHARGES`, `AMAZONFEE`, dll. | 2.307 | **522.571** |

> **Catatan Penanganan Missing Data & Outlier:**
> * Sebanyak ~25% baris tidak memiliki `CustomerID` (transaksi *guest*). Data ini tetap dipertahankan untuk analisis total revenue dan produk, namun **dieksklusi secara ketat** saat segmentasi pelanggan (RFM).
> * Ditemukan 1 transaksi *wholesale/outlier* ekstrem pada produk `23843` (80.995 unit dalam satu faktur) yang diisolasi agar tidak mendistorsi pola penjualan ritel umum.

---

## 📈 4. Key Business Insights

### 1. Pola Musiman Penjualan (Seasonality Trend)
* Terjadi lonjakan pendapatan yang signifikan pada kuartal keempat (Sep–Nov 2011), mencapai puncaknya di **November 2011 (~£1,45 Juta)** yang didorong oleh *Christmas holiday shopping*.
* *Catatan teknis*: Data Desember 2011 hanya mencakup hingga tanggal 9 (bukan bulan penuh), sehingga penurunan angka di bulan tersebut adalah artefak batas cutoff data, bukan penurunan kinerja riil.

### 2. Konsentrasi Pasar (Geographic Distribution)
* **United Kingdom** menyumbang **85,16% dari total pendapatan**.
* Pasar internasional dipimpin oleh **Belanda (Netherlands)** (£283k) dan **Irlandia (EIRE)**, yang menunjukkan adanya potensi pasar B2B/grosir lintas batas yang belum dimonetisasi optimal.

### 3. Distribusi Pelanggan & Prinsip Pareto (80/20 Rule)
* **20% pelanggan teratas (866 pelanggan)** menghasilkan **74,6% total pendapatan**.
* Sebanyak **26,1% pelanggan (1.133 orang)** sudah menguasai **80% total revenue**. Bisnis sangat bergantung pada segmen pembeli volume tinggi.

### 4. Pola Operasional & Waktu Transaksi
* Transaksi paling padat terjadi pada rentang waktu **10:00 – 15:00**, dengan puncak di pukul 12:00.
* **Nol transaksi di hari Sabtu**, mencerminkan jadwal operasional pemrosesan gudang/sistem logistik yang libur pada akhir pekan.

---

## 💡 5. Strategic Business Recommendations

1. **Prioritas Program Retensi & VIP Tiering:**  
   Alokasikan anggaran retensi pemasaran khusus untuk **Top 20% Pelanggan** (berbasis RFM). Menyediakan akun representatif khusus, diskon volume grosir, atau *priority dispatch* akan jauh lebih efisien dalam mempertahankan revenue dibandingkan akuisisi massal.
2. **Kesiapan Rantai Pasok & Smoothing Kampanye Musiman:**  
   Siapkan alokasi inventaris dan kapasitas gudang ekstra sebelum September. Luncurkan kampanye *early-bird / pre-order* pada bulan Agustus untuk meratakan beban operasional lonjakan Natal.
3. **Konversi Transaksi Guest ke Akun Terdaftar:**  
   Buat insentif pendaftaran (misal: *first-purchase voucher* atau *tracking order*) untuk 25% transaksi *guest* agar data perilaku mereka dapat dipersonalisasi dan dimasukkan ke dalam funnel retensi.
4. **Mitigasi Kerugian Akibat Pembatalan Order:**  
   Investigasi akar masalah pesanan yang dibatalkan bernilai **~£894rb (1,7% order)**. Integrasi data alasan pembatalan (misal: stok kosong atau isu sistem checkout) berpotensi menyelamatkan pendapatan secara langsung.

---

## 📂 6. Repository Structure
```plaintext
├── Analisis_Online_Retail.xlsx      # File Excel utama (Cleaned sample, Pivots, Log, & Insights)
├── README.md                        # Dokumentasi dan ringkasan studi kasus proyek
