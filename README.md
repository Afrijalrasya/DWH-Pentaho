# 🏪 ETL Superstore Project (Pentaho Kettle)

ETL pipeline ini dibuat untuk memproses data Superstore (CSV/Excel) menggunakan **Pentaho Data Integration (PDI / Kettle)**. Proyek ini mengimplementasikan **Medallion Architecture** (Bronze, Silver, Gold) untuk memastikan data diolah secara bertahap — dari mentah hingga siap dianalisis.

---

## 🧱 Arsitektur yang Digunakan: Medallion Architecture

+-------------+ +--------------+ +---------------+

| Sources | --> | Bronze Layer | --> | Silver Layer | --> | Gold Layer  | --> | BI Tools

| (CSV Files) | | (Raw Staging)|     |   (Dimensi)  |     |(Fact Table) |     | Power BI

+-------------+ +--------------+ +---------------+


---

## 📂 Struktur Direktori
      📁 ETL-Superstore/
      │
      ├── 📁 data_source/                
      │   └── Superstore+Sales.csv
      │
      ├── 📁 docs/                      ← Dokumentasi & diagram visual
      │   ├── dashboard.png
      │   ├── process_detail.png
      │
      ├── 📁 kettle/                    ← Seluruh file Kettle ETL
      │   ├── 📁 stages/                ← Bronze Layer (staging)
      │   │   ├── customer_stg.ktr
      │   │   ├── product_stg.ktr
      │   │   ├── order_stg.ktr
      │   │   └── values_stg.ktr
      │   │
      │   ├── 📁 dimension/             ← Silver Layer (dimensi)
      │   │   ├── customers_dim.ktr
      │   │   ├── products_dim.ktr
      │   │   ├── orders_dim.ktr
      │   │   └── dim_date.ktr
      │   │
      │   ├── 📁 fact/                  ← Gold Layer (fact)
      │   │   ├── pre_fact.ktr
      │   │   ├── fact_table.ktr
      │   │
      │   └── 📁 job/                   ← Master ETL job
      │       └── ETL-superstore.kjb
      │
      ├── 📁 visualization/            ← Dashboard files (Tableau / Power BI / CDE)
      │   ├── dw sales visualisation.pbix
      │
      └── 📄 README.md                 ← Dokumentasi utama proyek



---

## 🔁 Proses ETL

### 🟫 Bronze Layer – Staging (Raw Data)
- **Transformasi:** ORDER_STG, PRODUCTS_STG, CUSTOMERS_STG, VALUES_STG
- **Tujuan:** Menyimpan data mentah (as-is) dari CSV (Superstore+Sales.csv)
- **Proses:** Full Load, basic cleaning, truncate & insert

### 🪙 Silver Layer – Dimensi (Cleaned & Standardized)
- **Transformasi:** ORDERS_DIM, PRODUCTS_DIM, CUSTOMERS_DIM, DIM_Date
- **Tujuan:** Menyusun data dimensi terstandarisasi dengan surrogate key
- **Proses:** Lookup referensi dari VALUES_STG, validasi, enrichment

### 🟨 Gold Layer – Fact Table (Business-Ready Data)
- **Transformasi:** PRE_FACT, FACT_TABLE
- **Tujuan:** Buat fact table siap digunakan untuk analitik
- **Proses:** Join antar dimensi, hitung metrik (`Sales`, `Profit`), dan clear cache OLAP

---

## 📊 Output

- `fact_sales` dengan metrik siap analisis
- Struktur Star Schema
- Terintegrasi dengan cache OLAP (Mondrian, CDA)
- Siap untuk dipakai oleh tools seperti:
  - Tableau
  - Power BI

---

## 📦 Dataset yang Digunakan

- Superstore Sales (Orders.csv)
- Format: Excel/CSV
- Kolom utama:
  - Row ID, Order Date, Product, Customer, Sales, Profit, Customer Segment, Region, Ship Date, dsb.

---

## 🧠 Tujuan Pembelajaran

✅ Memahami alur ETL modern  
✅ Membangun data warehouse sederhana  
✅ Menerapkan Medallion Architecture dengan tool ETL GUI (PDI/Kettle)  
✅ Dokumentasi pipeline untuk portofolio GitHub

---

## 🧰 Tools

- 🛠️ [Pentaho Data Integration (Kettle)](https://sourceforge.net/projects/pentaho/)
- 🗃️ PostgreSQL 
- 📊 Power BI (opsional)

---

## 🧾 Lisensi

Proyek ini digunakan sebagai pembelajaran. Dataset berasal dari sumber publik dan tidak untuk kepentingan komersial.

---

