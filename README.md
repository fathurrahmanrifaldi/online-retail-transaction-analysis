# Analisis Penjualan & Dashboard Ritel Online (*Online Retail Sales Analysis & Dashboard*)

Proyek analisis data komprehensif dari hulu ke hilir (*end-to-end*) pada 522 ribu+ transaksi *e-commerce*, mencakup pembersihan data (*data cleaning*), analisis eksploratif (EDA), pembuatan *dashboard* Excel, serta perancangan arsitektur Power BI.

**Demo Langsung / Portofolio:** [Tautan ke portofolio atau dashboard Anda, jika ada]

---

##  Gambaran Umum Proyek (*Project Overview*)

Proyek ini menganalisis data transaksi selama satu tahun (Desember 2010 – Desember 2011) dari peritel hadiah online yang berbasis di Inggris (UK). Dataset ini berisi 541.909 baris data mentah dari 4.334 pelanggan unik yang tersebar di 38 negara.

### Hasil Utama (*Key Deliverables*)
*  **Alur Pembersihan Data (*Data Cleaning Pipeline*):** Validasi dan dokumentasi sistematis (menangani 19,5 ribu anomali).
*  **Buku Kerja Analisis Excel (*Excel Analytics Workbook*):** 9 *sheet* interaktif dengan KPI terverifikasi dan 6 grafik visual.
*  **Panduan Arsitektur Power BI:** Cetak biru lengkap untuk 5 halaman *dashboard* (formula DAX, skema bintang/*star schema*).
*  **Dataset Siap Produksi (*Production-Ready Datasets*):** Ekspor file CSV bersih (lengkap 522 ribu+ baris, bukan sampel).

---

##  Dampak Bisnis (*Business Impact*)

| Metrik | Temuan |
| :--- | :--- |
| **Konsentrasi 20% Pelanggan Teratas** | 20% pelanggan menyumbang 75% dari total pendapatan. |
| **Puncak Musiman (*Seasonal Peak*)** | Pendapatan November naik +45% dibandingkan baseline (musim belanja pra-liburan). |
| **Peluang Geografis** | Pasar Inggris mendominasi (85%), penetrasi pasar Eropa masih <3%. |
| **Biaya Pembatalan (*Cancellation Cost*)** | Pesanan dibatalkan: ~£894 ribu/tahun (1,7% dari GMV). |
| **Total Pendapatan yang Dianalisis** | £10,26 juta dari 19.776 pesanan unik. |

---

##  Pembersihan Data & Metodologi

### Statistik Dataset Mentah
* **Baris awal:** 541.909
* **Baris bersih akhir:** 522.571 (Retensi 96,4%)
* **Baris yang dikecualikan:** 19.338 (3,6%)
  * **Data duplikat identik:** 5.268 (deteksi entri ganda)
  * **Pesanan dibatalkan (awalan "C"):** 9.251 (dipisahkan untuk analisis pembatalan)
  * **Harga satuan nol/negatif:** 2.512 (penyesuaian stok, penghapusan buku/*write-offs*)
  * **Kode stok non-produk:** 2.307 (biaya admin: POST, BANK CHARGES, dll.)

### Aturan Pembersihan Data (Terdokumentasi)
Setiap keputusan penghapusan data memiliki justifikasi yang dapat diaudit:
* **Duplikat** → Dihapus (transaksi palsu/ganda).
* **Pembatalan** → Dipisahkan (tingkat pembatalan 1,7% dianalisis terpisah).
* **Harga ≤ 0** → Dikecualikan (bukan transaksi penjualan riil).
* **Kuantitas Negatif** → Sebagian besar berkorelasi dengan pembatalan; kasus khusus diisolasi untuk ditinjau.
* **Kode Non-Produk** → Dikecualikan (biaya logistik dan admin, bukan pendapatan produk).
* **Penanganan CustomerID Kosong (*Missing*):** 25% transaksi tidak memiliki CustomerID (*guest checkout*).
  * ✅ Tetap dimasukkan dalam analisis pendapatan/produk (transaksi tetap valid).
  * ✅ Dikecualikan dari segmentasi RFM tingkat pelanggan (tidak ada riwayat pelanggan untuk dianalisis).
  * Keputusan ini didokumentasikan pada *sheet* Excel "Ringkasan & Insight".

---

##  Analisis Utama & Temuan

### 1. Konsentrasi Pendapatan (Prinsip Pareto)
* 20% pelanggan teratas (868 dari 4.334) menyumbang 75% dari total pendapatan.
* Hanya butuh 343 pelanggan (7,9%) untuk mencapai ambang batas 80% pendapatan.
* **Implikasi Bisnis:** Strategi retensi untuk segmen bernilai tinggi (*high-value*) memberikan ROI yang jauh lebih signifikan.

### 2. Pola Waktu (*Temporal Patterns*)

| Periode / Waktu | Pola | Implikasi Bisnis |
| :--- | :--- | :--- |
| **Sep–Nov 2011** | +45% vs baseline | Lonjakan pra-liburan; rencanakan inventaris/staf untuk Q4. |
| **Nov 2011 (Puncak)** | Pendapatan £1,45 juta | Bulan dengan penjualan terkuat; periode ideal untuk pengujian kampanye. |
| **Des 2011 (Data)** | Parsial (hanya sampai 9 Des) | **Jangan** dibandingkan langsung (*apple-to-apple*) dengan bulan penuh. |
| **Sabtu** | Nol transaksi | Toko/gudang tutup di akhir pekan; pertimbangkan optimasi jadwal kerja. |
| **10:00–15:00** | Jam sibuk belanja | Waktu paling optimal untuk promosi langsung (*live*) & dukungan *customer service*. |

### 3. Wawasan Geografis

| Negara | % Pendapatan | Potensi / Ukuran Pasar | Tindakan |
| :--- | :--- | :--- | :--- |
| **Inggris Raya (UK)** | 85,2% | Jenuh (Pasar Utama) | Optimasi retensi pelanggan. |
| **Belanda** | 3,0% | Pasar Uni Eropa Besar | Peluang ekspansi. |
| **Irlandia** | 1,8% | Pasar Kecil Berkembang | Uji pasar (*test market*). |
| **Jerman** | 1,6% | Terbesar di Uni Eropa | Penetrasi masih rendah (*underrepresented*). |
| **Prancis** | 1,5% | Pasar Uni Eropa Besar | Target ekspansi strategis. |

* **Rekomendasi:** Alokasikan uji coba anggaran pemasaran Eropa ke Belanda, Jerman, dan Prancis (saat ini penetrasi masih <3% dibandingkan ukuran pasar).

### 4. Wawasan Produk
* 15 produk teratas menghasilkan ~45% dari total pendapatan.
* **Deteksi Pencilan (*Outlier*):** StockCode 23843 ("PAPER CRAFT") melonjak karena satu pesanan grosir masif (80 ribu unit, 1 faktur) — ditandai sebagai anomali B2B, bukan tren ritel umum.
* Terdapat 3.914 SKU unik; strategi produk *long tail* sangat layak diterapkan.

### 5. Dampak Pembatalan Pesanan
* 9.251 pesanan dibatalkan (1,7% dari GMV).
* Potensi pendapatan hilang: ~£894 ribu/tahun.
* **Langkah Aksi:** Jika tingkat pembatalan ditekan hingga 50%, potensi penambahan pendapatan mencapai **+£447 ribu/tahun** tanpa perlu biaya akuisisi pelanggan baru.
* **Tindak Lanjut:** Perlu analisis akar masalah (*root-cause analysis*) bersama tim operasional/CS karena dataset mentah belum memiliki kolom alasan pembatalan.

---
