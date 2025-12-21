📌 Project Overview

This project demonstrates an end-to-end modern data stack pipeline for a Banking domain
We simulate customer  account  and transaction data stream changes in real time  transform them into analytics-ready models and visualize insights best practices of CI/CD and data warehousing.


Architecture

<img width="781" height="495" alt="Screenshot From 2025-12-10 16-04-07" src="https://github.com/user-attachments/assets/ab23fe27-3ba2-42b2-a16b-3bfb3610d8d0" />

Pipeline Flow:

1- data generator by faker simulate customers accounts and transavcations 
2- debzium + kafka stream change (CDC) into Minio s3 storge 
3- airflow orchestrat DATA ingestion  and snapshots into snowflake
4- snowflake cloud data warehouse (bronze silver gold )
5- dbt  transformation build marts and staging and snapshots  SCD type-2
6- CI/CD with github actions and tests and deployment

Tech Stack

1- postgres : source oltp system
2- python faker : data simulation
3- debzium + apache kafka : Real time streaming and CDC
4- air flow : orchestration and dag scheduling
5- minio : s3 storge 
6- snowflake cloud data warehouse
7- DBT : transformtion and testin and snapshots SCD type-2
8- docker compose : containerized setup
9- git/github actions : CI/CD Workflows



Key features

1- postgressql OLTP : source relational database with ASID guarantees (customer account transaction)
2- simulated banking system : customers accounts and transavcations 
3- change data capture CDC kafka + debezium capturing Postgres 
4- Raw Staging dimension/Fact in models DBT
5- Snapshot history tracking (slowly changing dimensions)
6- Automated pipline orchestration  using Airflow
7- CI/CD pipline using github action 


Step-by-Step Implementation
1- Data Simulation
Generated synthetic banking data (customers, accounts, transactions) using Faker.
Inserted data into PostgreSQL (OLTP) so the system behaves like a real transactional database (ACID, constraints).
Controlled generation via config.yaml

2- Kafka + Debezium CDC
Set up Kafka Connect & Debezium to capture changes from Postgres.
Streamed CDC events into MinIO.

3- Airflow Orchestration
Built DAGs to:
Ingest MinIO data > Snowflake (Bronze)
Schedule snapshots & incremental loads

4- Snowflake Warehouse
Organized into Bronze > Silver > Gold layers
Created staging schemas for ingestion.

5- DBT Transformations
Staging models > cleaned source data
Dimension & fact models > built marts
Snapshots > tracked history of accounts & customers

6- CI/CD with GitHub Actions
ci.yml  dbt compile, run tests
cd.yml Deploy DAGS DBT models 

