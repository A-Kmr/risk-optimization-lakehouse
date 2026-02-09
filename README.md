# risk-optimization-lakehouse
End-to-end credit risk engine on Databricks using the Medallion Architecture (Bronze/Silver/Gold) and PySpark

# 🏦 End-to-End Credit Risk Lakehouse & Optimization Engine

![Status](https://img.shields.io/badge/Status-In%20Progress-yellow) ![Platform](https://img.shields.io/badge/Platform-Databricks-orange) ![Language](https://img.shields.io/badge/Language-Python%20%7C%20PySpark-blue)

> **🚧 Project currently being uploaded. Full code and documentation coming soon.**

## 📋 Project Overview
This project implements a scalable **Data Lakehouse** on Databricks to process **2.2 million** loan records. It features a complete ETL pipeline using **Medallion Architecture**, a **Gradient Boosted Tree (GBT)** model to predict loan default probability, and a financial simulation demonstrating a improvement in collection recovery efficiency.

## 🛠️ Tech Stack
* **Platform:** Databricks (Community Edition 13.x)
* **Processing:** PySpark 3.4
* **Storage:** Delta Lake 2.4 (Bronze/Silver/Gold)
* **Machine Learning:** Spark MLlib (GBT Classifier)
* **Language:** Python 3.10

## 📂 Upcoming Repository Structure
The following notebooks and artifacts are being finalized for upload:

* **`01_Bronze_Ingestion.ipynb`**: Raw data ingestion from zipped archives into Delta Tables.
* **`02_Silver_Cleaning.ipynb`**: Schema enforcement, data cleaning, and feature engineering.
* **`03_Gold_Modeling.ipynb`**: Training the GBT classifier and evaluating AUC (0.71).
* **`04_Financial_Simulation.ipynb`**: ROI analysis comparing Random vs. Model-Driven strategies.
---
