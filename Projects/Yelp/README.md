# Data Engineering Project - Yelp

## Project Objective
The purpose of this project is to demostrate various skills associaetd with data engineering project. In particular developing ETL pipelines using 

## Yelp Dataset 
Description: The Yelp dataset is a subset of our businesses, reviews, and user data for use in personal, educational, and academic purposes. Available as JSON files, use it to teach students about databases, to learn NLP, or for sample production data while you learn how to make mobile apps.
<img src="images/yelp_dataset_desc.png"/>

Yelp Dataset JSON hierarchy (9.3GB)
* yelp_academic_dataset_business.json (120MB)
* yelp_academic_dataset_checkin.json (287MB)
* yelp_academic_dataset_review.json (534GB)
* yelp_academic_dataset_tip.json (180MB)
* yelp_academic_dataset_user.json (336GB)

Yelp Dataset Photos (10GB)

Downloading the JSON file

```bash
wget https://yelp-dataset.s3.amazonaws.com/YDC22/yelp_dataset.tgz?AWSAccessKeyId=AKIAJ3CYHOIAD6T2PGKA&Signature=oIxPAtaKM6Y2hhQ%2F9Mwyp%2FRlVA8%3D&Expires=1678273296
```
Downloading the Photos file
```bashs
wget https://yelp-dataset.s3.amazonaws.com/YDC22/yelp_dataset.tgz?AWSAccessKeyId=AKIAJ3CYHOIAD6T2PGKA&Signature=oIxPAtaKM6Y2hhQ%2F9Mwyp%2FRlVA8%3D&Expires=1678273296
```

## Architecture diagram


## Technologies
* Google Cloud Platform (GCP)
  * Google Cloud Storage (GCS): Data Lake
  * BigQuery: Data Warehouse
  * Google Cloud SDK
* Docker: Containerization
  * Docker-Compose: define and run multi-container Docker application
  * Postgre Database
  * pgAdmin: web-based GUI tool to interactive with Postgre Database
* Terraform: Infrastructure-as-Code (IaC)
* SQL: Data Analysis & Exploration
* Python3: Programming language (via Anaconda)
* Airflow: Workflow Orchestration
* dbt: Data Transformation
* Spark: Distributed Processing
* Kafka: Streaming
* GitHub: Version Control
* PowerBI: Business intelligence & Visualization

## Workflow
1. Download Yelp JSON & Photos dataset
2. Setting up infrastucture on GCP via Terraform
a. Google Cloud Storage (GCS)
b. Bigquery
c. VM
3. Prepare and configure the VM environment for the project
4. Setting up microservice via Docker
a. Postgre Database & pgAdmin
b. Airflow 
c. dbt
5. Data Modeling
6. Data Ingestion
a. ETL with Postgre DB
b. ETL with GCS & Bigquery via Airflow
1. Exploratory Data Analysis via SQL
2. Data Transformation via dbt 
3. Batch processing via Spark
a. Spark Dataframe
b. Spark SQL
c. RDDs
1.  Streaming processing via Kafka
a. Kafka Producer
b. Kafka Consumer
c. Streaming Analytcis
1.  Visualization via PowerBI

## Conclusion
