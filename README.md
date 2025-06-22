# Real-Time-Transaction-Processing-Pipeline
# ⚡ Real-Time Transaction Batch Processing Pipeline

This project simulates a **real-time data processing pipeline** where batches of transactions are ingested every second from **Azure Data Lake**, processed in stages, and finally delivered to consumers in a synchronized and controlled manner.

It showcases modern **data engineering practices** including real-time aggregation, staging architecture, Delta Lake integration, and inter-process synchronization.

---

## 🚀 Project Overview

- A new batch of transaction data is **ingested every second** from Azure Data Lake.
- Each batch is processed to calculate key metrics **per merchant**, such as:
  - Average transaction amount
  - Total transaction count
  - Number of female customers
- Data is staged, processed, and stored in various layers to maintain data lineage and integrity.

---

## 🔧 Technologies Used

- **Azure Data Lake** (source layer)
- **Azure Delta Lake** (raw, processed, semi-processed data)
- **Apache Spark (PySpark)** for batch transformations
- **PostgreSQL** for staging tables and sync-state control
- **Delta Tables** for ACID-compliant processing layers

---

## 🧱 Architecture Overview

### ⛓️ Batch Ingestion
- Data is ingested from Azure Data Lake in 1-second intervals.
- Raw data is written to **Delta Lake raw layer**.

### 🔄 Staging and Transformation
- Intermediate (semi-processed) data is written to **staging tables**.
- Processing includes grouping, filtering, and aggregation logic:
  - Avg transaction amount
  - Gender-based counts per merchant

### 🗃️ Syncing & Control Logic
- PostgreSQL used to store:
  - Intermediate staging tables
  - Sync control tables to track the **next chunk to be consumed**
- Ensures **exactly-once processing** by consumer systems through chunk tracking and checkpointing logic.

---

## 📁 Data Flow Summary

1. Azure Data Lake → Delta Lake (raw layer)  
2. Delta Lake → Staging Layer (intermediate calculations)  
3. Staging Tables → PostgreSQL (tracking, syncing, partial state)  
4. PostgreSQL → Consuming services (controlled via sync logic)

---

## 🎯 Key Features

- ✅ Real-time ingestion with second-level batch control
- ✅ Robust pipeline with fault tolerance and chunk tracking
- ✅ PostgreSQL-based synchronization ensures safe, sequenced consumption
- ✅ Modular architecture supporting future enhancements

---

## 📌 Use Cases

- Merchant-level performance analytics  
- Gender-based behavior analysis  
- Real-time dashboard enablement  
- Backpressure-safe streaming simulation

---

## 📄 Author

**Gautam Rawat**  
Email: gautam.rawat3007@gmail.com  
LinkedIn: [linkedin.com/in/gautam-rawat-710029194](https://linkedin.com/in/gautam-rawat-710029194)

