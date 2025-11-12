# covid-19_prediction_reporting
Objective: Date lake built with multiple data sources in Europan countries to aid data scientists to predit the spread of the virus
  - Confirmed cases
  - Mortality
  - Hospital Admissions / ICU Cases
  - Testing Numbers
  - Countries population by age group
Solution Architecture:

Data Sources:
  -  ECDC Website for Covid-19 Data - https://www.ecdc.europa.eu/en/covid-19/data
  -  Euro Stat Website for Population Data -https://ec.europa.eu/eurostat/web/main/data/bulkdownload
  -  
Data Warehouse:
  Objective : Aid reporting and identify trends by using PowerBI
  - Confirmed cases
  - Mortality
  - Hospital Admissions / ICU Cases
  - Testing Numbers

Storage Solutions Used - https://learn.microsoft.com/en-us/azure/storage/common/storage-introduction
  - Azure SQL Database - https://learn.microsoft.com/en-us/azure/azure-sql/database/sql-database-paas-overview?view=azuresql
  - Azure Blob Storage - https://learn.microsoft.com/en-us/azure/synapse-analytics/overview-what-is
  - Azure Data Lake Storage Gen 2 - https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction

Data Ingestion from Azure Blob
  Azure Blob Storage -> Azure Data Lake
  Copy Activity
  <img width="1243" height="513" alt="image" src="https://github.com/user-attachments/assets/e070920a-72ae-4b28-8c23-e6490fbcf275" />

Naming Standard
  - Link Services - ls_ablob_coviodreportingdkrsa
  - Source Dataset - ds_population_raw_gz
  - Link Services - ls_adls_covidreportingdkrdl
  - Sink Dataset - ds_population_raw_tsv
  - Pipeline - pl_injest_population_data
  - Copy Activity - Copy Population Data

Creating Link Services

Creating Datasets
<img width="1365" height="595" alt="image" src="https://github.com/user-attachments/assets/34340b61-116c-4e2e-b9f4-d2231b3eba06" />
Creating Pipeline
<img width="1167" height="707" alt="image" src="https://github.com/user-attachments/assets/d2abb8a9-4402-4a25-8659-056b5fa43d1e" />
Output Generated (Viewed throuh Storage Explorer)
<img width="1450" height="621" alt="image" src="https://github.com/user-attachments/assets/b259518e-5e20-4c31-a5b8-fda3c868340e" />
Adding a control flow to copy data as soon as file is available
<img width="1914" height="903" alt="image" src="https://github.com/user-attachments/assets/8de96eca-ed39-46c3-b932-bee259e38e0e" />
File validation using a control flow - If receiving file is available as expected
<img width="1916" height="879" alt="image" src="https://github.com/user-attachments/assets/a772c939-4ad1-4cc2-a566-76b55df8c175" />
<img width="1918" height="899" alt="image" src="https://github.com/user-attachments/assets/ab265f93-2adc-41eb-8aab-91dec8b10f86" />
File deleted as soon as file copy is complete
<img width="1916" height="901" alt="image" src="https://github.com/user-attachments/assets/041224be-9d80-4276-ac70-82dbe98e43e1" />
<img width="1916" height="647" alt="image" src="https://github.com/user-attachments/assets/65eb5518-a616-43c5-8f08-7cfb478f6308" />
Scheduling pipeline in ADF using Triggers
  - Schedule
  - Thumbling Window
  - Storage Events
  - Custom Events

Storage event trigger
<img width="1915" height="478" alt="image" src="https://github.com/user-attachments/assets/e4c00400-d932-40e5-9260-46129efd0965" />

Data Flows (Mapping Data Flow)
1. Code free data transformations
2. Does the ETL (Similar to SSIS)
3. Executed on data factory managed Databricks Spark Clusters
4. Benefits from data factory scheduling and monitoring capabilities
5. Data Flows -> Databricks -> Spark Cluster

Transform Cases & Deaths data
<img width="1148" height="629" alt="image" src="https://github.com/user-attachments/assets/a584568f-1f0d-420c-93ba-6d7c4602ab57" />
Data Flow to Transform Daa
<img width="1920" height="543" alt="image" src="https://github.com/user-attachments/assets/745f1fca-b430-4055-bc09-b23d01544828" />

Transform Cases & Deaths data
<img width="1148" height="629" alt="image" src="https://github.com/user-attachments/assets/a584568f-1f0d-420c-93ba-6d7c4602ab57" />
Data Flow to Transform Daa
<img width="1920" height="543" alt="image" src="https://github.com/user-attachments/assets/745f1fca-b430-4055-bc09-b23d01544828" />





