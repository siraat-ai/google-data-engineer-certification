# Dataform Lab: Creating and Executing a SQL Workflow

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

---

## 1. What Is This Lab About?

**Mr. X:**
What will I learn in this Dataform lab?

**Mr. Artificial King:**
In this lab, you learn how to use **Dataform** to **create, run, and monitor a SQL workflow** that executes inside **Google BigQuery**.

You will:

* Create a Dataform repository
* Initialize a development workspace
* Build and execute a SQL workflow
* Verify execution using logs

![Image](https://www.ga4bigquery.com/content/images/2023/12/1_dataform_diagram.max-2200x2200.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2Au91Q9NTao0sNYH3-bE2I1A.png)

![Image](https://cuberoot31.com/images/dataform-workflow-execution-log.png)

---

## 2. Step 1: Creating a Dataform Repository

**Mr. X:**
What is the first thing I need to set up?

**Mr. Artificial King:**
You start by creating a **Dataform repository**.

This repository:

* Stores all SQLX and JavaScript code
* Tracks workflow definitions
* Acts as the foundation for ELT development

Think of it as the **home for your data transformation logic**.

---

## 3. Step 2: Initializing a Development Workspace

**Mr. X:**
How do I actually start writing transformations?

**Mr. Artificial King:**
Next, you create and initialize a **Dataform development workspace**.

The workspace:

* Provides default folders like `definitions/` and `includes/`
* Lets you safely develop and test SQL workflows
* Keeps development isolated from production

Once initialized, you’re ready to build transformations.

---

## 4. Step 3: Creating and Executing a SQL Workflow

**Mr. X:**
What happens inside the workflow?

**Mr. Artificial King:**
Inside the workspace, you:

* Define tables or views using **SQLX files**
* Configure dependencies and metadata
* Compile the workflow

When executed:

* Dataform converts SQLX into executable SQL
* Dependency order is resolved automatically
* The SQL runs **inside BigQuery**

This ensures reliable and repeatable transformations.

---

## 5. Step 4: Viewing Execution Logs

**Mr. X:**
How do I know the workflow completed successfully?

**Mr. Artificial King:**
After execution, you check the **execution logs in Dataform**.

Logs show:

* Which steps ran successfully
* Execution order
* Any errors or warnings

This confirms that your SQL workflow finished as expected.

---

## 6. Why This Lab Matters

**Mr. X:**
Why is this workflow approach important?

**Mr. Artificial King:**
Because it teaches you how to:

* Manage SQL transformations at scale
* Automate ELT pipelines
* Track execution and troubleshoot issues
* Build production-ready data workflows

It’s a key skill for modern data engineering on Google Cloud.

---

## 7. Lab Summary

* Created a Dataform repository
* Initialized a development workspace
* Built and executed a SQL workflow
* Verified completion using execution logs
* All transformations ran inside BigQuery

---

### 📁 Suggested GitHub Filename

**dataform-lab-sql-workflow.md**
