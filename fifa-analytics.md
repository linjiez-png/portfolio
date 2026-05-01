---
layout: single
title: "FIFA Player Analytics and Machine Learning Pipeline"
permalink: /fifa-analytics/
---

<a href="/portfolio/assets/files/FIFA_Project_Report.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

---

## Overview

This project builds a scalable analytics and machine learning pipeline for FIFA player data from 2015–2022. The system processes structured player datasets, stores them in PostgreSQL, performs distributed analytics using PySpark, and trains machine learning models to predict player overall ratings.

The project demonstrates how big-data tools can be used to transform raw sports datasets into structured insights and predictive models.

---

## System Architecture

The pipeline includes:

- CSV ingestion from yearly FIFA datasets
- PySpark preprocessing and schema alignment
- PostgreSQL storage for structured querying
- Distributed analytics functions using Spark
- Machine learning models using Spark MLlib and PyTorch
- Cloud deployment on Google Cloud Dataproc

<img src="/portfolio/assets/images/fifa_pipeline.png" width="700">

---

## Data Engineering Pipeline

The raw dataset contains male and female FIFA player records across multiple years. The ingestion pipeline:

- Loads annual player CSV files
- Adds year and gender metadata
- Aligns schemas across datasets
- Converts date and skill-rating fields into usable numeric formats
- Creates a unique record ID for each player-year entry
- Stores the processed data in PostgreSQL

The final combined dataset contains approximately **144,000 player records**.

---

## Analytics Functions

Four PySpark analytics functions were implemented to support football business intelligence:

| Function | Purpose |
|---|---|
| Contract ending analysis | Identify clubs with many players nearing contract expiration |
| Average age ranking | Compare clubs by squad age profile |
| Nationality trend analysis | Find most common player nationalities by year |
| Nationality histogram | Count unique players by nationality with deduplication |

These functions use Spark transformations, aggregations, window functions, and deduplication logic to support scalable analysis.

---

## Machine Learning Models

The project compares four models for predicting player overall rating:

| Model | Platform | RMSE | MAE | R² |
|---|---|---:|---:|---:|
| Deep MLP | PyTorch | 1.47 | 1.16 | 0.95 |
| Random Forest | Spark MLlib | 2.04 | 1.55 | 0.91 |
| Shallow MLP | PyTorch | 2.16 | 1.60 | 0.90 |
| Elastic Net | Spark MLlib | 2.64 | 2.07 | 0.86 |

The best-performing model was the **Deep MLP**, which achieved **RMSE = 1.47** and **R² = 0.95**.

<img src="/portfolio/assets/images/fifa_results.png" width="650">

---

## Cloud Deployment

The pipeline was also deployed on Google Cloud Platform using Dataproc.

Key cloud components:

- Google Cloud Storage for dataset storage
- Dataproc Spark cluster for distributed processing
- GCS output paths for analytics results and model artifacts

This demonstrated that the pipeline could move from a local environment to a scalable cloud-based Spark workflow.

---

## My Contribution

I contributed mainly to the first stage of the project, focusing on data ingestion, preprocessing, database design, and early analytics implementation.

My work included:

- Built the PySpark ingestion pipeline for FIFA datasets from 2015–2022
- Added metadata fields such as year and gender
- Merged male and female annual datasets using schema-aligned union operations
- Cleaned and converted date fields, skill-rating fields, and categorical variables
- Designed the PostgreSQL schema and stored the processed dataset under the `fifa` schema
- Created a unique `record_id` primary key for reliable database indexing
- Implemented and tested several distributed analytics functions using PySpark
- Helped prepare the dataset for downstream machine learning tasks

I was not primarily responsible for the YouTube streaming analytics component.

---

## Key Insights

- Relational databases are well-suited for structured sports analytics datasets.
- PySpark enables scalable preprocessing and aggregation across many years of player data.
- Neural networks can capture nonlinear interactions among player attributes better than linear regression.
- Cloud deployment improves scalability but requires careful path, dependency, and storage management.

---

## Skills Demonstrated

- PySpark data processing
- PostgreSQL database design
- Distributed analytics
- Machine learning model comparison
- Cloud deployment with Google Dataproc
- Data cleaning and feature engineering

---

## Takeaway

This project demonstrates an end-to-end data analytics workflow, from raw dataset ingestion to database storage, distributed analytics, predictive modeling, and cloud deployment. It highlights practical experience with scalable data engineering and machine learning pipelines.
