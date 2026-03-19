# MedallionEcom – E-commerce Data Pipeline

> Production-style data pipeline simulating real-world data engineering challenges including SCD handling, streaming ingestion, and Delta Lake optimizations.

## Overview
End-to-end data engineering pipeline built using PySpark and Delta Lake, implementing the Medallion Architecture (Bronze → Silver → Gold) for analytics-ready data.

## 🏗 Architecture
- **Bronze:** Raw streaming ingestion from source files
- **Silver:** Cleaned, deduplicated, schema-enforced data
- **Gold:** Star schema with fact and dimension tables for analytics

## Key Features
- Streaming ingestion using Auto Loader
- Data cleaning (null handling, deduplication)
- SCD Type 1 (products)
- SCD Type 2 (customers with history tracking)
- Fact & dimension modeling
- Partitioned fact table (date_key)
- Delta Lake merge operations

## Key Challenges Solved
- Handling duplicate records in streaming pipelines with stateful processing
- Designing reliable deduplication without losing valid updates
- Resolving Delta Lake merge conflicts (multiple source match issue)
- Implementing correct SCD Type 2 logic with versioning
- Managing schema evolution and null handling in streaming data

## Tech Stack
- PySpark
- Delta Lake
- SQL (Databricks)
- Medallion Architecture

## Project Structure
notebooks/ → Notebooks of each phase(setup) + Pipeline notebook (execute)   
databricks_notebooks/ → .dbc archive  
sample_data/ → test data

## How to Run
1. Import `.dbc` into Databricks workspace  
2. Upload sample data to DBFS (two phases: initial + update data)  
3. Execute notebooks in order:
   - Bronze ingestion  
   - Silver cleaning  
   - Gold modeling  
   - Fact table creation 

## Example Scenario
- Initial data contains customer records with missing values
- Second batch introduces updates (email/name changes)
- Pipeline correctly:
  - Updates SCD Type 1 fields
  - Creates new records for SCD Type 2 changes

## Output
- Cleaned dimension tables (`dim_customers`, `dim_products`)
- Historical tracking via SCD Type 2
- Analytics-ready `fact_orders` table

## Skills Demonstrated
- Data pipeline design
- Delta Lake merge operations
- SCD1 & SCD2 implementation
- Data cleaning & validation
- Partitioning & optimization
