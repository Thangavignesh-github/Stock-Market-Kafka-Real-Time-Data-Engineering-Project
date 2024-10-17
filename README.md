
# Stock Market Kafka Real-Time Data Engineering Project

## Introduction
This project demonstrates the end-to-end data engineering process on real-time stock market data using Apache Kafka, Zookeeper, and various AWS services. The goal is to build a real-time data pipeline that simulates stock market data streaming, processes the data, and makes it available for querying and analysis.

## Architecture Overview
- **Producer**: A Python-based stock market simulation app streams data using Apache Kafka.
- **Broker**: Kafka on AWS EC2 handles the message brokering.
- **Consumer**: The data is consumed by AWS services and processed for storage and querying.



## Technologies Used
- **Programming Language**: Python
- **Messaging System**: Apache Kafka
- **Coordination Service**: Zookeeper
- **AWS Services**:
  - **S3**: Stores stock market data.
  - **Glue Crawler**: Extracts metadata and catalogs data.
  - **Glue Data Catalog**: Maintains a schema of the data.
  - **Athena**: Allows querying of the data using SQL.

## Workflow
1. **Data Simulation**: A Python app simulates real-time stock market data using the dataset and produces messages to a Kafka topic.
2. **Data Streaming**: The stock data is streamed into Kafka, which is hosted on an AWS EC2 instance.
3. **Data Consumption**: A consumer service on AWS consumes the data from Kafka.
4. **Data Storage**: The consumer stores the data into an S3 bucket.
5. **Data Cataloging**: AWS Glue Crawler runs periodically to catalog the new data in S3.
6. **Data Querying**: AWS Athena is used to query the stock market data stored in S3.

## Prerequisites
- **Python 3.x**
- **Apache Kafka** and **Zookeeper** (both locally or on AWS EC2)
- **AWS Account** for S3, Glue, and Athena services

## Setup

### Kafka & Zookeeper Setup
1. **Download Kafka and Zookeeper**:
   ```bash
   wget https://downloads.apache.org/kafka/2.13-2.7.0/kafka_2.13-2.7.0.tgz
   tar -xzf kafka_2.13-2.7.0.tgz
   cd kafka_2.13-2.7.0
   ```

2. **Start Zookeeper**:
   ```bash
   bin/zookeeper-server-start.sh config/zookeeper.properties
   ```

3. **Start Kafka Broker**:
   ```bash
   bin/kafka-server-start.sh config/server.properties
   ```

### Python Producer Setup
1. **Install Dependencies**:
   ```bash
   pip install kafka-python boto3
   ```

### AWS S3 Setup
1. **Create an S3 Bucket** to store the stock market data.
2. **Configure AWS CLI** with your credentials:
   ```bash
   aws configure
   ```

### AWS Glue Crawler Setup
1. **Create a Glue Crawler** that points to the S3 bucket and catalog the data.
2. **Run the Crawler** to update the Glue Data Catalog.

### AWS Athena Setup
1. **Create a Table** in Athena by pointing to the S3 bucket and Glue Data Catalog.
2. **Run Queries** using SQL to analyze the stock market data.

## How to Run
1. Start **Zookeeper** and **Kafka Broker**.
2. Run the **Python producer script** to simulate stock market data.
3. Check the **AWS S3 bucket** for incoming data.
4. Use **AWS Glue Crawler** to catalog the data.
5. Query the data in **Athena**.

## Future Enhancements
- Add more complex transformations to the data pipeline.
- Implement real-time monitoring using AWS CloudWatch.
- Optimize Kafka configuration for larger-scale data.

## Conclusion
This project demonstrates how to set up a real-time stock market data pipeline using Apache Kafka, Zookeeper, and AWS services. The data is produced, stored, and made queryable, enabling analysis and insights in real time.
