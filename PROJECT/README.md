# Retail Sales Data Engineering & Analytics Pipeline

## Project Overview

This project builds an end-to-end retail data pipeline that automatically processes raw sales data and generates business analytics.

The pipeline uses AWS services for data ingestion and transformation, and Databricks for analytics and business insights.

Whenever a new retail CSV file is uploaded, the system automatically processes the data and updates analytics.

---

# Project Architecture

Raw Data → AWS S3 → Lambda Trigger → AWS Glue ETL → Cleaned Data in S3 → Databricks → Business Analytics Dashboard

Workflow:

1. Raw retail data is uploaded to an AWS S3 bucket.
2. S3 event triggers an AWS Lambda function.
3. Lambda automatically starts an AWS Glue ETL job.
4. AWS Glue cleans and transforms the raw data.
5. Processed data is stored back in S3.
6. Databricks connects to S3 and reads the processed dataset.
7. Business analytics and KPIs are generated using PySpark and SQL.

---

# Technologies Used

## Cloud
• AWS S3  
• AWS Glue  
• AWS Lambda  

## Data Processing
• Apache Spark  
• PySpark  

## Analytics
• Databricks  
• SQL  

## Version Control
• GitHub  

---

# Business Requirements

The stakeholders wanted insights on the following metrics:

1. Total number of customers
2. Total number of orders
3. Total sales revenue
4. Total profit generated
5. Top sales by country
6. Most profitable region and country
7. Top product categories by sales
8. Top 10 sub-category products
9. Most ordered product by quantity
10. Top customers based on sales and city

The dashboard refreshes based on weekly and monthly analysis.

---

# AWS Pipeline Implementation

## 1. Data Storage (AWS S3)

Raw retail data is uploaded into an S3 bucket.

Example structure:

s3://superstore-raw-data-input/superstore1.csv
s3://superstore-raw-data-input/superstore2.csv

---

## 2. Automatic Trigger (AWS Lambda)

Whenever a new CSV file is uploaded into S3, an AWS Lambda function is triggered automatically.

Lambda code starts the AWS Glue job.

---

## 3. Data Processing (AWS Glue)

AWS Glue performs ETL operations:

• Reads raw CSV data
• Cleans malformed records
• Fixes column formatting issues
• Transforms data into structured format
• Saves processed data back to S3

Output location:

s3://superstore-processed-data/output/

---

## 4. Data Analytics (Databricks)

Databricks connects to the S3 processed data.

Using PySpark and SQL:

• Data is analyzed
• KPIs are generated
• Business insights are calculated

---

## 5. Architecture Diagram

       +-------------+
       |   Raw CSV   |
       +-------------+
              |
              v
       +-------------+
       |   AWS S3    |
       +-------------+
              |
              v
       +-------------+
       | AWS Lambda  |
       +-------------+
              |
              v
       +-------------+
       | AWS Glue ETL|
       +-------------+
              |
              v
    +--------------------+
    | Processed Data S3  |
    +--------------------+
              |
              v
       +-------------+
       | Databricks  |
       +-------------+
              |
              v
      Business Analytics
