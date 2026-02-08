# DSAI3202 – Lab 2  
## Data Ingestion in Azure (Up to Azure Data Factory Pipeline)

**Student ID:** 60105845  
**Semester:** Winter 2026  
**Course:** DSAI3202 – Programming IoT Applications  

---

## 📌 Lab Objective
The objective of this lab is to design and implement a **cloud-based data ingestion pipeline** on Microsoft Azure. The lab demonstrates how large-scale raw data can be ingested, processed, and transformed into an optimized format using Azure services.

The pipeline follows a layered data lake architecture and prepares data for downstream analytics.

---

## 📂 Dataset Description
The datasets used in this lab are obtained from the **Stanford SNAP Amazon Reviews Dataset**.

### 1. Electronics Reviews Dataset
- **File:** `reviews_Electronics_5.json.gz`
- **Approx. Size:** ~500 MB (compressed)
- **Description:** Contains user reviews, ratings, timestamps, and product identifiers.

### 2. Electronics Metadata Dataset
- **File:** `meta_Electronics.json.gz`
- **Approx. Size:** ~170 MB (compressed)
- **Description:** Contains product metadata such as title, category, brand, and price.

---

## ☁️ Azure Services Used
- **Azure Data Lake Storage Gen2**
- **Azure Machine Learning**
- **Azure Data Factory**

---

## 🏗️ Storage Architecture
An Azure Data Lake Storage Gen2 account was created with **hierarchical namespace enabled**.

### Containers Created
- `raw` – stores raw JSON data
- `processed` – stores transformed Parquet data
- `curated` – reserved for future analytics (not used in this lab)

---

## 📥 Data Ingestion Process

### Step 1: Upload Raw Reviews Data
- The large reviews dataset was downloaded inside an **Azure ML Compute Instance** using `wget`.
- The file was decompressed and uploaded to the `raw` container using **azcopy and a SAS token**.

**Result:**
