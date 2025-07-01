# 🎧 Spotify End-to-End Data Engineering Project

A complete data engineering pipeline that extracts Spotify music data using the Spotify Web API, processes it using AWS cloud services, and enables SQL-based analysis via Athena. This project showcases the design and deployment of a scalable, cloud-native ETL pipeline for real-world music data.

---

## 🧱 Architecture Overview

![Spotify Data Pipeline Architecture](https://github.com/amitsingh79/Spotify-end-to-end-Data-Engineering-Project/blob/main/spotify%20data%20pipeline%20diagram.png)

---

## 🎯 Objectives

- Build a fully automated ETL pipeline
- Use AWS services to process, query, and store Spotify data
- Perform data analysis using Athena
- Create a robust foundation for future analytics/dashboard integration

---

## 🧰 Tech Stack

- **Languages**: Python, SQL  
- **Data Source**: Spotify Web API  
- **AWS Services**:  
  - S3 – Storage for raw and processed data  
  - Lambda – Serverless orchestration  
  - Glue – ETL and schema inference  
  - Athena – SQL-based querying  
  - IAM – Role-based access control  
- **Data Formats**: JSON → Parquet  
- **(Optional)**: Apache Airflow, QuickSight for scheduling/visualization  

---

## 🔁 End-to-End Workflow

1. **Extraction**  
   - Spotify API called using Python scripts  
   - Data pulled: playlists, tracks, audio features, artist metadata  
   - Stored in **raw JSON** format in S3 bucket:  
     `s3://spotify-etl-project-amit-singh/raw_data/`

2. **Transformation**  
   - AWS Glue crawlers infer schema  
   - Glue jobs convert JSON → Parquet (optimized for Athena)  
   - Data stored in:  
     `s3://spotify-etl-project-amit-singh/processed_data/`

3. **Loading & Querying**  
   - AWS Athena connects to S3 (via Glue Data Catalog)  
   - SQL queries performed for analysis (see examples below)  
   - Result sets downloadable or connected to dashboards  

---

## 🧾 Repository Structure

📁 Spotify-end-to-end-Data-Engineering-Project/
├── scripts/ # Python ETL scripts
│ └── spotify_api_to_s3.py
│ └── glue_job_script.py
├── lambda_function/ # (Optional) AWS Lambda function
├── athena_queries/ # SQL queries for table creation & analysis
├── screenshots/ # Diagram or output screenshots
├── requirements.txt # Python dependencies
└── README.md # This file


---

## 🚀 Getting Started

### ✅ Prerequisites
- AWS Account with IAM permissions
- Spotify Developer Account + App (to get API credentials)

### ⚙️ Setup Instructions
1. **Clone the repo**


## 🚀 Getting Started

### ✅ Prerequisites
- AWS Account with IAM permissions
- Spotify Developer Account + App (to get API credentials)

### ⚙️ Setup Instructions
1. **Clone the repo**
   ```bash
   git clone https://github.com/amitsingh79/Spotify-end-to-end-Data-Engineering-Project.git
   cd Spotify-end-to-end-Data-Engineering-Project
2.
```
  pip install -r requirements.txt
```
3.Install dependencies
```
  pip install -r requirements.txt
```
4. Configure Spotify credentials In credentials.cfg (add your client_id, client_secret, and redirect_uri)

-Run the ETL script
```
  python scripts/spotify_api_to_s3.py
```
5.Set up Glue jobs and Athena tables

6.Use Glue to convert JSON → Parquet

7.Create external tables in Athena using athena_queries/create_tables.sql

8.Analyze data with custom SQL

9.📊 Sample Athena Query
sql
```
-- Top 10 Artists by Track Count
SELECT artist_name, COUNT(*) AS track_count
FROM spotify_tracks
GROUP BY artist_name
ORDER BY track_count DESC
LIMIT 10;
```

##🚧 Future Enhancements

-Add Apache Airflow for orchestration

-Integrate with Amazon QuickSight for BI dashboards

-Add support for real-time streaming using Kafka + Spark

-Dockerize the ETL scripts for containerized execution

