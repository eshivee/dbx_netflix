#  Netflix Data Pipeline (End-to-End Data Pipeline with Azure Databricks and Azure Data Factory)

An Azure Databricks project that creates a data pipeline to generate data that can now be used for downstream users for their specific needs. It demonstrates my ability to **write production-quality Pyspark and SQL codes, design efficient queries, and build robust data pipelines so that users can draw insights from the data generated**.

The pipeline processes Netflix's data which includes directors, cast, countries, categories, titles and their details through a medallion architecture (Bronze → Silver → Gold), implementing incremental loading, slowly changing dimensions (SCD Type 1 and 2) using Delta Live Tables DLT, to create analytics-ready datasets.

## 🏗️ Architecture

![Project Architecture](images/Project_Architecture.png)

### Data Flow
```
Source Data (CSV) → GitHub → Azure Data Factory (Staging) → → → → → → → → → → 
                                                                              ↓    
Source Data (CSV) → ADLS Gen 2 → Databricks (Staging) → Bronze Layer → Silver Layer → Gold Layer
                                                                ↓              ↓           ↓
                                                              Raw Data    Cleaned Data    Analytics
```
### Technology Stack

- **Cloud Data Warehouse**: Azure Databricks
- **Transformation Layer**: Azure Databricks
- **Cloud Storage**: ADLS Gen2
- **Version Control**: Git
- **Key Azure Databricks Features**:
  - AutoLoader for Incremental Loading
  - Azure Data Factory
  - Dbutils Widgets for Parameterization
  - Delta Live Tables (SCD Type 2)
  - Databricks Workflows
  - Adls Gen2 Hierachical Namespace(Delta Lake)
  - Unity Catalog
 
## 📊 Data Model

### Medallion Architecture

#### 🥉 Bronze Layer (Raw Data)
Raw data ingested from Delta Lake:
- `directors` - Raw directors information 
- `cast` - Raw cast details
- `countries` - Raw countries details
- `categories` - Raw movie categories
- `titles` - Raw customer orders

#### 🥈 Silver Layer (Cleaned Data)
Cleaned and standardized data:
- `directors` - Validated directors information 
- `cast` - Validated cast details
- `countries` - Validated countries details
- `categories` - Valdidated movie categories
- `titles` - Validated customer orders

