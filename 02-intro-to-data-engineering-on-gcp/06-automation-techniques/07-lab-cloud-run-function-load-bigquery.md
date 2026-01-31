# Lab: Using a Cloud Run Function to Load Data into BigQuery

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

---

## 1. What Is This Lab About?

**Mr. X:**
What will I build in this lab?

**Mr. Artificial King:**
In this lab, you create a **serverless Cloud Run function** that loads data into **BigQuery**.
You’ll see how **event-driven or on-demand code** can directly interact with analytics services.

You will use:

* **Cloud Run functions**
* **Google BigQuery**

![Image](https://docs.cloud.google.com/static/run/docs/images/functions-overview.svg)

![Image](https://miro.medium.com/1%2AOipvGHB4AvXCNnkoHit02w.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/bq_to_cf.max-800x800.jpg)

---

## 2. Step 1: Create a Cloud Run Function with Google Cloud SDK

**Mr. X:**
How do I start creating the function?

**Mr. Artificial King:**
First, you use the **Google Cloud SDK** to create a **Cloud Run function**.

In this step, you:

* Initialize a new function project
* Define the function logic (for loading data into BigQuery)
* Specify the runtime and trigger type

The SDK helps you work locally while preparing the function for deployment.

---

## 3. Step 2: Deploy and Test the Cloud Run Function

**Mr. X:**
How do I make the function live?

**Mr. Artificial King:**
Next, you **deploy the Cloud Run function** using the Google Cloud SDK.

After deployment:

* The function becomes available via its trigger (HTTP or event-based)
* You **test the function** by invoking it
* The function executes serverlessly and writes data into BigQuery

This confirms that your function logic and permissions are set correctly.

![Image](https://docs.cloud.google.com/static/run/docs/images/functions-overview.svg)

![Image](https://docs.cloud.google.com/static/workflows/images/workflows-run-visualization.svg)

---

## 4. Step 3: View the Data in BigQuery

**Mr. X:**
How do I verify that the data was loaded?

**Mr. Artificial King:**
You then open **BigQuery** and:

* Locate the target dataset and table
* Run a **SQL query** or preview the table
* Confirm that new rows were inserted

Seeing the data in BigQuery confirms the function executed successfully.

---

## 5. Step 4: Review Cloud Run Function Logs

**Mr. X:**
What if something goes wrong?

**Mr. Artificial King:**
That’s why the final step is reviewing **Cloud Run function logs**.

Logs help you:

* Confirm successful execution
* Debug errors or failures
* Track invocation details and timestamps

This is essential for troubleshooting and production monitoring.

---

## 6. Why This Lab Is Important

**Mr. X:**
Why is this approach useful in real projects?

**Mr. Artificial King:**
Because it demonstrates how to:

* Use **serverless functions** for data ingestion
* Trigger BigQuery loads without managing infrastructure
* Build **event-driven or on-demand ETL pipelines**
* Monitor executions using logs

This pattern is widely used for **lightweight, reactive data pipelines**.

---

## 7. Lab Summary

* Created a Cloud Run function using Google Cloud SDK
* Deployed and tested the function
* Loaded data into BigQuery
* Verified results using SQL
* Reviewed Cloud Run function logs for monitoring

---

### 📁 Suggested GitHub Filename

**cloud-run-function-load-bigquery-lab.md**
