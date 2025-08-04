# ETL-dwh-Pentaho

Proyek ini bertujuan membangun pipeline ETL end-to-end untuk mengintegrasikan dan mengolah data penjualan ke dalam bentuk Enterprise Data Warehouse (EDW) berbasis Star Schema. Sistem ini dirancang untuk mendukung analisis bisnis secara efisien melalui pemisahan data ke dalam tabel dimensi dan fakta, serta kompatibel dengan alat analitik seperti Power BI dan Tableau.

---

## 🔁 Proses ETL

### Staging (Raw Data)
- **Transformasi:** ORDER_STG, PRODUCTS_STG, CUSTOMERS_STG, VALUES_STG
- **Tujuan:** Menyimpan data mentah (as-is) dari CSV (Superstore+Sales.csv)
- **Proses:** Full Load, basic cleaning, truncate & insert

### Dimensi (Cleaned & Standardized)
- **Transformasi:** ORDERS_DIM, PRODUCTS_DIM, CUSTOMERS_DIM, DIM_Date
- **Tujuan:** Menyusun data dimensi terstandarisasi dengan surrogate key
- **Proses:** Lookup referensi dari VALUES_STG, validasi, enrichment

### Fact Table 
- **Transformasi:** PRE_FACT, FACT_TABLE
- **Tujuan:** Buat fact table siap yang berisi key reference dari table dimensi
- **Proses:** Join antar dimensi, hitung metrik (`Sales`, `Profit`)

---

## 📂 Struktur Direktori
      📁 ETL-Pentaho/
      │
      ├── 📁 data_source/                
      │   └── Superstore+Sales.csv
      │
      ├── 📁 docs/                      ← Dokumentasi & diagram visual
      │   ├── process_detail.png
      │
      ├── 📁 kettle/                    ← Seluruh file Kettle ETL
      │   ├── 📁 stages/               
      │   │   ├── customer_stg.ktr
      │   │   ├── product_stg.ktr
      │   │   ├── order_stg.ktr
      │   │   └── values_stg.ktr
      │   │
      │   ├── 📁 dimension/           ← Dimensional process  
      │   │   ├── customers_dim.ktr
      │   │   ├── products_dim.ktr
      │   │   ├── orders_dim.ktr
      │   │   └── dim_date.ktr
      │   │
      │   ├── 📁 fact/                 ← Faktualisasi
      │   │   ├── Pre_fact.ktr 
      |   |   ├── fact_table.ktr
      │   │
      │   └── 📁 job/                   ← Master ETL job
      │       └── DataWarehouse.kjb
      │
      └── 📄 README.md                 


---

## 📊 Output

- Data sales dengan model Star Schema dan siap untuk proses analisis
- Terintegrasi dengan cache OLAP (Mondrian, CDA)
- Siap untuk digunakan untuk visualisasi menggunakan tools seperti:
  - Tableau
  - Power BI

---

## 🧠 Tujuan Pembelajaran

✅ Memahami alur ETL  
✅ Membangun mini data warehouse/data mart
✅ Dokumentasi pipeline untuk portofolio GitHub
✅ Membangun dashboard visualisasi

---

## 🧰 Tools
<p align="center">
  <img src="https://img.icons8.com/?size=256&id=38561&format=png" alt="postgre" width="40">
  <img src="https://www.datageeks.pl/images/Article-images/102-How-to-open-Microsoft-XLSB/pdi.png" alt="Pentaho PDI" width="40" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/c/cf/New_Power_BI_Logo.svg" alt="Power BI" width="40" />
</p>

---

## 🧾 Lisensi

Proyek ini digunakan sebagai pembelajaran. Dataset berasal dari sumber publik dan tidak untuk kepentingan komersial.

---

