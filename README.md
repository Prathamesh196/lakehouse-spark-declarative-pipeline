# Lakehouse Data Pipeline with Spark (Bronze–Silver–Gold)

An end-to-end **lakehouse data engineering project** built using **Apache Spark**, **Databricks**, and **Delta Lake** with a **declarative pipeline approach**.  
This project demonstrates how raw data can be incrementally ingested, validated, transformed, modeled, and served for analytics using the **Medallion Architecture**.

---

## 🎥 Project Walkthrough Video

[Watch the full project demo](https://youtu.be/bIIC44n2Dss?si=l3bF4F0NzkzdfmKX)

---

## 🧠 What This Project Demonstrates

- Declarative data pipelines using Spark
- Bronze → Silver → Gold medallion architecture
- Incremental ingestion using Autoloader
- Change Data Capture (CDC) processing
- Data quality validation inside pipeline
- Delta tables for reliable storage
- Role-based access control using Unity Catalog
- Region-specific analytical views for stakeholders

---

## 🏗️ Architecture Overview

![Architecture](docs/architecture.png)

| Layer  | Purpose | Key Operations | Output |
|--------|---------|----------------|--------|
| **Bronze** | Raw ingestion | Schema capture, metadata columns, streaming ingestion | Raw Delta tables |
| **Silver** | Cleaning & validation | Null checks, deduplication, type casting, validations | Clean Delta tables |
| **Gold** | Business modeling | Fact & dimension joins, aggregations, city views | Analytics-ready views |

---

## 📁 Repository Structure

lakehouse-spark-declarative-pipeline/
│
├── pipelines/
│ ├── bronze/
│ ├── silver/
│ └── gold/
│
├── setup/
├── docs/
└── README.md

yaml
Copy code

---

## ⚙️ Technologies Used

| Technology | Purpose |
|------------|---------|
| Apache Spark | Distributed data processing |
| Databricks | Lakehouse platform |
| Delta Lake | Reliable table storage format |
| Unity Catalog | Data governance & RBAC |
| Python | Pipeline transformations |
| SQL | Gold layer modeling & views |

---

## 🚀 Pipeline Flow

### 🔹 Bronze Layer (Raw Ingestion)
- Ingests raw `city` and `trips` data from cloud storage
- Uses streaming ingestion (Autoloader)
- Adds metadata: file name, ingest timestamp
- Stores append-only raw Delta tables

### 🔹 Silver Layer (Data Quality & Cleaning)
- Applies validation rules (ratings range, null checks)
- Deduplicates records
- Standardizes schema and column names
- Uses CDC for incremental updates

### 🔹 Gold Layer (Analytics Views)
- Joins `trips`, `city`, and `calendar`
- Creates fact and dimension-style views
- Generates **city-specific views** for regional managers

---

## ✅ Data Quality Checks Implemented

| Check | Description |
|------|-------------|
| Null validation | Ensures mandatory columns are not null |
| Range checks | Validates ratings and fare ranges |
| Deduplication | Removes duplicate trip records |
| Referential checks | Ensures trips map to valid cities |
| CDC handling | Processes only changed records |

---

## 🔐 Data Governance

- Unity Catalog used for access control
- City-level RBAC applied
- Users see only their region’s data in Gold views

---

## 📊 Example Analytical Queries (Gold)

- Revenue by city and date
- Average driver & passenger ratings
- Trip distribution by passenger type
- City-wise operational metrics

---

## 🧪 Incremental & Streaming Capabilities

- Autoloader processes only new files
- Continuous pipeline mode supported
- Change Data Feed avoids full reloads
- Declarative framework handles orchestration automatically

---

## 📸 Project Proof

Screenshots and execution proof available in the `/docs` and `/screenshots` folders.

---

## 🎯 Key Learning Outcomes

- Designing lakehouse pipelines using medallion architecture
- Implementing declarative ETL with Spark
- Embedding data validation within pipelines
- Building analytics-ready models from raw data
- Applying governance and RBAC in data platforms

---

## 📌 Conclusion

This project showcases how modern data engineering pipelines can be built using a declarative approach with Spark and Delta Lake, ensuring **data reliability**, **incremental processing**, and **analytics readiness** for business stakeholders.
