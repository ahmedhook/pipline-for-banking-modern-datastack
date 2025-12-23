📌 Project Overview

This project demonstrates an end-to-end modern data stack pipeline for a Banking domain
We simulate customer  account  and transaction data stream changes in real time  transform them into analytics-ready models and visualize insights best practices of CI/CD and data warehousing.


Architecture

<img width="781" height="495" alt="Screenshot From 2025-12-10 16-04-07" src="https://github.com/user-attachments/assets/ab23fe27-3ba2-42b2-a16b-3bfb3610d8d0" />

A7MED _EZZAT, [12/22/25 10:20 PM]
https://www.linkedin.com/posts/ahmed-ezzat-a6b84b277_%D9%81%D9%8A-project-%D8%AF%D9%87-%D8%B9%D9%85%D9%84%D8%AA-pipline-%D9%83%D8%A7%D9%85%D9%84-%D9%8A%D8%AD%D8%A7%D9%83%D9%8A-%D9%86%D8%B8%D8%A7%D9%85-activity-7408964175860899840-jIML?utm_source=share&utm_medium=member_desktop&rcm=ACoAAEOUJDMBlY5ptydLeVm4NRQvymARdtCts0A

A7MED _EZZAT, [12/23/25 2:11 AM]
# Data Engineering Pipeline Project

## 📌 Pipeline Flow

1. Data generator by Faker simulates customer accounts and transactions
2. Debezium + Kafka stream changes (CDC) into MinIO S3 storage
3. Airflow orchestrates data ingestion and snapshots into Snowflake
4. Snowflake cloud data warehouse (Bronze, Silver, Gold layers)
5. dbt transformations build staging, marts, and snapshots (SCD Type 2)
6. CI/CD with GitHub Actions for testing and deployment

---

## 🛠️ Tech Stack

1. PostgreSQL – Source OLTP system
2. Python (Faker) – Data simulation
3. Debezium + Apache Kafka – Real-time streaming and CDC
4. Apache Airflow – Orchestration and DAG scheduling
5. MinIO – S3-compatible storage
6. Snowflake – Cloud data warehouse
7. dbt – Transformations, testing, and snapshots (SCD Type 2)
8. Docker Compose – Containerized setup
9. Git / GitHub Actions – CI/CD workflows

---

## ✨ Key Features

1. PostgreSQL OLTP source relational database with ACID guarantees (customer account transactions)
2. Simulated banking system with customer accounts and transactions
3. Change Data Capture (CDC) using Kafka + Debezium from PostgreSQL
4. Raw staging dimension and fact models using dbt
5. Snapshot history tracking (Slowly Changing Dimensions)
6. Automated pipeline orchestration using Apache Airflow
7. CI/CD pipeline using GitHub Actions

---

## 🚀 Step-by-Step Implementation

### 1️⃣ Data Simulation
- Generated synthetic banking data (customers, accounts, transactions) using Faker
- Inserted data into PostgreSQL (OLTP) so the system behaves like a real transactional database (ACID, constraints)
- Controlled data generation via config.yaml

### 2️⃣ Kafka + Debezium CDC
- Set up Kafka Connect and Debezium to capture changes from PostgreSQL
- Streamed CDC events into MinIO

### 3️⃣ Airflow Orchestration
- Built DAGs to:
  - Ingest MinIO data into Snowflake (Bronze layer)
  - Schedule snapshots and incremental loads

### 4️⃣ Snowflake Warehouse
- Organized data into Bronze → Silver → Gold layers
- Created staging schemas for ingestion

### 5️⃣ dbt Transformations
- Staging models: cleaned source data
- Dimension and fact models: built marts
- Snapshots: tracked history of accounts and customers

### 6️⃣ CI/CD with GitHub Actions
- ci.yml: dbt compile and run tests
- cd.yml: deploy Airflow DAGs and dbt models
