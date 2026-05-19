# Patient-Vital-Monitoring

Welcome to the **Patient-Vital-Monitoring Project** repository! 

This project demonstrates an End-to-End data pipeline solution, from generating streams of live data to delivering actionable medical insights. Designed as a portfolio project, it highlights industry best practices in data engineering, cloud architecture, and real-time analytics.

---

## Project Overview
This project implements a real-time, end-to-end streaming data pipeline built on Google Cloud Platform (GCP) to monitor and analyze patient vital signs dynamically. The primary objective is to process continuous streams of medical data (such as heart rate, oxygen saturation $SpO_2$, and body temperature) coming from healthcare simulators, aggregate them per patient every minute, and flag potential medical risks instantly.

The pipeline architecture follows the **Medallion Design Pattern**, which guarantees data quality and structured refinement across three distinct layers:
* **Bronze Layer (Raw Storage):** Ingests raw JSON data streamed from Google Cloud Pub/Sub and archives it directly into Google Cloud Storage (GCS) for historical auditing and backup purposes.
* **Silver Layer (Cleaned Data):** Validates the incoming records, filters out corrupted or incomplete readings, and standardizes the data structures.
* **Gold Layer (Aggregated Insights):** Utilizes fixed 60-second time windows to calculate vital metrics—such as average heart rate and critical risk levels—per patient. The final analytical outputs are seamlessly streamed into Google Cloud BigQuery for real-time dashboarding and medical alerts.

---

## Data Architecture

![Project Architecture](https://github.com/ayman23-ds/Patient-Vital-Monitoring-GCP/blob/2fa14b06f5c9f0efec85c773c668812bb2553535/reports/P_V_M.png)

1. **Bronze Layer:** Stores raw data as-is from the source systems. Data is ingested from a simulator that generates vital patient metrics.
2. **Silver Layer:** Includes data cleansing, validation, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer:** Houses business-ready, aggregated data required for analytical reporting, alerting, and visualization.

---

## Core Technologies Used
* **Infrastructure:** Google Cloud Platform (GCP)
* **Ingestion:** Google Cloud Pub/Sub
* **Data Processing & Orchestration:** Apache Beam & Google Cloud Dataflow
* **Storage & Data Lake:** Google Cloud Storage (GCS)
* **Data Warehousing & Analytics:** Google Cloud BigQuery
* **Programming Language:** Python 3
* **Visualization:** Power BI

---

## Data Pipeline Lifecycle: From Source to Visualization
The movement and transformation of patient data through the pipeline can be broken down into three main operational phases:

### 1. Data Generation (The Simulator)
* **Role:** Acts as the streaming data source, mimicking IoT medical devices attached to patients in a hospital environment.
* **Mechanism:** The Python-based simulator (`patient_vitals_simulator.py`) generates continuous, real-time healthcare metrics including heart rates, oxygen saturation ($SpO_2$), and body temperatures.
* **Ingestion:** Each generated message is instantly published as a JSON payload to a Google Cloud Pub/Sub Topic, ensuring high-throughput and decoupled asynchronous communication.

### 2. Stream Processing & Aggregation (Google Cloud Dataflow)
* **Role:** The analytical processing engine of the pipeline.
* **Mechanism:** Powered by Apache Beam, the Dataflow streaming job consumes live messages from the Pub/Sub subscription continuously.
* **Transformation Steps:**
    * **Bronze Processing:** Safely backs up the raw, unmodified JSON messages directly into Google Cloud Storage (GCS) buckets for auditing.
    * **Silver Processing:** Parses and validates the streaming data to ensure accurate schema adherence and data hygiene.
    * **Gold Processing:** Groups the streaming records into fixed 1-minute time windows per patient. It computes rolling averages for vitals and dynamically flags the highest risk category (`max_risk_level`). The processed insights are immediately streamed into Google Cloud BigQuery tables.

### 3. Business Intelligence & Visualization (Power BI)
* **Role:** The presentation layer for medical personnel and stakeholders.
* **Mechanism:** Power BI connects directly to the Google Cloud BigQuery Gold dataset using DirectQuery modes for near real-time updates.
* **Value Delivered:** Translates complex tabular data into intuitive, visual health dashboards. Doctors and nurse stations can monitor live patient health trends, track average vital metrics across wards, and receive immediate visual cues for patients flagged with "High" or "Moderate" risk levels, driving faster, life-saving clinical decisions.
![Project Architecture](https://github.com/ayman23-ds/Patient-Vital-Monitoring-GCP/blob/305ff51ab46352ba1f1a3730cedaff3e1a2d0712/reports/dashboard.png)
---
## About Me

I am a **Data Engineer** with a strong interest in building modern data platforms and scalable data pipelines.

I am currently pursuing a **Master’s degree in Machine Learning and Deep Learning at the University of Pavia, Italy**. My academic and technical focus includes:

* Data Engineering & Data Warehousing
* ETL / ELT Pipelines
* Big Data Technologies
* Machine Learning & Deep Learning

I am passionate about designing efficient data architectures that enable advanced analytics and intelligent systems.

## Connect With Me

🔗 [LinkedIn Profile](https://www.linkedin.com/in/ahmed-ayman-b69219354/)

