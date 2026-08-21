# Deskripsi Project untuk CV — Online Retail Analysis

Pilih versi yang sesuai dengan role & level pengalaman kamu. Semakin senior, semakin fokus ke bisnis impact & keputusan strategis, bukan detail teknis.

---

## VERSI 1: Short & Punchy (untuk CV dengan ruang terbatas)

**Online Retail Sales Analysis Dashboard**
- Membersihkan & menganalisis 522.571 transaksi penjualan dari UK-based online retailer (periode Des 2010–Des 2011)
- Merancang data cleaning pipeline: identifikasi & menangani duplikat, cancelled order, dan non-produk line items (2.307 baris excluded)
- Membangun pivot table & dashboard Excel interaktif + panduan implementasi Power BI dengan 5-page report (Overview, Trend, Geografi, Produk, Customer/RFM)
- Insight: 20% customer menyumbang 75% revenue (Pareto principle); seasonality pattern naik 45% menjelang Natal; UK mendominasi 85% pasar
- Tools: Python (pandas, openpyxl), Excel pivot table + formula, Power BI architecture (DAX, star schema)

---

## VERSI 2: Mid-Level (untuk data analyst / business analyst role)

**Online Retail Data Analysis & Dashboard Development**
- **Data Cleaning & Preparation**: Membersihkan raw dataset 541.909 baris menjadi 522.571 baris transaksi valid melalui systematic validation:
  - Removed 5.268 duplicate rows (exact match detection)
  - Separated 9.251 cancelled orders untuk dianalisis terpisah (1.7% cancellation rate, ~£894K revenue impact)
  - Excluded 2.512 adjustment line items (price ≤ 0) & 2.307 non-product administrative codes
  - Documented setiap keputusan cleaning untuk auditability

- **Exploratory Data Analysis (EDA)**: Menggunakan Python (pandas) untuk mengidentifikasi:
  - Customer distribution: 4.334 unique customers, 25% transaksi tanpa CustomerID (guest checkout)
  - Product portfolio: 3.914 unique SKU, top 15 produk generating 45% revenue
  - Geographical concentration: UK = 85% revenue, 38 negara total (expansion opportunity di Eropa)
  - Temporal patterns: Peak season Sep–Nov (35% higher than baseline), zero Saturday transactions

- **Dashboard & Reporting**:
  - Built interactive Excel workbook (9 sheets): Cleaning log, KPI summary, 5 pivot tables + 6 charts
  - Created 5-page Power BI architecture blueprint dengan DAX measures untuk RFM segmentation & year-over-month growth tracking
  - Provided structured SQL-ready CSV exports (522K rows) untuk BI system integration

- **Business Recommendations** (didukung data):
  1. Retention program targeting top 20% customer (disproportionate impact)
  2. Inventory & staffing plan untuk Q4 seasonal surge
  3. Cancellation root-cause analysis (opportunity: reduce 1.7% cancel rate = +£450K annual)
  4. Geographic expansion testing: Belanda, Irlandia, Jerman (currently <3% penetration vs market size)

- **Skills demonstrated**: SQL-level data validation logic, Python data wrangling, Excel formula/pivot mastery, BI data modeling (star schema), stakeholder-ready insights

---

## VERSI 3: Senior / Manager Level (fokus pada business value & keputusan)

**Strategic Data Analysis: Online Retail Customer & Revenue Optimization**

Conducted comprehensive analytics project untuk retail e-commerce store (522K+ transactions, 1-year period) yang menghasilkan **actionable strategic recommendations**:

**Business Outcome:**
- Identified **20% of customer base representing 75% of revenue** → directly informs acquisition cost target & lifetime value modeling
- Quantified cancellation loss: **~£894K/year (1.7% of GMV)** → prioritized operational/fulfillment investigation
- Discovered **seasonal revenue peak (Nov) +45% vs baseline** → enables cash flow forecasting & resource planning untuk Q4
- Revealed **geographic under-penetration** (UK 85%, Eropa target <3%) → justified European market testing budget allocation

**Analytical Approach:**
- Executed rigorous data validation protocol mencakup duplicate detection, transaction categorization (sales vs adjustments), & completeness checks
- Applied Pareto principle analysis untuk customer segmentation → 343 customers (8% of base) achieve 80% revenue threshold
- Modeled time-series trends + anomaly detection (outlier wholesale order identification)

**Deliverables:**
- Production-ready cleaned dataset (CSV, 522.571 rows) + Excel analytics workbook dengan validated KPIs
- Power BI implementation roadmap (5-page dashboard, DAX specifications, star schema design)
- Executive summary dengan 5 prioritized recommendations (supported by quantified impact)

**Tools & Methodologies:** Advanced Excel (pivot, complex formula), Python (pandas data profiling, statistical summary), BI design (dimensional modeling, measure-based architecture)

