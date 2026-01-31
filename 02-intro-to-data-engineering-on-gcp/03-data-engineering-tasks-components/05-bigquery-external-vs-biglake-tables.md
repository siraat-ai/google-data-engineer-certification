# BigQuery External Tables and BigLake Tables

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the kind and patient guide

---

## 1. BigQuery Beyond Its Own Storage

**Mr. X:** I thought BigQuery only worked with data stored inside it. Is that true?

**Mr. Artificial King:** Not anymore.
**Google BigQuery** can analyze data **even when it is stored outside BigQuery**.

It can directly query data from:

* **Google Cloud Storage**
* **Google Sheets**
* **Google Cloud Bigtable**

This is made possible using **external tables** and **BigLake tables**.

![Image](https://miro.medium.com/1%2APnCw2SnrlXjXQt_O63W2Ww.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/BQ_Explained_2.max-900x900.jpg)

---

## 2. Permanent Tables vs External Tables

**Mr. X:** What are my options for analyzing data?

**Mr. Artificial King:** You have three main choices:

### Permanent BigQuery Tables

* Data is **loaded into BigQuery**
* Very **high performance**
* Requires **data movement**

### External Tables

* Data stays in **Cloud Storage or Sheets**
* No data loading required
* Best for **less frequent queries**
* Performance can be slower

### BigLake Tables

* Data stays outside BigQuery
* High-performance analytics
* No data movement
* Enterprise-grade features

---

## 3. External Tables Explained

**Mr. X:** How do external tables work?

**Mr. Artificial King:** External tables let BigQuery **query data directly at its source**.

Examples:

* CSV or Parquet files in Cloud Storage
* A Google Sheets document treated as a table

You simply provide:

* File or sheet URL
* Data format

BigQuery then treats it like a normal table.

---

## 4. Limitations of External Tables

**Mr. X:** Are there any drawbacks?

**Mr. Artificial King:** Yes, some limitations:

* Slower query performance
* No query cost estimation
* No table preview
* No query result caching

They are simple, but not ideal for complex or frequent analytics.

---

## 5. What Is BigLake?

**Mr. X:** So what makes BigLake special?

**Mr. Artificial King:** **BigLake** extends BigQuery’s power to **data lakes**.

It provides:

* Unified querying across data lakes and warehouses
* Access to data in Cloud Storage and even **other cloud object stores**
* No data copying or movement

![Image](https://pbs.twimg.com/media/GuYzapKWQAAiNKw.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/0%2AbGFXoLb45JkZSoGV.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/biglake.max-2000x2000.jpg)

---

## 6. Performance and SQL Experience with BigLake

**Mr. X:** Can I still use SQL?

**Mr. Artificial King:** Yes.
You can use **standard BigQuery SQL**, including:

* `SELECT` queries
* Joins
* Filters and aggregations

Even though data lives outside BigQuery, **metadata caching** improves performance behind the scenes.

---

## 7. BigLake Metadata Cache

**Mr. X:** What is metadata caching?

**Mr. Artificial King:** BigLake maintains a **metadata cache** that stores:

* File size
* Row count
* Column statistics (min/max values)
* Partition information

This allows BigQuery to:

* Skip scanning unnecessary files
* Prune partitions faster
* Push down filters dynamically

BigLake uses **Apache Arrow** for efficient data handling.

---

## 8. Spark and Metadata Sharing

**Mr. X:** Can other tools benefit from this metadata?

**Mr. Artificial King:** Yes.
The metadata cache can also be accessed by **Apache Spark** through the Spark–BigQuery connector, improving query speed across platforms.

The cache:

* Can be refreshed automatically or manually
* Supports staleness from **30 minutes to 7 days**

---

## 9. Security and Access Management

**Mr. X:** What about permissions?

**Mr. Artificial King:** This is where BigLake shines.

### External Tables

* Require permissions on:

  * The BigQuery table
  * The underlying data source
* More complex access control

### BigLake Tables

* Use **service account delegation**
* Decouple table access from storage access
* Support:

  * Column-level security
  * Row-level security

This simplifies security and improves governance.

---

## 10. External Tables vs BigLake Tables (Summary)

| Feature              | External Tables | BigLake Tables |
| -------------------- | --------------- | -------------- |
| Data movement        | No              | No             |
| Performance          | Lower           | Higher         |
| Security             | Basic           | Advanced       |
| Metadata caching     | No              | Yes            |
| Multi-cloud support  | No              | Yes            |
| Enterprise readiness | Limited         | Strong         |

---

## 11. Final Summary

* BigQuery can analyze data outside its storage
* External tables are simple and quick to set up
* BigLake offers high performance without data movement
* BigLake provides unified access across data lakes and warehouses
* Advanced security and metadata caching make BigLake ideal for enterprise use cases

---

### 📁 Suggested GitHub Filename

**bigquery-external-vs-biglake-tables.md**
