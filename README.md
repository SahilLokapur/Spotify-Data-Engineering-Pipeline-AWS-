# Spotify-Data-Engineering-Pipeline-AWS-
Spotify Data Engineering Pipeline (AWS)

This project outlines a scalable, serverless data engineering pipeline built entirely on Amazon Web Services (AWS) to process and analyze raw Spotify dataset files (artists, tracks, albums). The goal was to transform disparate CSV files into an optimized, easily queryable format for business intelligence and data visualization.

Architecture and Technologies
Data Ingestion & Storage (AWS S3): Raw data is manually uploaded as CSV files to a designated S3 bucket (Landing Zone), serving as the primary source of truth.

ETL Processing (AWS Glue): An AWS Glue ETL job is configured to read the raw CSV data. The job performs essential data integration steps, including inner joining the artist, track, and album datasets to create a unified view.

Data Transformation & Optimization (Parquet): The transformed dataset is converted into Apache Parquet format. Parquet is highly optimized for analytical querying, reducing storage costs and accelerating query performance. The Parquet files are written to a separate S3 bucket (Processed Zone).

Schema & Metadata (AWS Glue Crawler): An AWS Glue Crawler automatically scans the Parquet files in the Processed Zone, infers the schema, and registers the metadata as a table in the AWS Glue Data Catalog.

Querying (Amazon Athena): The Glue Data Catalog table is utilized by Amazon Athena, allowing users to run standard SQL queries directly against the Parquet files in S3 without managing any infrastructure.

Visualization (Power BI): Power BI is connected to Amazon Athena to pull the analyzed data, enabling the creation of interactive dashboards and visualizations for data analysis.

Security: Proper IAM roles were configured to grant the Glue job and Athena necessary permissions to interact securely with S3.
