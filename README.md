DSAI3202 – Lab 2
Data Ingestion Pipeline on Azure

Student ID: 60105845
Semester: Winter 2026

INTRODUCTION

In this lab, I implemented a data ingestion pipeline on Microsoft Azure using Amazon Electronics review data. The objective was to understand how large, unstructured JSON data can be ingested, cleaned, transformed, and organized in the cloud for analytics.

The lab combines Azure Portal operations, terminal-based workflows, and Azure Data Factory to demonstrate real-world data engineering practices.

DATASETS

The following datasets from the Stanford SNAP Amazon Reviews collection were used:

• Electronics Reviews Dataset
File: reviews_Electronics_5.json.gz (~500 MB compressed)
Contains customer reviews, ratings, timestamps, and product identifiers.

• Electronics Metadata Dataset
File: meta_Electronics.json.gz (~170 MB compressed)
Contains product information such as title, category, brand, and price.

AZURE STORAGE SETUP

An Azure Data Lake Storage Gen2 account was created with Hierarchical Namespace enabled.
Three containers were created to organize the data:

• raw – original unprocessed data
• processed – transformed data
• curated – reserved for future analytics

DATA INGESTION

The metadata file was uploaded to the raw container using the Azure Portal.

Due to its large size, the reviews dataset was ingested using an Azure Machine Learning Compute Instance. The file was downloaded using terminal commands and uploaded to Azure Blob Storage using azcopy and a SAS token.

METADATA FIX

The metadata file was not in valid JSON format. Each line was originally stored as a Python dictionary. A Python script was used to convert the file into valid line-delimited JSON, and the corrected file was uploaded back to the raw container for further use.

AZURE DATA FACTORY PIPELINE

An Azure Data Factory (V2) instance was created to process the raw review data.

A linked service was configured to connect ADF to the storage account. Source and sink datasets were created for JSON input and Parquet output.

A Mapping Data Flow was implemented to:
• Read raw JSON review data
• Derive a review_year column from unixReviewTime
• Write the output in Parquet format
• Partition the data by review_year

The pipeline was executed successfully, producing partitioned Parquet files in the processed container.

OUTCOME

This lab resulted in a fully functional Azure-based data ingestion pipeline. Large JSON data was successfully ingested, cleaned, transformed, and stored in an optimized format suitable for analytics.

CONCLUSION

This lab provided practical experience in building cloud-native data ingestion pipelines using Azure Storage, Azure Machine Learning, and Azure Data Factory, reflecting real-world data engineering workflows.
