# Realtime Data Architecture: Hiring Platform

## Table of Contents
- [Introduction](#introduction)
- [System Architecture](#system-architecture)
- [Technologies](#technologies)
- [Project Files](#project-files)
- [Getting Started](#getting-started)
- [Watch the Video Tutorial](#watch-the-video-tutorial)

## Introduction

This project serves as a comprehensive guide to building an end-to-end data engineering pipeline. It covers each stage from data ingestion to processing and finally to multiple storages, utilizing a robust tech stack that includes Apache Airflow, Python, Apache Kafka, Apache Zookeeper, Apache Spark, Cassandra, MySQL, and Grafana. Everything is containerized using Docker for ease of deployment and scalability.

## System Architecture

![System Architecture](https://github.com/MarcusLe02/realtime-pipeline-hiring-platform/blob/master/data-engineering-architecture.png)

The project is designed with the following components:

- **Data Source**: `randomuser.me` API provides mock user data.
- **Apache Airflow**: Responsible for orchestrating the pipeline and storing fetched data in a PostgreSQL database.
- **Apache Kafka and Zookeeper**: Used for streaming data from PostgreSQL to the processing engine.
- **Apache Spark**: For data processing with its master and worker nodes.
- **Cassandra**: Where the raw user and tracking data will be stored.
- **MySQL**: Stored transformed and aggregated tracking data for analysis.
- **Grafana**: Create real-time dashboards, pulling data directly from MySQL.

## Technologies

- Apache Airflow
- Python
- Apache Kafka
- Apache Zookeeper
- Apache Spark
- Cassandra
- MySQL
- Grafana
- Docker

## Project Files

- [docker-compose.yml](https://github.com/MarcusLe02/realtime-pipeline-hiring-platform/blob/master/docker-compose.yml): Configure containers for each technology
- dags/kafka-stream.py: Streams data from the API to Kafka
- spark_stream.py: Processes data from Kafka and stores it in Cassandra
- faking_log.py: Generates sample interaction log data for testing
- spark_cdc.py: Captures changes in Cassandra, transforms and pushes them to MySQL

## Getting Started

1. Clone the repository:
    ```bash
    git clone https://github.com/MarcusLe02/realtime-pipeline-hiring-platform.git
    ```

2. Navigate to the project directory:
    ```bash
    cd realtime-pipeline-hiring-platform
    ```

3. Run Docker Compose to spin up the services:
    ```bash
    docker-compose up -d
    ```
