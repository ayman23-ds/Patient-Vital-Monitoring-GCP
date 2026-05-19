# Patient-Vital-Monitoring
Welcome to the **Patient-Vital-Monitoring Project** repository
This project demonstrates an End to End data pipline solution,from generating stram of data  to generaing actionable insights. Designed as portofolio project highlights industry best practices in data engineering and analytics

---

## Project Overview
This project implements a real-time, end-to-end streaming data pipeline built on Google Cloud Platform (GCP) to monitor and analyze patient vital signs dynamically. The primary objective is to process continuous streams of medical data (such as heart rate, oxygen saturation $SpO_2$, and body temperature) coming from healthcare simulators, aggregate them per patient every minute, and flag potential medical risks instantly.The pipeline architecture follows the Medallion Design Pattern, which guarantees data quality and structured refinement across three distinct layers:
- Bronze Layer (Raw Storage): Ingests raw JSON data streamed from Google Cloud Pub/Sub and archives it directly into Google Cloud Storage (GCS) for historical auditing and backup purposes.
- Silver Layer (Cleaned Data): Validates the incoming records, filters out corrupted or incomplete readings, and standardizes the data structures.
- Gold Layer (Aggregated Insights): Utilizes fixed 60-second time windows to calculate vital metrics—such as average heart rate and critical risk levels—per patient. The final analytical outputs are seamlessly streamed into   Google Cloud BigQuery for real-time dashboarding and medical alerts.
---

## Data Architecture

![image alt](https://github.com/ayman23-ds/Patient-Vital-Monitoring-GCP/blob/2fa14b06f5c9f0efec85c773c668812bb2553535/reports/P_V_M.png)

1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from simulator that generate specific type of data.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.


  
## Core Technologies Used:
- Infrastructure: Google Cloud Platform (GCP)
- Ingestion: Google Cloud Pub/Sub
- Data rocessing & Orchestration: Apache Beam & Google Cloud Dataflow
- Storage & Data Lake: Google Cloud Storage (GCS)
- Data Warehousing & Analytics: Google Cloud BigQuery
- Programming Language: Python 3
