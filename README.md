# Data Pipelines with Airflow
This project implements automated ETL pipelines using Apache Airflow for Sparkify, a music streaming company. The goal is to create dynamic, reusable, and easily monitored data pipelines that can process data from S3 to Amazon Redshift, ensuring high data quality for analysis.

## Structure
The project consists of four main operators:

1. Stage Operator: Loads JSON formatted files from S3 to Amazon Redshift
2. Fact Operator: Transforms data for fact tables
3. Dimension Operator: Transforms data for dimension tables
4. Data Quality Operator: Runs data quality checks

## Data Sources
- Song data: `s3://udacity-dend/song_data/` - JSON files containing metadata about songs and artists
- Log data: `s3://udacity-dend/log_data/` - JSON files containing log events from the Sparkify app

## Airflow DAG
![Airflow DAG](/dag.png)

## Airflow Operators

### Stage Operator
- Load JSON files from S3 to Redshift
- Creates and runs SQL COPY statements
- Allows loading timestamped files for backfills
- Configurable S3 and target table parameters

### Fact and Dimension Operators
- Utilize SQL helper class for data transformations
- Take SQL statements as input
- Allow specifying a target database and table
- Dimension Operator supports truncate-insert pattern
- Fact Operator supports append functionality

### Data Quality Operator
- Run SQL-based test cases against the data
- Compares test results with expected results
- Raises exceptions for failed tests
- Supports multiple test cases

## Dependencies 
- Apache Airflow
- Amazon Redshift
- Python ^3.9



