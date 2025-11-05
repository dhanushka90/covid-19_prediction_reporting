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
