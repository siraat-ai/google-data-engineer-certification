# Understanding Diagnostic Scenarios with Clear Reasoning

## Examining Slow Dataflow Pipeline Performance
**Mr. X:** My Dataflow pipeline is running slowly. I wrote the DoFn code myself. How can I understand what’s going wrong inside the code?  
**Mr. Artificial King:** Since the issue is about *code-level performance*, you need visibility into CPU usage, memory usage, and function execution time.  
The best tool here is **Cloud Profiler** because it helps analyze how your code behaves while running, without adding overhead.

**✔ Correct Approach:** Use Cloud Profiler

## Storing Order Files Immutably for Compliance
**Mr. X:** Laws say I must store daily order files without any changes for 365 days, and I also want to keep costs low. What’s the safest way?  
**Mr. Artificial King:** You need immutability, not just deletion rules. Cloud Storage lets you enforce this using **retention policies**, which prevent deletion or modification until the time expires.

**✔ Correct Approach:** Store the data in a Cloud Storage bucket and specify a retention period

## Creating a Unified and Searchable Data View
**Mr. X:** Different teams keep asking producers about data details like ownership and freshness. This is slow and messy. How can I fix this?  
**Mr. Artificial King:** You need a centralized governance and discovery layer. A **data mesh approach with Dataplex** allows producers to tag and manage metadata at creation time, making data searchable and trustworthy for everyone.

**✔ Correct Approach:** Implement a data mesh with Dataplex and have producers tag data when created

## Redacting Sensitive Customer Information
**Mr. X:** Regulations say we must store customer details like credit cards and emails, but analysts must never see them. What should we do?  
**Mr. Artificial King:** Manual deletion or regex is risky and unreliable. Google recommends **Cloud Data Loss Prevention (DLP)**, which has built-in detectors called *infoTypes* to accurately find and redact sensitive data.

**✔ Correct Approach:** Use the Cloud DLP API to identify and redact data matching infoTypes

## Granting BigQuery Access to Business Analysts
**Mr. X:** Analysts need to query data in BigQuery, but I want to follow best practices. Which permissions are right?  
**Mr. Artificial King:** Analysts should be able to run queries and view data, but not modify it. That means:
- `bigquery.user` to run jobs
- `bigquery.dataViewer` to read data

**✔ Correct Approach:** bigquery.user and bigquery.dataViewer

## Choosing Storage for Dataproc Processing
**Mr. X:** My Dataproc clusters process large CSV files, and many worker nodes need to read and write data. What storage works best?  
**Mr. Artificial King:** You need shared, scalable, and durable storage that multiple clusters can access easily. **Cloud Storage** is built exactly for this purpose.

**✔ Correct Approach:** Cloud Storage

## Applying Regional Policies Consistently
**Mr. X:** Cymbal Retail expanded into Europe, and regional policies differ from North America. How do I manage this cleanly?  
**Mr. Artificial King:** Google Cloud hierarchy helps here. By creating **top-level folders per region**, you can apply policies once and have them inherited by all projects in that region.

**✔ Correct Approach:** Create top level folders for each region and assign policies at the folder level

## Managing Encryption Keys Across Regions
**Mr. X:** Some regions require encryption keys to stay outside Google Cloud, but I still want centralized control. What’s the solution?  
**Mr. Artificial King:** This is exactly what **Cloud External Key Manager (EKM)** is for. It lets you store keys with an external provider while managing them centrally from Google Cloud.

**✔ Correct Approach:** Store keys with an external key management partner and use Cloud EKM

## Enabling Non-Programmers to Fix Data Repeatedly
**Mr. X:** Business analysts need to clean and fix large data files regularly, but they don’t know programming. What tool fits best?  
**Mr. Artificial King:** **Dataprep** is designed for this. It provides a visual interface to clean, deduplicate, and transform data in a repeatable and automated way.

**✔ Correct Approach:** Load the data into Dataprep and edit transformations as needed

## Migrating Massive On-Prem Data with Limited Bandwidth
**Mr. X:** We have hundreds of terabytes of data, only a 100 Mbps connection, and 45 days to migrate. Uploading won’t work. What should we do?  
**Mr. Artificial King:** In this case, physical transfer is the fastest and most reliable option. Google’s **Transfer Appliance** lets you ship data securely without relying on network bandwidth.

**✔ Correct Approach:** Order a transfer appliance, export the data to it, and ship it to Google

---

**filename:** diagnostic-questions-explained-dialogue.md
