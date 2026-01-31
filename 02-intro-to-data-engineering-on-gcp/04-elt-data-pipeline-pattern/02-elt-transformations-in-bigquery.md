# Extract, Load, and Transform (ELT) in BigQuery

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

---

## 1. Core Idea of the ELT Pattern

**Mr. X:**
I keep hearing that ELT is different from ETL. What is the main idea behind ELT?

**Mr. Artificial King:**
In the **Extract, Load, and Transform (ELT)** pattern, data is **loaded into BigQuery first**, and transformations happen *after* loading.

This means:

1. Extract data from source systems
2. Load raw data directly into **Google BigQuery**
3. Transform the data inside BigQuery

This approach fully uses BigQuery’s powerful processing engine.

![Image](https://miro.medium.com/1%2A_nYVb7FnqOxhJ-azDxNnZw.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/instant-insights-35pye.max-1200x1200.PNG)

![Image](https://docs.cloud.google.com/static/bigquery/images/elt-or-etl.png)

---

## 2. Ways to Transform Data After Loading

**Mr. X:**
Once the data is in BigQuery, how can I transform it?

**Mr. Artificial King:**
You have several flexible options:

* **SQL (procedural queries)**

  * Filter, join, aggregate, and clean data
* **Scheduled queries**

  * Automatically run transformations on a schedule
* **Scripting and programming languages**

  * Use tools like Python with BigQuery APIs
* **Transformation tools**

  * Use **Dataform** for managed SQL workflows

You can choose what fits your team and complexity level.

---

## 3. ELT Pipeline Flow in Practice

**Mr. X:**
Can you explain how a typical ELT pipeline works step by step?

**Mr. Artificial King:**
Sure. A standard ELT pipeline looks like this:

### Step 1: Load to Staging Tables

* Structured data is loaded into **staging tables** in BigQuery
* Data remains raw or lightly structured

### Step 2: Transform Inside BigQuery

* Use **SQL scripts**, **scheduled queries**, or **Dataform SQL workflows**
* Clean, enrich, and reshape the data

### Step 3: Move to Production Tables

* Transformed data is written to **production tables**
* Data is now ready for analytics and reporting

---

## 4. Why BigQuery Is Ideal for ELT

**Mr. X:**
Why do transformations happen inside BigQuery instead of outside?

**Mr. Artificial King:**
Because BigQuery offers:

* Massive, scalable compute
* Fast SQL-based transformations
* No infrastructure management
* Easy automation and scheduling

This makes transformations **faster, simpler, and more reliable**.

![Image](https://docs.cloud.google.com/static/bigquery/images/elt-or-etl.png)

![Image](https://user-images.githubusercontent.com/3038111/125615532-dcfa90c4-f211-4b79-8b15-a2f6f2a069ed.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/1_dataform_diagram.max-2200x2200.jpg)

---

## 5. Role of Dataform in ELT

**Mr. X:**
Where does Dataform really help?

**Mr. Artificial King:**
Dataform simplifies transformations beyond basic scripting by:

* Organizing SQL into reusable models
* Managing dependencies between tables
* Enabling version control
* Supporting production-ready workflows

It turns SQL-based ELT into a **well-managed data engineering process**.

---

## 6. Final Summary

* ELT loads data into BigQuery first
* Transformations happen *after loading*
* SQL, scheduled queries, and Python can transform data
* Dataform simplifies and manages SQL workflows
* Staging tables → transformations → production tables
* BigQuery’s processing power makes ELT efficient

---

### 📁 Suggested GitHub Filename

**elt-transformations-in-bigquery.md**
