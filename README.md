# Retail ETL Data Warehouse Project

## Project Overview

This project implements an end-to-end Retail ETL Data Warehouse pipeline using modern Lakehouse architecture principles with:

* AWS S3
* Databricks
* Delta Lake
* PySpark
* SQL
* AWS Lambda
* Event-driven ETL Automation

The project simulates a real-world enterprise retail data warehouse system that ingests incremental source files, performs ETL transformations, applies SCD Type-2 logic, validates data quality, and generates Gold-layer analytical dashboards.

---

# Architecture Overview

<img width="512" height="512" alt="architecture" src="https://github.com/user-attachments/assets/fc839d24-0817-46db-864f-1bda75633d57" />

The Retail ETL Data Warehouse project follows a Star Schema architecture where the central `FACT_SALES` table stores transactional sales data such as quantity sold, revenue amount, transaction date, and foreign keys referencing multiple dimension tables including `DIM_CUSTOMER`, `DIM_PRODUCT`, and `DIM_STORE`. The dimension tables contain descriptive business information used for analytics and reporting, such as customer details, product categories, and store regions. The `DIM_CUSTOMER` table additionally implements SCD Type-2 logic to maintain historical customer changes using active/inactive records along with start and end dates. This schema enables efficient analytical querying, business KPI generation, revenue analysis, customer insights, regional reporting, and dashboard visualization while supporting scalable and optimized warehouse operations using Delta Lake and medallion architecture principles.



---

# Technologies Used

| Technology | Purpose                      |
| ---------- | ---------------------------- |
| AWS S3     | Data Lake Storage            |
| Databricks | ETL Processing               |
| Delta Lake | Transactional Lakehouse      |
| PySpark    | Data Engineering             |
| SQL        | Transformations & Validation |
| AWS Lambda | Event-driven Trigger         |
| CloudWatch | Monitoring & Logging         |
| GitHub     | Version Control              |

---

# Medallion Architecture

## Bronze Layer

Raw ingestion layer.

Features:

* Loads CSV data from S3
* Stores raw Delta tables
* Minimal transformations
* Incremental ingestion support

Tables:

* customers_raw
* products_raw
* stores_raw
* sales_transactions_raw

---

## Silver Layer

Cleansed and transformed business layer.

Implementations:

* SCD Type-2 for DimCustomer
* Data cleansing
* Deduplication
* Referential integrity validation
* Null handling
* Derived calculations

Tables:

* dim_customer
* dim_product
* dim_store
* fact_sales

SCD Type-2 Features:

* Active/Inactive records
* Historical tracking
* StartDate/EndDate management
* Incremental updates

---

## Gold Layer

Business analytics layer.

KPI Tables:

* sales_summary_daily
* product_sales_summary
* customer_sales_summary
* store_sales_summary
* region_sales_summary

Dashboard Metrics:

* Revenue
* Transactions
* Units Sold
* Customer Analytics
* Region Analytics
* Product Performance
* ETL Health Monitoring

---

# Incremental ETL Workflow

## File Naming Convention


<filename>_DDMMYYYY_HHMMSS.csv


Example:


customers_06052026_120000.csv


---

# Archival Logic

When a new incremental file arrives:

* Latest file remains in incoming zone
* Previous file is automatically moved to archive zone

Implemented using:

* Python
* AWS Lambda
* Databricks automation


---

# ETL Testing Scope

## Source-to-Target Testing

* Row count validation
* Column mapping validation
* Datatype validation

## Data Transformation Testing

* Trim validation
* Lowercase validation
* Proper case validation
* Amount calculation
* Date formatting

## Data Quality Testing

* Duplicate checks
* Null handling
* Invalid data rejection
* Referential integrity validation

## SCD Type-2 Testing

* Active vs inactive records
* Historical data validation
* StartDate & EndDate validation

## Incremental Load Testing

* Full load validation
* Incremental update validation

---

# Dashboard Features

* Revenue Analytics
* Product Performance
* Region Sales Analysis
* Customer Lifetime Value
* Store Performance
* ETL Monitoring
* Data Quality Monitoring
* SCD Type-2 Tracking

---

# Data Quality Validations

Implemented validations include:

* Duplicate detection
* Null checks
* Invalid record rejection
* Foreign key validation
* Revenue reconciliation
* SCD consistency checks

---

# Monitoring and Logging

Implemented Features:

* ETL audit logging
* Workflow monitoring
* Lambda logging
* CloudWatch integration
* Failure tracking
* Pipeline execution logs

---

# Key Features

* End-to-End ETL Pipeline
* Event-Driven Automation
* Incremental Processing
* SCD Type-2 Implementation
* Delta Lake Architecture
* Automated Archival Logic
* Data Quality Framework
* ETL QA Validation
* Gold Layer Analytics
* Dashboard Reporting

---

# Learning Outcomes

This project demonstrates:

* Modern Data Engineering
* Lakehouse Architecture
* ETL Automation
* Incremental Data Processing
* Data Warehouse Modeling
* SCD Type-2 Implementation
* ETL Testing Strategies
* Cloud-native Pipeline Design
* Event-driven Architectures
