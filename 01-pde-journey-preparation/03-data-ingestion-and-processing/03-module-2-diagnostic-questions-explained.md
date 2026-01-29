# Diagnostic Questions: Ingesting and Processing Data (Explained)

## Letting Analysts Build Pipelines Visually
**Mr. X:** We have many data analysts but only a small data engineering team. Analysts want to build pipelines themselves using a graphical interface. Which tool fits best?  
**Mr. Artificial King:** You should choose a tool designed for **visual, no-code or low-code pipeline creation**. Cloud Data Fusion provides a drag-and-drop UI that analysts can easily use without deep engineering knowledge.

**✔ Correct Choice:** Cloud Data Fusion

## Orchestrating a Multi-Step Data Pipeline
**Mr. X:** My pipeline has many steps—watching a Cloud Storage bucket, starting a Dataflow job, running a shell script, and deleting files. How do I orchestrate all this?  
**Mr. Artificial King:** You need a workflow orchestration tool that can manage dependencies and task order. Cloud Composer is built exactly for this purpose and is based on Apache Airflow.

**✔ Correct Choice:** Cloud Composer

## Calculating Hourly Sales from Streaming Data
**Mr. X:** I’m processing streaming point-of-sales data and want total sales per hour continuously. What windowing should I use?  
**Mr. Artificial King:** Since you want **non-overlapping, fixed one-hour buckets**, tumbling windows are the right choice. They cleanly group data into hourly intervals.

**✔ Correct Choice:** Tumbling windows (fixed windows in Apache Beam)

## Choosing a Sink for Large Time-Series Data
**Mr. X:** My pipeline processes massive financial data and produces a sparse, time-series key-value dataset. Where should I store it?  
**Mr. Artificial King:** This is a classic use case for Bigtable. It’s optimized for large-scale, sparse, time-series data with very fast reads and writes.

**✔ Correct Choice:** Bigtable

## Building a Streaming Analytics Pipeline
**Mr. X:** I want to build a streaming analytics pipeline on Google Cloud. Which set of products supports streaming end to end?  
**Mr. Artificial King:** A typical streaming architecture uses:
- Pub/Sub for ingestion  
- Dataflow for processing  
- BigQuery for analytics  

Together, they form a complete streaming solution.

**✔ Correct Choice:** Pub/Sub, Dataflow, BigQuery

## Designing a Daily JSON Ingestion Pipeline
**Mr. X:** External sources send us JSON files daily. How should I design this pipeline?  
**Mr. Artificial King:** The recommended pattern is:
- Land the raw data in Cloud Storage
- Build an ETL pipeline to transform and load it into analytics systems

This approach is secure, scalable, and standard.

**✔ Correct Choice:** Store the data in Cloud Storage and create an ETL pipeline

## Running Spark Jobs Without Managing Clusters
**Mr. X:** I use PySpark on Dataproc, but I don’t want to manage clusters anymore. What’s the best option?  
**Mr. Artificial King:** Dataproc Serverless removes the need to provision or manage clusters. You submit jobs, and Google Cloud handles the infrastructure.

**✔ Correct Choice:** Configure the job to run on Dataproc Serverless

## Combining BigQuery Data with Cloud SQL Data
**Mr. X:** I have large datasets in BigQuery and a small, frequently changing dataset in Cloud SQL. What’s the best way to combine them?  
**Mr. Artificial King:** Federated queries allow BigQuery to read data directly from Cloud SQL in real time—perfect for small, changing datasets.

**✔ Correct Choice:** Use a federated query to get data from Cloud SQL

## Running Long-Running Batch Jobs Without Managing Infrastructure
**Mr. X:** I need to run batch jobs that may take days, and I don’t want to manage infrastructure. What should I use?  
**Mr. Artificial King:** Google Cloud Batch is designed exactly for this. It handles provisioning, scheduling, and execution of long-running batch workloads.

**✔ Correct Choice:** Run the jobs on Batch

## Building CI/CD for Dataflow Pipelines
**Mr. X:** When developers update Dataflow code, I want automated testing and deployment with minimal effort. What tool should I use?  
**Mr. Artificial King:** Cloud Build integrates directly with source repositories and automates build, test, and deployment workflows—ideal for CI/CD.

**✔ Correct Choice:** Cloud Build

## Final Advice
**Mr. Artificial King:** These diagnostic questions help you:
- Recognize the **right tool for each ingestion and processing scenario**
- Understand **Google-recommended architectures**
- Identify areas to focus on in your study plan

Use the reasoning behind each answer—not just the answer itself—to prepare confidently for the exam.

---

**filename:** module-2-diagnostic-questions-explained.md
