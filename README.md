# 📘 Azure Data Factory for Data Engineers — Retail Store Analytics Project

This repository contains a full **end-to-end Azure Data Engineering project** built for a Retail Store dataset including **Orders, Order Items, Products, Customers, and Store Locations**.

The solution demonstrates:

- Building a complete multi-zone **Data Lakehouse**
- Orchestrating pipelines with **Azure Data Factory**
- Transforming data using **ADF Mapping Data Flows**
- Modeling datasets for **Azure SQL analytics**
- Creating **monthly aggregated insights** for BI tools

---

# 🏗️ Solution Architecture

![Architecture](<sandbox:/mnt/data/Screenshot 2025-11-16 101526.png>)

---

# 🗂️ Data Lake Zone Blueprint

![Lake Blueprint](sandbox:/mnt/data/Course-Azure-Data-Factory-Data-Engineering-on-Azure-and-Fabric-Udemy-11-16-2025_09_50_AM.png)

---

# 📁 Repository Structure

retail-store-adf-project/
│
├── assets/ # Architecture diagrams & ADF screenshots
│
├── data_lake/
│ ├── landing/
│ ├── raw/
│ ├── cleansed/
│ ├── structured/
|     ├── sql_scripts/
│     └── create_retail_tables_ddl.sql
│ └── analytics/
│
│
└── README.md

---

# 1️⃣ Environment Setup

## 🔹 Azure Data Lake Gen2 — Layered Storage

![Layers](<sandbox:/mnt/data/Screenshot 2025-11-16 101453.png>)

![Layers2](<sandbox:/mnt/data/Screenshot 2025-11-16 101512.png>)

---

# 2️⃣ Architecture Layers (RAW → CLEANSED → STRUCTURED → ANALYTICS)

![LakeLayers](<sandbox:/mnt/data/Screenshot 2025-11-16 095317.png>)

---

# 3️⃣ Azure Data Factory Pipelines

---

## ▶ Master Pipeline — `pl_execute_retail`

This pipeline orchestrates the entire workflow:

1. Landing → Raw  
2. Raw → Cleansed  
3. Cleansed → Structured  
4. Structured → Analytics  

### Screenshot  
![MasterPipeline](<sandbox:/mnt/data/Screenshot 2025-11-16 100559.png>)

---

## ▶ Pipeline: `pl_landing_to_raw`

Performs initial ingestion using Copy Data activities for:

- Customers  
- Orders  
- Order Items  
- Products  
- Stores  

### Screenshots  
![LandingToRaw](<sandbox:/mnt/data/Screenshot 2025-11-16 100537.png>)  
![LandingToRaw2](<sandbox:/mnt/data/Screenshot 2025-11-16 100550.png>)  
![LandingToRaw3](<sandbox:/mnt/data/Screenshot 2025-11-16 100212.png>)

---

## ▶ Pipeline: `pl_raw_to_cleansed`

Transforms raw data:

- Normalize column names  
- Cast datatypes  
- Add timestamps  
- Format strings  

### Screenshots  
Customers cleansing:  
![CustomersRawToCleansed](<sandbox:/mnt/data/Screenshot 2025-11-16 095907.png>)

Order Items cleansing:  
![OrderItemsRawToCleansed](<sandbox:/mnt/data/Screenshot 2025-11-16 095931.png>)

Orders cleansing:  
![OrdersRawToCleansed](<sandbox:/mnt/data/Screenshot 2025-11-16 095855.png>)

Products cleansing:  
![ProductsRawToCleansed](<sandbox:/mnt/data/Screenshot 2025-11-16 095940.png>)

Stores cleansing:  
![StoresRawToCleansed](<sandbox:/mnt/data/Screenshot 2025-11-16 095920.png>)

---

## ▶ Pipeline: `pl_cleansed_to_structured`

Transforms cleansed data into modeled SQL-like structures:

- Adds computed SUBTOTAL  
- Standardizes schema  
- Reorders fields  
- Adds updated timestamps  

### Screenshots  
Orders cleansed → structured:  
![OrdersStruct](<sandbox:/mnt/data/Screenshot 2025-11-16 095247.png>)

Products cleansed → structured:  
![ProductsStruct](<sandbox:/mnt/data/Screenshot 2025-11-16 095258.png>)

Stores cleansed → structured:  
![StoresStruct](<sandbox:/mnt/data/Screenshot 2025-11-16 095308.png>)

---

## ▶ Pipeline: `pl_structured_to_analytics`

Generates **monthly aggregated insights**:

- Store-wise monthly revenue  
- Product-wise monthly revenue  
- Order status distribution  

### Screenshots  
Stores monthly:  
![StoresMonthly](<sandbox:/mnt/data/Screenshot 2025-11-16 093646.png>)

Products monthly:  
![ProductsMonthly](<sandbox:/mnt/data/Screenshot 2025-11-16 100156.png>)

Analytics pipeline:  
![AnalyticsPipeline](<sandbox:/mnt/data/Screenshot 2025-11-16 100212.png>)

---

# 4️⃣ Data Flows (Mapping Data Flows)

---

## 🟦 Raw → Cleansed

### Screenshot  
![RawToCleansed](<sandbox:/mnt/data/Screenshot 2025-11-16 095228.png>)

---

## 🟩 Cleansed → Structured

### Screenshot  
![CleansedToStructured](<sandbox:/mnt/data/Screenshot 2025-11-16 095317.png>)

---

## 🟧 Structured → Analytics

Product-level:  
![ProductAnalyticsFlow](<sandbox:/mnt/data/Screenshot 2025-11-16 093646.png>)

Store-level:  
![StoreAnalyticsFlow](<sandbox:/mnt/data/Screenshot 2025-11-16 093646.png>)

---

# 5️⃣ SQL Structured Layer

Final curated data is loaded into Azure SQL DB.

---

## STORES Table  
![SQLStores](<sandbox:/mnt/data/Screenshot 2025-11-16 100804.png>)

---

## PRODUCTS Table  
![SQLProducts](<sandbox:/mnt/data/Screenshot 2025-11-16 100752.png>)

---

## ORDER_ITEMS Table  
![SQLOrderItems](<sandbox:/mnt/data/Screenshot 2025-11-16 100740.png>)

---

## ORDERS Table  
![SQLOrders](<sandbox:/mnt/data/Screenshot 2025-11-16 100804.png>)

---

# 6️⃣ Analytics Layer Output (SQL)

Outputs include:

- `PRODUCTS_ORDERS_MONTHLY`
- `STORES_ORDERS_MONTHLY`

---

# 7️⃣ End-to-End Flow Summary

### ✔ Extract  
Landing → Raw (Copy Data)

### ✔ Transform  
Raw → Cleansed (Data Flows)

### ✔ Model  
Cleansed → Structured (SQL-shaped)

### ✔ Aggregate  
Structured → Analytics (Monthly KPIs)

### ✔ Serve  
SQL tables → BI (Power BI / Tableau)

---

# 👨‍💻 Author

**Rishikesh Gundla**  
Senior BI Engineer | Data Engineering & Analytics  
LinkedIn: https://www.linkedin.com/in/rishigundla
