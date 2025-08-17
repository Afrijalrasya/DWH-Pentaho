# DWH-Pentaho

This project aims to build an end-to-end ETL pipeline to integrate and process sales data into a Star Schema-based Enterprise Data Warehouse (EDW). The system is designed to efficiently support business analytics through the separation of data into dimension tables and facts, and is compatible with analytics tools such as Power BI and Tableau.



## 🔁 ETL Process

### Staging (Raw Data)
- **Transformation:** ORDER_STG, PRODUCTS_STG, CUSTOMERS_STG, VALUES_STG
- **Purpose:** Staging raw data (as-is) from CSV (Superstore+Sales.csv)
- **Process:** Full Load, basic cleaning, truncate & insert

### Dimensions (Cleaned & Standardized)
- Transformation:** ORDERS_DIM, PRODUCTS_DIM, CUSTOMERS_DIM, DIM_Date
- **Purpose:** Construct standardized dimension data with surrogate keys
- **Process:** Lookup references from VALUES_STG, validation, enrichment

### Fact Table 
- Transformation:** PRE_FACT, FACT_TABLE
- **Purpose:** Create a ready fact table that contains key references from the dimension table
- **Process:** Join between dimensions, calculate metrics (`Sales`, `Profit`)


---

## 📂 Struktur Direktori
      📁 DWH-Pentaho/
      │
      ├── 📁 data_source/                
      │   └── Superstore+Sales.csv
      │
      ├── 📁 docs/                     
      │   ├── process_detail.png
      │   ├── dashboard.png
      |
      ├── 📁 kettle/                    ← All Kettlesfiles
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
      │   ├── 📁 fact/                 ← Factualization process
      │   │   ├── Pre_fact.ktr 
      |   |   ├── fact_table.ktr
      │   │
      │   └── 📁 job/                   ← Master ETL job
      │       └── DataWarehouse.kjb
      │
      └── 📄 README.md                 


---

## 📊 Output

- Sales data with Star Schema model and ready for analysis process
- Integrated with OLAP cache (Mondrian, CDA)
- Ready to be used for visualization using tools such as:
  - Tableau
  - Power BI
---

## 🧠 Learning Objectives

✅ Understanding ETL flow 
✅ Building mini data warehouse/data mart
✅ Pipeline documentation for GitHub portfolio
✅ Building visualization dashboard
---

## 🧰 Tools
<p align="center">
  <img src="https://img.icons8.com/?size=256&id=38561&format=png" alt="postgre" width="40">
  <img src="https://www.datageeks.pl/images/Article-images/102-How-to-open-Microsoft-XLSB/pdi.png" alt="Pentaho PDI" width="40" />
  <img src="https://upload.wikimedia.org/wikipedia/commons/c/cf/New_Power_BI_Logo.svg" alt="Power BI" width="40" />
</p>

---

## 🧾 Lisensi

This project is used as a learning tool. Datasets are from public sources and are not for commercial use.

---