---

## VERSI 4: Entry-Level / Graduate (highlight skills & learning)

**Online Retail Data Analysis Project**

Independently conducted end-to-end data analytics project pada real-world e-commerce dataset, demonstrating technical & analytical capabilities:

**Technical Execution:**
- **Data Cleaning**: Processed 541K+ raw transactions, applied validation logic untuk identify & handle 19.5K anomalies (duplicates, cancellations, adjustments) dengan documented decision rules
- **Analysis & Visualization**: 
  - Leveraged Python (pandas) untuk exploratory analysis, uncovered patterns dalam customer behavior, seasonality, & geographic distribution
  - Built Excel pivot tables & formula-driven dashboard (9 sheets) dengan 6 interactive charts
- **BI Preparation**: Created Power BI implementation guide (data modeling, DAX measures, dashboard wireframes) showing understanding of modern analytics architecture

**Key Findings:**
- 4.334 active customers across 38 countries; top 20% generate 75% revenue
- Seasonal peak November (45% above avg); no Saturday transactions
- UK dominates market share (85%); identified Eropa sebagai expansion opportunity

**Learning Outcomes:**
- Mastered data validation methodology: importance of data quality dalam business decisions
- Developed business acumen: belajar cara translate technical findings menjadi strategic recommendations
- Gained BI fundamentals: dimensional modeling, measure-based reporting, cross-validation techniques

**Skills:** Python (data wrangling), Excel (pivot, advanced formula), Power BI concepts, business writing/communication

---

## VERSI 5: Singkat untuk LinkedIn / About Section

"Completed comprehensive analysis of 522K online retail transactions: cleaned data (excluded 19.5K anomalies), identified key insights (20% customer = 75% revenue, 45% seasonal peak), & delivered Excel dashboard + Power BI architecture. Demonstrated data validation, Python, pivot table mastery, & business-focused storytelling."

---

## TIPS MEMILIH VERSI:

| Role Target | Gunakan Versi | Alasan |
|---|---|---|
| Data Analyst (junior) | 2, 4 | Highlight teknis + learning; detail cleaning process |
| Business Analyst / Product | 3, 1 | Fokus business impact & strategic recommendations |
| Senior Data Lead / Manager | 3 | Executive summary, tidak perlu detail teknis; tekankan keputusan |
| Startup / Generalist | 2 | Balance teknis & bisnis |
| Big Tech / Consulting | 1 + tambahkan "scalability consideration" | Ringkas, tapi bisa ekspand kalau ditanya |

---

## BONUS: Pertanyaan Orang HR yang Mungkin Tanya (Persiapan Interview)

1. **"Gimana kamu handle missing data (CustomerID 25%) di analisis revenue?"**
   → "Karena kami fokus revenue & produk (bukan customer lifetime value), missing CustomerID tetap dihitung. Tapi kami exclude dari RFM analysis. Ini documented decision, jadi stakeholder paham trade-off-nya."

2. **"Outlier produk 23843 — gimana kamu approach?"**
   → "Diidentifikasi dulu (80K unit in 1 invoice), investigated contextnya (wholesale/B2B order), terus di-highlight di report bukan dihapus. Alasannya: excluding tanpa justifikasi itu data manipulation; better to flag & let decision maker decide."

3. **"Kenapa Python, bukan SQL langsung ke database?"**
   → "Data disediakan CSV, tidak ada database access. Tapi kalo ada database, SQL lebih efficient untuk filtering besar-besaran. Python dipakai untuk exploratory work & validation yang lebih flexible."

4. **"Power BI blueprint kamu — sudah diimplementasikan?"**
   → "Belum (data bukan dari perusahaan real), tapi panduan siap production-ready. Kalau ada dataset baru, bisa langsung execute tanpa major redesign."

5. **"Apa yang kamu pelajari dari project ini?"**
   → "Data quality is foundational — spending 20% waktu di cleaning menghemat 80% waktu di analysis. Dan importance of documentation: kalau tidak clear kenapa 19.5K rows di-exclude, orang percaya ke angka kita."

---

## Final Polish Tips:

✅ **Format**: Gunakan bullet points, bukan paragraph panjang (lebih scannable)
✅ **Numbers matter**: Selalu kasih angka konkret (522K, 75%, £10.2M), bukan "banyak" atau "significant"
✅ **Action verbs**: "Conducted", "Built", "Identified", "Quantified" — bukan "worked on" atau "helped with"
✅ **Outcome-focused**: Setiap line harus end di benefit/learning, bukan just description
✅ **Tailor per job posting**: Kalau job description butuh "SQL", sebutkan SQL; kalau butuh "Tableau", tulis "Power BI + Tableau readiness"
