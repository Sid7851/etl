Hi,

Please find the video link here: https://drive.google.com/file/d/160Nd0bEkDBcC0W-G-gOxEUKnqv8OkUx9/view?usp=drive_link

I've also created a README file to guide you through my approach to the ETL challenge.

ETL Process Overview
Data Ingestion:
* Created a Google Cloud Storage (GCS) bucket to store the raw data files.
* Set up a BigQuery dataset (raw_data) and loaded the files as external tables for quick access.

Staging Layer:
* Created a staging dataset (staging) in BigQuery.
* Transferred raw data from raw_data to staging.
* Performed Data Quality Checks, including:
  * NULL value validation
  * Primary Key Uniqueness
  * Foreign Key Integrity
* Normalized the dimension (hier_prod) table by creating separate tables: dept, category, subcategory, style, and sku.
* Created the final staging table for fact_transactions.

Refined Layer:
* Built the mview_weekly_sales table for aggregated sales metrics.
* Implemented an incremental update query to dynamically calculate totals for partially loaded data.

Automation Consideration
Due to the unavailability of Cloud Composer, I executed these steps manually. However, in a production environment, we can leverage Cloud Composer (Airflow) to automate the entire pipeline, eliminating the need for manual execution.
