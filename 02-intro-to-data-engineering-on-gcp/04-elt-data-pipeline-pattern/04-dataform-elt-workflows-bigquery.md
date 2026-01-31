# Dataform: Simplifying ELT Pipelines in BigQuery

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

---

## 1. What Is Dataform?

**Mr. X:**
I hear Dataform mentioned a lot with BigQuery. What exactly is it?

**Mr. Artificial King:**
**Dataform** is a **serverless framework** that simplifies building and managing **ELT pipelines** using **SQL**.

It works directly with **Google BigQuery**, allowing you to:

* Transform data inside BigQuery
* Ensure data quality
* Automate workflows
* Document data pipelines

![Image](https://miro.medium.com/1%2As5qxAdq-_FQ2ZzNHm_D_DQ.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2Au91Q9NTao0sNYH3-bE2I1A.png)

![Image](https://www.ga4bigquery.com/content/images/2023/12/1_dataform_diagram.max-2200x2200.jpg)

---

## 2. Why Dataform Is Needed

**Mr. X:**
What problems does Dataform actually solve?

**Mr. Artificial King:**
Without Dataform, teams must manually:

* Define tables and views
* Manage SQL code versions
* Test data quality
* Schedule pipelines
* Coordinate dependencies

These tasks are time-consuming and error-prone.
**Dataform unifies transformation, testing, and automation** in one place, making pipelines more reliable and efficient.

---

## 3. How Dataform Works with BigQuery

**Mr. X:**
How does Dataform run my SQL?

**Mr. Artificial King:**
The process is simple and powerful:

1. Developers write SQL and JavaScript in Dataform
2. Dataform **compiles workflows in real time**

   * Dependency checks
   * Syntax validation
   * Error handling
3. The compiled SQL is executed **inside BigQuery**
4. Tables and views are materialized:

   * On-demand
   * Or via schedules

BigQuery remains the execution engine.

---

## 4. Dataform Project Structure

**Mr. X:**
How is a Dataform project organized?

**Mr. Artificial King:**
Development happens inside **workspaces** with standard files and folders:

* `definitions/` → SQLX files (tables, views, assertions)
* `includes/` → JavaScript helper functions
* `.gitignore` → Git management
* `package.json` / `package-lock.json` → JS dependencies
* `workflow_settings.yaml` → Compilation settings
* `README.md` → Project documentation

This structure keeps projects clean and scalable.

---

## 5. Understanding SQLX File Structure

**Mr. X:**
What makes SQLX different from normal SQL?

**Mr. Artificial King:**
A **SQLX file** provides a structured format:

1. **config block**

   * Metadata
   * Table type
   * Data quality tests

2. **js block**

   * Reusable JavaScript functions

3. **pre_operations block**

   * SQL run before main logic

4. **main SQL body**

   * Core transformation logic

5. **post_operations block**

   * SQL run after execution

This structure enforces clarity and consistency.

---

## 6. Cleaner SQL with Reusable Logic

**Mr. X:**
How does Dataform reduce complex SQL?

**Mr. Artificial King:**
Dataform replaces repetitive SQL with reusable functions.

Instead of large `CASE` statements, you can use:

* Simple function calls like `$(mapping.region("country"))`

Benefits:

* Cleaner SQL
* Better readability
* Easier maintenance
* Reusable logic across models

---

## 7. Table and View Configuration Types

**Mr. X:**
How do I define tables in Dataform?

**Mr. Artificial King:**
Dataform supports several configuration types:

* **declaration**

  * Reference existing BigQuery tables

* **table**

  * Create or replace tables using `SELECT`

* **incremental**

  * Append or update tables with new data

* **view**

  * Create or replace views
  * Can be materialized if needed

These definitions are compiled into executable SQL.

---

## 8. Data Quality with Assertions and Operations

**Mr. X:**
How does Dataform ensure data quality?

**Mr. Artificial King:**
Dataform provides two powerful features:

### Assertions

* Data quality tests
* Written in SQL or JavaScript
* Validate accuracy and consistency

### Operations

* Custom SQL logic
* Run before, during, or after workflows

Together, they help build **robust and trustworthy pipelines**.

---

## 9. Dependency Management in Dataform

**Mr. X:**
How does Dataform know what runs first?

**Mr. Artificial King:**
Dependencies are managed in three ways:

* **Implicit declaration**

  * Use `ref()` in SQL

* **Explicit declaration**

  * List dependencies in the `config` block

* **resolve() function**

  * Reference objects without creating dependencies

This ensures correct execution order.

---

## 10. Workflow Execution and Visualization

**Mr. X:**
Can I visualize my pipeline?

**Mr. Artificial King:**
Yes. Dataform workflows are best viewed as **graphs**.

A typical flow:

* Source declaration
* Intermediate transformation tables
* Assertions for quality checks
* Branching into:

  * Operations (e.g., ML training)
  * Production views

This makes pipeline logic easy to understand.

---

## 11. Scheduling and Triggering Dataform Workflows

**Mr. X:**
How are workflows executed?

**Mr. Artificial King:**
There are two trigger types:

### Internal Triggers

* Manual runs from Dataform UI
* Scheduled runs within Dataform

### External Triggers

* **Cloud Scheduler**
* **Cloud Composer**

Regardless of the trigger, **execution always happens in BigQuery**.

---

## 12. Final Summary

* Dataform is a serverless ELT framework for BigQuery
* Unifies SQL transformation, testing, and automation
* Compiles SQL workflows with dependency management
* SQLX files bring structure and reusability
* Assertions and operations ensure data quality
* Graph-based workflows improve visibility
* Internal and external triggers automate execution
* BigQuery remains the core execution engine

---

### 📁 Suggested GitHub Filename

**dataform-elt-workflows-bigquery.md**
