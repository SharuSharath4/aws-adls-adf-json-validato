# AWS to ADLS JSON Validation Pipeline

This project is an end-to-end **event-driven data engineering pipeline** that transfers and validates JSON files from **AWS S3 to Azure SQL Database** via **Azure Data Lake**, using **Azure Functions** and **Azure Data Factory (ADF)**.

## Workflow Overview

1. **Data Ingestion**  
   - JSON files are moved from **AWS S3** to **Azure Data Lake Storage Gen2 (ADLS)**.

2. **Validation via Azure Function**  
   - A **blob-triggered Azure Function App** is invoked when a new file lands in ADLS.
   -  Valid JSON → Moved to `staging/` folder  
   -  Invalid JSON → Moved to `rejected/` folder

3. **Data Transfer to Azure SQL via ADF**  
   - A **Storage Event Trigger** detects new files in the `staging/` folder.
   - An **ADF pipeline** is triggered to load the validated JSON data into **Azure SQL Database**.

## ⚙️ Technologies Used

- **AWS S3**
- **Azure Data Lake Storage Gen2 (ADLS)**
- **Azure Functions (JavaScript)**
- **Azure Data Factory (ADF)**
- **Azure SQL Database**
- **Event Grid & Blob Triggers**
- **GitHub Integration with ADF**
