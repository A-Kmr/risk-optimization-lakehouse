# risk-optimization-lakehouse
End-to-end credit risk engine on Databricks using the Medallion Architecture (Bronze/Silver/Gold) and PySpark

# 🏦 End-to-End Credit Risk Lakehouse & Optimization Engine

![Status](https://img.shields.io/badge/Status-In%20Progress-yellow) ![Platform](https://img.shields.io/badge/Platform-Databricks-orange) ![Language](https://img.shields.io/badge/Language-Python%20%7C%20PySpark-blue)

> **🚧 Project currently being uploaded. Full code and documentation coming soon.**
> **🚀 Project Status:** Bronze and Silver layers are complete. Modeling (Gold) in progress.
> 
## 📋 Project Overview
This project implements a scalable **Data Lakehouse** on Databricks to process **2.2 million** loan records. It features a complete ETL pipeline using **Medallion Architecture**, a **Gradient Boosted Tree (GBT)** model to predict loan default probability, and a financial simulation demonstrating a improvement in collection recovery efficiency.

## 🛠️ Tech Stack
* **Platform:** Databricks (Community Edition 13.x)
* **Processing:** PySpark 3.4
* **Storage:** Delta Lake 2.4 (Bronze/Silver/Gold)
* **Machine Learning:** Spark MLlib (GBT Classifier)
* **Language:** Python 3.10

---

## 🏗️ Architecture & Pipeline Details

### **1️⃣ Bronze Layer: Raw Ingestion**
**Goal:** Ingest immutable raw data from the Lending Club dataset (2007–2018) into the Lakehouse.
* **Source:** Zipped CSV archives uploaded to DBFS (Databricks File System).
* **Engineering:**
  * utilized shell commands (`%sh unzip`) to dynamically extract data within the notebook environment.
  * Ingested **2,260,668 rows** of raw loan data.
  * Saved as **Delta Tables** to enable ACID transactions and version history.
* **Notebook:** `01_Bronze_Ingestion.ipynb`

### **2️⃣ Silver Layer: Cleaning & Schema Enforcement**
**Goal:** Clean data, handle schema mismatches, and prepare high-quality features for machine learning.
* **Filtering:** Removed "Current" loans to prevent data leakage, keeping only terminal states ("Fully Paid" or "Charged Off"), resulting in **~1.2 million** records.
* **Resilient Schema Enforcement:** * Addressed schema drift where numeric columns (e.g., `annual_inc`) contained dirty strings.
  * Implemented PySpark's **`try_cast`** logic to handle bad data gracefully (converting errors to `NULL` instead of crashing the pipeline).
* **Feature Engineering:**
  * Converted string-based `term` (e.g., " 36 months") to integer (`36`).
  * Extracted numeric experience from `emp_length` (e.g., "10+ years" → `10`).
* **Notebook:** `02_Silver_Cleaning.ipynb`
  
---

## 📂 Upcoming Repository Structure
The following notebooks and artifacts are being finalized for upload:

* **`03_Gold_Modeling.ipynb`**: Training the GBT classifier and evaluating AUC (0.71).
* **`04_Financial_Simulation.ipynb`**: ROI analysis comparing Random vs. Model-Driven strategies.
---

*Created by Anirudh Pentapati | February 2026*
