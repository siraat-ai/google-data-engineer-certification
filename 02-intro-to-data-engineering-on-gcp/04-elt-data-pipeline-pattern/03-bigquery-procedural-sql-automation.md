# Advanced SQL, Automation, and Extensions in BigQuery

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

---

## 1. Procedural SQL in BigQuery

**Mr. X:**
Can BigQuery run more than one SQL statement like a program?

**Mr. Artificial King:**
Yes. **Google BigQuery** supports **procedural SQL**, which allows you to execute **multiple SQL statements in sequence with shared state**.

This enables:

* Automated table creation
* Complex logic using `IF`, `WHILE`, and loops
* Use of **transactions** for data integrity
* Declaring and using **variables**
* Referencing **system variables**

This makes SQL behave more like a programming language.

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/unsaved_query_edited.max-600x600.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/BQARef_Query_Exec.max-2200x2200.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/BigQuery_queries_9.max-1000x1000.png)

---

## 2. User-Defined Functions (UDFs)

**Mr. X:**
What if I need custom logic that SQL doesn’t support easily?

**Mr. Artificial King:**
That’s where **User-Defined Functions (UDFs)** come in.

BigQuery supports:

* **SQL UDFs** (recommended when possible)
* **JavaScript UDFs** for more flexibility

UDFs can be:

* **Temporary** (exist only for a session)
* **Persistent** (reusable across queries)

JavaScript UDFs allow:

* Use of external libraries
* Reuse of community-contributed UDFs

---

## 3. Stored Procedures in BigQuery

**Mr. X:**
How do I organize complex SQL logic cleanly?

**Mr. Artificial King:**
You can use **stored procedures**.

Stored procedures are:

* Pre-compiled collections of SQL statements
* Designed to encapsulate complex logic

### Benefits

* Reusability
* Parameterized inputs
* Transaction handling
* Better performance and maintainability

They can be called:

* From applications
* From other SQL scripts

This promotes **modular and clean design**.

---

## 4. Stored Procedures for Apache Spark

**Mr. X:**
Can BigQuery work with Spark-based logic too?

**Mr. Artificial King:**
Yes. BigQuery supports **stored procedures for Apache Spark** using **Apache Spark**.

You can define Spark stored procedures:

* In the **BigQuery PySpark editor**
* Using `CREATE PROCEDURE`
* With **Python, Java, or Scala**

The code can be:

* Stored in **Cloud Storage**
* Written inline in the BigQuery editor

---

## 5. Remote Functions with Cloud Run

**Mr. X:**
What if I want to use Python logic inside SQL?

**Mr. Artificial King:**
That’s possible using **remote functions**.

Remote functions:

* Extend BigQuery using **Cloud Run**
* Allow complex transformations in Python
* Are registered in BigQuery with a connection and endpoint

Once defined, they behave like UDFs and can be called directly in SQL queries.

Example use case:

* A Python function returns file sizes for Cloud Storage objects
* Registered in BigQuery as `object_length()`
* Used directly inside SQL queries

![Image](https://media.licdn.com/dms/image/v2/D4E12AQEPOaknD6jCyA/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1682164414549?e=2147483647\&t=BC5Xa6uYCTsTfm3kQHuvdqyH2nFujc172EcIpzGVI08\&v=beta)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AxYXMsGeqpgyV93IEdbSdew.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AVi_LvEYAJQKa79Cc10kpvw.png)

---

## 6. BigQuery DataFrames and Jupyter Notebooks

**Mr. X:**
Can I explore BigQuery data using Python notebooks?

**Mr. Artificial King:**
Absolutely.
**Jupyter Notebooks** integrated with **BigQuery DataFrames** allow you to:

* Explore very large datasets (bigger than memory)
* Combine SQL and Python transformations
* Perform advanced data manipulation
* Schedule notebook executions
* Use popular visualization libraries seamlessly

This is ideal for data exploration and experimentation.

---

## 7. Saving and Scheduling Queries

**Mr. X:**
Can I automate queries to run regularly?

**Mr. Artificial King:**
Yes. BigQuery lets you:

* Save queries
* Manage versions
* Share queries with others

You can also **schedule queries** by setting:

* Execution frequency
* Start and end times
* Destination tables

This enables hands-free, repeatable workflows.

---

## 8. Handling Post-Query Tasks

**Mr. X:**
What if more steps are needed after a scheduled query runs?

**Mr. Artificial King:**
That’s common in real pipelines.

Post-query tasks may include:

* Triggering additional SQL scripts
* Running data quality checks
* Applying or updating security policies

For **complex SQL workflows**, **Dataform** is recommended.
It helps orchestrate transformations, dependencies, and validations automatically.

---

## 9. Final Summary

* Procedural SQL enables multi-step logic in BigQuery
* UDFs extend SQL with reusable custom logic
* Stored procedures encapsulate complex operations
* Spark stored procedures support Python, Java, and Scala
* Remote functions integrate Python via Cloud Run
* Notebooks enable large-scale exploration and scheduling
* Saved and scheduled queries automate pipelines
* Dataform manages complex, production-grade SQL workflows

---

### 📁 Suggested GitHub Filename

**bigquery-procedural-sql-automation.md**
