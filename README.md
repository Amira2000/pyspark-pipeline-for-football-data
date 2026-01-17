# PySpark Football Data Pipeline on Databricks

##  Project Overview

This project implements an **end-to-end data engineering pipeline** using **PySpark on Databricks**, following the **Medallion Architecture (Raw → Bronze → Silver → Gold)**.

The pipeline ingests raw football match data (CSV files), progressively cleans and enriches it, computes advanced team-level statistics, and produces analytics-ready datasets.
The workflow is fully automated using **Databricks Jobs orchestration**.

---

## Project Goals

* Build a scalable PySpark data pipeline
* Apply Medallion Architecture best practices
* Use Delta Lake for reliable storage
* Compute team performance metrics
* Automate the pipeline execution

---

## Architecture

**Medallion Architecture:**

* **Raw**: Raw CSV files stored in Databricks Volumes
* **Bronze**: Raw ingestion into Delta tables
* **Silver**: Cleaned, standardized, and enriched data
* **Gold**: Aggregated team statistics and rankings

---

##  Notebooks Description

###  Raw → Bronze (`01_Raw_To_Bronze_Transformations`)

* Reads multiple raw CSV files
* Merges all seasons into a single Delta table
* Preserves raw structure for traceability

###  Bronze → Silver (`02_Bronze_To_Silver_Transformations`)

* Cleans and standardizes the data
* Casts columns to correct data types
* Renames columns for clarity
* Writes partitioned Silver Delta tables

### Silver → Gold (`03_Silver_To_Gold_Transformations`)

* Computes home and away statistics
* Aggregates full season team metrics
* Calculates KPIs:

  * Goals scored / conceded
  * Wins, losses, draws
  * Goal differential
  * Win percentage
* Ranks teams per season using window functions

### Data Analysis (`04_Data_Analysis`)

* Identifies champions per season
* Finds teams with the most titles
* Determines best attacking teams

### Orchestration (`05_Orchestration`)

* Automates notebook execution using Databricks Jobs
* Ensures correct task dependencies
* Simulates a production-ready pipeline

* The orchestration logic and execution flow are documented here:
- [Pipeline Orchestration](orchestration/orchestration.md)

---

## ⚙️ Tech Stack

* Apache Spark (PySpark)
* Databricks
* Delta Lake
* Databricks Jobs (Orchestration)

---

##  Key Learnings

* Distributed data processing with Spark
* Production-grade data pipeline design
* Delta Lake and partitioning
* Data aggregation and window functions
* Workflow automation

---

##  Author

**Amira Ouaked**
Data Analyst/Engineer 
