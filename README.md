# End-To-End-Data-Engineering-Project
An end-to-end ETL (Extract, Transform, Load) pipeline from an on-premises SQL Server to Microsoft Azure involves various components and services for ingestion, transformation, storage, and visualization of data. Below is a step-by-step flow of the ETL pipeline process:
# This Section explains the flow of an End To End ETL pipeline 

![Screenshot 2024-09-25 205339](https://github.com/user-attachments/assets/1b6cf53a-a4ea-4fea-9644-658860e23485)

# STEP1 : Download the dataset "AdventureWorks2017" 

# STEP2 : Restore the Dataset on SSMS SQL SERVER
1. Data Source: On-Premises SQL Server
Objective: Extract data from the on-premises SQL Server database.

Tools: On-premises SQL Server, Self-hosted Integration Runtime (SHIR).
A Self-hosted Integration Runtime (SHIR) is installed within the on-premise environment to facilitate a secure connection between the on-premises SQL Server and the Azure cloud.
The SHIR enables data extraction from SQL Server tables or views and handles secure data movement into Azure services.


Steps:

![Screenshot (1)](https://github.com/user-attachments/assets/5a9cbcbe-fdb4-470c-b470-3659298f57cd) 

# STEP3 : Go to Azure Portal and create a resource group and under that resouce group create the following azure services:
1. Storage Account 
2. Azure Data Factory(ADF)
3. Databricks
4. Azure Key Vault
5. Azure Synapse Analytics

![Screenshot 2024-09-26 000007](https://github.com/user-attachments/assets/ff6a3759-1030-43ff-8c66-aea71d045c0d)

# STEP 4: Create containers in the Azure portal Storage Account For Storing different Level of Data Transformation 

![Screenshot 2024-09-26 001309](https://github.com/user-attachments/assets/480a06f6-4a91-4c8a-b818-0a83599f1355)

# STEP 5:  Data Ingestion: Azure Data Factory (ADF)

Objective: Ingest the extracted data from SQL Server into Azure.
Tools: Azure Data Factory (ADF), Self-hosted Integration Runtime.

Steps:
Azure Data Factory uses SHIR to connect to the on-premise SQL Server, ensuring secure data movement.
Linked Services in ADF define connections to the on-premise SQL Server and Azure Data Lake.
A pipeline is created in ADF with Copy Data Activity to extract data from SQL Server and ingest it into Azure Data Lake Storage Gen2.


![Screenshot 2024-09-26 185603](https://github.com/user-attachments/assets/1b17256c-44eb-4ddd-b555-ba6a734d5a2f)

. Data Transformation: Azure Databricks
Objective: Cleanse, transform, and process the data for downstream analysis.

Tools: Azure Databricks, PySpark or Scala.


# Step 6: Data Transformation 
Azure Databricks is used to process and transform the data stored in the Azure Data Lake.
Data transformation happens in stages, typically divided into:
Bronze Layer: Raw data ingestion.
Silver Layer: Data cleaning and transformation.
Gold Layer: Aggregated, ready-for-analysis data.
Azure Databricks notebooks can be used to write transformations using PySpark or Scala, including filtering, joining, and aggregating data.
# Mounting Databricks Notebook 

![Screenshot 2024-09-26 190302](https://github.com/user-attachments/assets/a78bf2fb-577a-4b54-8090-465d5a88fdde)

# Data Transfromation From Bronze Layer to Silver Layer 

![Screenshot 2024-09-26 190326](https://github.com/user-attachments/assets/886e1fea-e432-4360-a6bd-47c147ae7900)

# Data Transformation from Silver Layer to Gold Layer 

![Screenshot 2024-09-26 190408](https://github.com/user-attachments/assets/0b5df6cd-fa9d-4e33-848c-c97342cfd166)

# Step 7 :  Data Loading & Analytics: Azure Synapse Analytics

Objective: Load transformed data into Azure Synapse for advanced analytics and reporting.
Tools: Azure Synapse Analytics, SQL Pools, or Serverless SQL Pools.

Steps:
Once the data is transformed, it is loaded into Azure Synapse Analytics for querying and analysis.
Data can be stored in dedicated SQL pools or serverless SQL pools.
Azure Synapse allows running complex SQL queries, building data models, and generating reports based on the processed data.

![Screenshot 2024-09-26 000506](https://github.com/user-attachments/assets/75806c10-dabd-401a-a29f-3fd2f6a7b1d5)

# Step 8 :  Data Visualization: Power BI

Objective: Visualize the data and provide business insights through interactive dashboards.
Tools: Power BI, Power BI Service.

Steps:
Power BI connects to the data stored in Azure Synapse Analytics or directly to the Gold Layer in Azure Data Lake.
Reports and dashboards are created in Power BI using visualizations like charts, graphs, and KPIs.
The Power BI Service is used to publish and share dashboards with business users.

![Screenshot 2024-09-26 005829](https://github.com/user-attachments/assets/f6cf3f8b-e572-42ed-8106-b5c428849ad3)

# Step 9 :. Data Security & Governance: Azure Active Directory & Azure Key Vault

Objective: Ensure secure access to data and manage sensitive information.
Tools: Azure Active Directory (AAD), Azure Key Vault.

Steps:
Azure Active Directory (AAD) is used to manage identity and access control to ensure that only authorized users and services can access data.
Azure Key Vault securely stores sensitive information like connection strings, API keys, and secrets used in the ETL pipeline.
Role-based access controls (RBAC) are set up in Azure to govern access to ADF, Databricks, and Synapse Analytics.


