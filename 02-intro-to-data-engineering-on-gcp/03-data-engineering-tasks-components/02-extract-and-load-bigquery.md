# Extract and Load Data Pipeline Pattern (BigQuery)

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — a curious learner
* **Mr. Artificial King** — a kind and patient guide

---

## 1. What Is the Extract and Load Pattern?

**Mr. X:** I often hear about *extract, transform, load (ETL)*. What is *extract and load* then?

**Mr. Artificial King:** Good question! The **extract and load (EL)** pattern is a simpler approach.
Here, we:

1. **Extract** data from source systems
2. **Load** it directly into **Google BigQuery**
3. Skip *upfront transformation*

This means we do **not** clean or reshape data before loading it.

---

## 2. Why Use Extract and Load?

**Mr. X:** Why would we skip transformation?

**Mr. Artificial King:** Because BigQuery is powerful enough to handle transformations *after* loading.
This gives us:

* Faster data ingestion
* Simpler pipelines
* Less maintenance

In short, **load first, transform later**.

![Image](https://docs.cloud.google.com/static/bigquery/images/elt-or-etl.png)

![Image](https://mozilla.github.io/gcp-ingestion/architecture/diagram.svg)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/Screen_Shot_2021-06-27_at_2.03.28_PM.max-1300x1300.png)

---

## 3. How Data Is Loaded into BigQuery

**Mr. X:** How does data actually get into BigQuery?

**Mr. Artificial King:** BigQuery offers several easy options:

### Common Tools

* **`bq load`** command-line tool
* **BigQuery Data Transfer Service** (scheduled, automated loading)
* **External tables** (query data without copying it)
* **BigLake tables** (unified access across storage systems)

These options reduce data duplication and improve efficiency.

---

## 4. Scheduling and Efficiency

**Mr. X:** Do I need to run loading manually every time?

**Mr. Artificial King:** Not at all.

* Built-in **scheduling** is supported
* Automated transfers reduce manual work
* External and BigLake tables avoid unnecessary data copying

This makes pipelines more **cost-effective** and **scalable**.

---

## 5. Supported Data Formats

**Mr. X:** What types of files can BigQuery load?

**Mr. Artificial King:** BigQuery is very flexible. It supports:

### Import Formats

* Avro
* Parquet
* ORC
* CSV
* JSON
* Firestore exports

### Export Formats

* CSV
* JSON
* Avro
* Parquet

This makes integration with other tools very easy.

---

## 6. Ways to Load Data into BigQuery

**Mr. X:** Is coding required to load data?

**Mr. Artificial King:** Not always. There are **two main ways**:

### 1. BigQuery Web UI

* Upload files directly
* Choose file format
* Auto-detect schema
* Best for beginners and quick tasks

### 2. `LOAD DATA` SQL Statement

* More control
* Ideal for automation
* Supports append or overwrite
* Perfect for production pipelines

---

## 7. Key Takeaways

* Extract and Load removes upfront transformation
* BigQuery handles transformations later using SQL
* Multiple tools simplify ingestion
* Supports many data formats
* UI for ease, SQL for control
* Efficient, scalable, and automation-friendly

---

### 📁 Suggested GitHub Filename

**extract-and-load-bigquery.md**
