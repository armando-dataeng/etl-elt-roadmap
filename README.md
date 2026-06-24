# ETL / ELT Roadmap

A comprehensive roadmap for learning **ETL**, **ELT**, **Data Pipelines**, **Data Integration**, and **Modern Data Engineering**.

This repository is designed for:

- Data Engineers
- Analytics Engineers
- BI Developers
- Data Analysts
- Database Developers
- Cloud Engineers
- Anyone interested in building data pipelines

---

# What is ETL?

ETL stands for:

```text
Extract
Transform
Load
```

It is the process of moving data from source systems into a Data Warehouse.

Example:

```text
ERP
   ↓
ETL
   ↓
Data Warehouse
```

---

# What is ELT?

ELT stands for:

```text
Extract
Load
Transform
```

Instead of transforming data before loading it, the transformation occurs inside the Data Warehouse.

Example:

```text
ERP
   ↓
Load
   ↓
Data Warehouse
   ↓
Transform
```

ELT is the dominant approach in modern cloud platforms such as:

- Snowflake
- BigQuery
- Databricks
- Azure Synapse

---

# Learning Path

The roadmap is divided into seven major sections:

```text
ETL Fundamentals
        ↓
Data Pipelines
        ↓
Data Loading Strategies
        ↓
Data Quality
        ↓
Pipeline Orchestration
        ↓
Modern Data Tools
        ↓
Production Data Engineering
```

---

# ETL Fundamentals

Learn the foundations of data integration.

- [ ] 01_ETL_FUNDAMENTALS
- [ ] 02_ELT_FUNDAMENTALS
- [ ] 03_ETL_VS_ELT

Topics covered:

- ETL architecture
- ELT architecture
- Data movement
- Data integration patterns

---

# Data Pipelines

Learn how data moves through systems.

- [ ] 04_DATA_SOURCES
- [ ] 05_DATA_EXTRACTION
- [ ] 06_DATA_TRANSFORMATION
- [ ] 07_DATA_LOADING

Topics covered:

- APIs
- Databases
- CSV files
- JSON files
- Data transformations
- Loading strategies

---

# Data Loading Strategies

Learn how data is loaded efficiently.

- [ ] 08_INCREMENTAL_LOADS
- [ ] 09_FULL_LOADS
- [ ] 10_CHANGE_DATA_CAPTURE_CDC

Topics covered:

- Incremental processing
- Full refresh
- CDC
- Watermarks
- Change tracking

---

# Data Quality

Learn how to build reliable pipelines.

- [ ] 11_DATA_QUALITY
- [ ] 12_DATA_VALIDATION
- [ ] 13_ERROR_HANDLING

Topics covered:

- Data validation
- Data testing
- Data profiling
- Error recovery
- Data observability

---

# Pipeline Orchestration

Learn how production pipelines are managed.

- [ ] 14_ORCHESTRATION
- [ ] 15_SCHEDULING
- [ ] 16_PIPELINE_MONITORING

Topics covered:

- Workflow management
- Scheduling
- Monitoring
- Alerting
- Logging

---

# Modern Data Tools

Learn the most common tools used in Data Engineering.

- [ ] 17_AIRFLOW
- [ ] 18_DBT
- [ ] 19_AZURE_DATA_FACTORY

Topics covered:

- Apache Airflow
- dbt
- Azure Data Factory
- Pipeline automation

---

# Data Processing Patterns

Learn how modern data systems process information.

- [ ] 20_BATCH_PROCESSING
- [ ] 21_STREAM_PROCESSING

Topics covered:

- Batch workloads
- Streaming workloads
- Event-driven architecture
- Real-time analytics

---

# Case Study

Apply everything learned in a practical project.

- [ ] 22_ETL_CASE_STUDY
- [ ] 23_MODERN_DATA_STACK

Topics covered:

- End-to-end pipelines
- Production architecture
- Cloud data platforms
- Modern Data Stack

---

# Roadmap Progression

```text
ETL FUNDAMENTALS
        ↓
ELT FUNDAMENTALS
        ↓
ETL VS ELT
        ↓
DATA SOURCES
        ↓
DATA EXTRACTION
        ↓
DATA TRANSFORMATION
        ↓
DATA LOADING
        ↓
INCREMENTAL LOADS
        ↓
FULL LOADS
        ↓
CDC
        ↓
DATA QUALITY
        ↓
DATA VALIDATION
        ↓
ERROR HANDLING
        ↓
ORCHESTRATION
        ↓
SCHEDULING
        ↓
PIPELINE MONITORING
        ↓
AIRFLOW
        ↓
DBT
        ↓
AZURE DATA FACTORY
        ↓
BATCH PROCESSING
        ↓
STREAM PROCESSING
        ↓
ETL CASE STUDY
        ↓
MODERN DATA STACK
```

---

# Recommended Previous Roadmap

Before starting this repository, complete:

```text
SQL Roadmap
        ↓
Database Design Roadmap
        ↓
ETL / ELT Roadmap
```

---

# Recommended Next Roadmap

After completing this repository, continue with:

```text
Data Lake Roadmap
        ↓
Apache Spark Roadmap
        ↓
Cloud Data Engineering Roadmap
        ↓
Data Engineering Roadmap
```

---

# Repository Goal

The objective is not only to learn ETL tools.

The objective is to understand:

- How data moves through systems.
- How production pipelines are built.
- How modern Data Platforms operate.
- How Data Engineers design reliable architectures.
- How to think like a Data Engineer.

---

# License

This repository is intended for educational purposes and continuous learning.

Contributions and improvements are welcome.
