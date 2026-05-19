# Earth-Quake-Data-Bricks-Project

## 📌 Overview

This project demonstrates a data engineering pipeline built on Databricks (Free Edition) using Unity Catalog, Delta Live Tables (DLT), and Databricks Asset Bundles.
The pipeline ingests data from a REST API (Earthquake dataset), processes it through Bronze → Silver → Gold layers, and delivers insights via dashboards.
It also showcases automation with Databricks Jobs and deployment with Asset Bundles from Dev → Prod environments.

## 🎯 Objectives

 - Build a Medallion Architecture pipeline (Bronze, Silver, Gold layers).
 - Ingest REST API JSON data into Databricks Volumes.
 - Transform raw JSON into structured Delta Tables using DLT pipelines.
 - Automate ingestion and transformation with Databricks Jobs.
 - Deploy resources across environments using Databricks Asset Bundles.
 - Visualize insights with Databricks Dashboards.

## 🏗️ Architecture

The project follows the Medallion Architecture:

- **Bronze Layer**: Raw ingestion from REST API stored as JSON in Volumes
- **Silver Layer**:Cleaned & structured Delta Tables using DLT pipelines
- **Gold Layer**: (Optional) Aggregated business-ready tables for analytics
- **Dashboard**: Visual insights built on top of Silver/Gold tables
- **Jobs**: 	Automated orchestration of ingestion, transformation & dashboard refresh
- **Asset Bundles	Deployment**:  from Dev → Prod environments

## ⚙️ Tech Stack
 - Databricks Free Edition
 - Unity Catalog (Schemas, Tables, Views)
 - Delta Live Tables (DLT)
 - Databricks Jobs
 - Databricks Asset Bundles
 - GitHub (Version Control)
 - REST API (Earthquake Data)

## 📂 Project Structure

```
Earth-Quake-Data-Bricks-Project/
├── README.md                                         # This file
├── .github                             
│
└── EarthQuake_Bundle/                                        # Main databricks project bundle
    ├── databricks.yml                                        # databricks project configuration
    ├── pyproject.toml                                        # Python dependencies
    │
    ├── resources/                               
    │   ├── EarthQuake_Bundle_etl.pipeline.yml                # DLT pipeline to transform data
    │   ├── earthquake_dashboard.yml                          # Visual insights dashoard config
    │   └── earthquake_job.job.yml                            # Automates pipeline job refresh configs 
    │    
    ├── src/                                                  # ELT required program code
    │   ├── Notebooks/                                        # Bronze Layer
    |   |     └── Ingestion.ipynb
    |   |
    |   ├── Dashboards/
    |   |    └── EarthQuake_Dashboard_Prod.lvdash.json        # Visual insights on earthquake data
    |   |
    |   └── DLT_Pipeline/ Standardization/transformation      # Silver Layer
    |         └── data_cleaning.py                            # Data cleaning/transforming the data
    │         
    │
    └──  tests/                                               # Data quality tests
          └── sample_tests.py

```

## 🔄 Workflow

1. Data Ingestion (Bronze Layer)
   - REST API (Earthquake dataset) → JSON files stored in Databricks Volumes.
   - Parameterized notebooks ensure environment flexibility (Dev/Prod).
   
2. Transformation (Silver Layer)
   - Delta Live Tables pipeline parses JSON into structured Delta Tables.
   - Extracts key fields: magnitude, location, time, coordinates, depth, etc.
   - Cleans & normalizes schema using PySpark.

3. (Optional) Gold Layer
   - Aggregated tables for advanced analytics (e.g., earthquake trends by region).

4. Visualization
   - Databricks Dashboard built on Silver/Gold tables.
   - Displays earthquake statistics, trends, and geospatial insights.

5. Automation
   - Databricks Job orchestrates:
      - Notebook execution (ingestion)
      - DLT pipeline run (transformation)
      - Dashboard refresh

6. Deployment
   - Databricks Asset Bundles used to deploy resources from Dev → Prod.
   - GitHub integration ensures version control and CI/CD readiness.

## 🚀 Getting Started

### Prerequisites
  - Databricks Free Edition account
  - GitHub account (for version control & asset bundles)
  - Basic knowledge of PySpark and Databricks UI
  - REST API endpoint (Earthquake dataset from USGS)
  - Python 3.12+

### How to Run

1. Create a project workspace in DataBricks
2. Create a Catalog for your environment (For development, For production).
3. Create a Git folder```<repository-url>``` (with a project name), with the git account url to link the project under dev branch
4. Under created Git folder, Create a asset bundle(with bundle name), by selecting a 'default Python' template
5. Inside the bundle's src folder, create Schemas:
   - bronze → raw ingestion (ingestion_to_bronze.ipynb that fetch earthquake json data)
   - silver → Read JSON files from the Bronze layer → Parse and normalize fields → Write structured Delta Tables into the silver schema
   - gold → optional aggregated tables
6. Create a Databricks Dashboard to visualize the transformed data according to bussiness use case.
7. Create resource configuration for job and etl_pipeline yml files under resources to run the job
8. Create a Automation of job deployment upon merging of dev branch into main.
   - Create .githun/workflows, with ci.yml configuration to run the job automatically.

## 📚 Additional Resources

- **Databricks Documentation**: https://docs.databricks.com/
- **Earthquake REST API (USGS)**: https://earthquake.usgs.gov/fdsnws/event/1/

## 📝 License

This project is part of a data engineering portfolio demonstration.

## 👤 Author

**Project**: Earthquake Data Bricks Data Engineering Project 
**Technologies**: DataBricks, Rest API, Delta Lake,  Python  
**Architecture**: Medallion (Bronze → Silver → Gold)
