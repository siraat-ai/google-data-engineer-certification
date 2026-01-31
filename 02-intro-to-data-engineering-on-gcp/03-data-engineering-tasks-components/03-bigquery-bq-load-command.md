# Using the `bq` Command to Load Data into BigQuery

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the kind and patient guide

---

## 1. What Is the `bq` Command?

**Mr. X:** I want to work with BigQuery from the terminal. Is that possible?

**Mr. Artificial King:** Absolutely!
The **`bq` command**, which comes with the **Google Cloud SDK**, lets you interact with **Google BigQuery** programmatically using the command line.

It feels very similar to common Linux commands, making it easy to learn.

---

## 2. Creating BigQuery Objects with `bq mk`

**Mr. X:** Can I create datasets and tables using `bq`?

**Mr. Artificial King:** Yes.
You can use the **`bq mk`** command to:

* Create datasets
* Create tables

This is useful when setting up environments or automating infrastructure.

---

## 3. Loading Data Using `bq load`

**Mr. X:** How do I load data into BigQuery tables?

**Mr. Artificial King:** That’s where **`bq load`** comes in.
It is a powerful command designed to efficiently load data into BigQuery tables from different sources.

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AGaZToPJ49vWrvqkY-U4wGA.png)

![Image](https://i.sstatic.net/fUQHQ.png)

![Image](https://miro.medium.com/1%2AVPdfV1nJm9HDNVQk-XoaPw.png)

---

## 4. Important Parameters in `bq load`

**Mr. X:** What options do I need to remember?

**Mr. Artificial King:** Some key parameters are:

* **Source format**

  * Example: CSV, JSON, Avro, Parquet
* **Skip header rows**

  * Useful when CSV files contain column names
* **Target dataset and table**

  * Where the data will be stored

These options help control how data is interpreted during loading.

---

## 5. Loading Data from Cloud Storage

**Mr. X:** Can I load many files at once?

**Mr. Artificial King:** Yes!

* You can load data from **Cloud Storage**
* Use **wildcards** to load multiple files in one command

  * Example: `data_*.csv`

You can also:

* Provide a **schema file**
* Define table structure explicitly instead of auto-detection

---

## 6. Why Use `bq load`?

**Mr. X:** Why not always use the UI?

**Mr. Artificial King:** The `bq load` command gives:

* More **flexibility**
* Better **automation**
* Fine-grained **control**
* Easy integration with scripts and pipelines

It’s ideal for production-grade data pipelines.

---

## 7. Key Takeaways

* `bq` is a command-line tool for BigQuery
* `bq mk` creates datasets and tables
* `bq load` loads data efficiently
* Supports multiple formats
* Can load multiple files using wildcards
* Schema files add structure and control

---

### 📁 Suggested GitHub Filename

**bigquery-bq-load-command.md**
