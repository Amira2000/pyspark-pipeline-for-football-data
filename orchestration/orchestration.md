# Pipeline Orchestration

##  Goal

The purpose of orchestration is to automate the execution of the data pipeline
and ensure that each transformation layer is executed in the correct order.

This pipeline is orchestrated using **Databricks Jobs**, simulating a
production-grade workflow.

---

##  Execution Flow

The pipeline follows a strict dependency order:

1. **Raw → Bronze**

   * Notebook: `01_Raw_To_Bronze_Transformations.ipynb`
   * Ingests raw CSV files and stores them as Delta tables

2. **Bronze → Silver**

   * Notebook: `02_Bronze_To_Silver_Transformations.ipynb`
   * Cleans, standardizes, and enriches the data

3. **Silver → Gold**

   * Notebook: `03_Silver_To_Gold_Transformations.ipynb`
   * Aggregates team statistics and computes KPIs

4. **Data Analysis**

   * Notebook: `04_Data_Analysis.ipynb`
   * Uses Gold-layer data to answer analytical questions

Each step depends on the successful completion of the previous one.

---

##  Scheduling Strategy

In a production environment, this pipeline can be scheduled to:

* Run daily (e.g. after new data ingestion)
* Be triggered manually for backfills
* Retry automatically in case of failure

---

##  Benefits of This Orchestration Design

* Guarantees data consistency
* Avoids partial or corrupted outputs
* Enables automation and scalability
* Reflects real-world data engineering workflows

