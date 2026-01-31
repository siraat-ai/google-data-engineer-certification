# Combining Operational and Analytical Data with Federated Queries

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

![Image](https://miro.medium.com/0%2A8MyJ0_rA81cckV9a.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/0%2A3JANLGiGusC0kExh)

![Image](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2019/11/26/AthenaFederatedQueries1.png)

---

## 1. Going Beyond the Lakehouse with Federated Queries

**Mr. X:**
We already have a lakehouse with Cloud Storage, Iceberg, and BigQuery. How can we include live operational data too?

**Mr. Artificial King:**
That’s where **federated queries** come in.
**Google BigQuery** can query data stored **outside** the lakehouse—such as operational databases—**in real time**, without copying or moving the data.

This allows Cymbal to **bridge live operational data with historical analytical data**.

---

## 2. What Are Federated Queries?

**Mr. X:**
What does “federated” actually mean here?

**Mr. Artificial King:**
A **federated query** lets BigQuery:

* Send a query to an **external system**
* Retrieve results on demand
* Combine those results with data already in BigQuery

All of this happens through **a single SQL query**.

For Cymbal, this means querying:

* Real-time inventory data in **AlloyDB for PostgreSQL**
* Historical sales data stored as Iceberg tables in Cloud Storage

---

## 3. Why This Is Powerful for Cymbal

**Mr. X:**
Why is this useful for an e-commerce company?

**Mr. Artificial King:**
Because it unlocks **new insights without new pipelines**.

For example, Cymbal can:

* Join **current inventory levels** with **historical sales trends**
* Make real-time decisions about:

  * Stock replenishment
  * Promotions
  * Regional demand

And they can do this **without duplicating operational data** into the lakehouse.

---

## 4. Step 1: Create a Secure Connection Resource

**Mr. X:**
How does BigQuery securely access AlloyDB?

**Mr. Artificial King:**
First, a data administrator creates a **connection resource** in BigQuery.

This connection:

* Stores credentials securely
* Defines how BigQuery communicates with AlloyDB
* Is created **once** and reused across queries

This setup ensures **secure and controlled access** to operational systems.

---

## 5. Step 2: Query AlloyDB Using EXTERNAL_QUERY

**Mr. X:**
How do analysts actually query the operational database?

**Mr. Artificial King:**
They use the **EXTERNAL_QUERY** SQL function.

This function:

* Takes the **connection ID**
* Takes a **SQL query** written for the external database
* Executes that query on AlloyDB
* Returns the results to BigQuery

The results can then be:

* Joined with Iceberg tables
* Aggregated
* Filtered
* Used in BI dashboards

All within one BigQuery query.

---

## 6. Real-Time + Historical Data in One Query

**Mr. X:**
So everything feels like it’s in one place?

**Mr. Artificial King:**
Exactly.

From the analyst’s point of view:

* BigQuery queries **live operational data**
* BigQuery queries **historical analytical data**
* Everything is combined using **standard SQL**

Behind the scenes, the data stays **where it belongs**, optimized for its workload.

---

## 7. Key Benefits of Federated Queries

**Mr. X:**
What are the biggest advantages of this approach?

**Mr. Artificial King:**

Federated queries provide:

* **No data duplication**
* **Real-time access** to operational systems
* **Lower data movement costs**
* **Simpler architectures**
* **Faster time to insight**

They are perfect when operational freshness matters.

---

## 8. Key Takeaway

**Mr. Artificial King:**
Federated queries extend BigQuery beyond the lakehouse.

By combining:

* **AlloyDB** for live operational data
* **Iceberg tables** for historical analytics
* **BigQuery** as the central query engine

Cymbal can analyze **real-time and historical data together**, using one SQL interface—without compromising performance or data integrity.

---

### 📁 Suggested GitHub Filename

**bigquery-federated-queries-operational-analytical.md**
