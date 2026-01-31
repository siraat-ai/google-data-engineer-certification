# BigQuery Partitioning Demo

## Why Partitioned Tables Use Fewer Resources (and Cost Less)

## Simple Notes with a Friendly Conversation

### Characters

* **Mr. X** — the curious learner
* **Mr. Artificial King** — the calm and patient guider

![Image](https://docs.cloud.google.com/static/bigquery/images/clustering-and-partitioning-tables.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A5vKIsGzOnymrLkUwba2v9Q.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/BigQuery_explained_storage_3.max-600x600.png)

---

## 1. What This Demo Is Really Showing

**Mr. X:**
In this demo, both tables are identical—same data, same rows. Why does one query cost so much less?

**Mr. Artificial King:**
Because **one table is partitioned and the other is not**.

Both queries:

* Use the **same SQL**
* Scan the **same logical dataset**
* Filter by the **same date**

The **only difference** is that one table is **partitioned on the date column**.

This single design choice dramatically changes how **Google BigQuery** processes the query.

---

## 2. The Three Metrics That Matter

**Mr. X:**
The demo focuses on three numbers in the execution details. What do they mean?

**Mr. Artificial King:**
These three metrics tell you **how expensive a query really is**.

### 1) Elapsed Time (Wall-Clock Time)

* The real-world time from clicking **Run** to completion
* What the user experiences

### 2) Slot Time Consumed

* The **total CPU work done**
* Calculated by adding up:

  * How long **each slot** worked
* This is what mostly drives **query cost**

### 3) Bytes Shuffled

* How much data was **moved between slots**
* High shuffle = expensive joins and aggregations

---

## 3. Results: Non-Partitioned Table

**Mr. X:**
What happened when the query ran on the non-partitioned table?

**Mr. Artificial King:**
Here’s what the execution details showed:

* **Elapsed time:** ~14 seconds
* **Slot time consumed:** ~7 hours 16 minutes
* **Bytes shuffled:** ~100 MB

Even though the query finished quickly, it:

* Scanned **far more data than necessary**
* Used **many more slots**
* Shuffled a **large volume of data**

If this ran on a **single processor**, it would have taken **over 7 hours**.

---

## 4. Results: Partitioned Table

**Mr. X:**
And what changed with the partitioned table?

**Mr. Artificial King:**
Everything improved—using the **same SQL**.

* **Elapsed time:** ~10 seconds
* **Slot time consumed:** ~4 hours 34 minutes
* **Bytes shuffled:** ~100 KB

That’s:

* Much **less compute**
* Much **less data movement**
* Much **lower cost**

---

## 5. Why Partitioning Makes Such a Big Difference

**Mr. X:**
Why does partitioning reduce resource usage so much?

**Mr. Artificial King:**
Because of **partition pruning**.

When a table is partitioned by date:

* BigQuery reads **only the relevant partitions**
* It skips all other dates entirely

Without partitioning:

* BigQuery must scan **the entire table**
* Even if your `WHERE` clause filters by date

Less data scanned means:

* Fewer slots needed
* Less shuffle
* Lower cost

---

## 6. Same Query, Same Data — Very Different Cost

**Mr. X:**
So nothing changed except the table design?

**Mr. Artificial King:**
Exactly.

| Aspect         | Non-Partitioned | Partitioned |
| -------------- | --------------- | ----------- |
| SQL Query      | Same            | Same        |
| Data           | Same            | Same        |
| Elapsed Time   | Slower          | Faster      |
| Slot Time      | Very High       | Much Lower  |
| Bytes Shuffled | ~100 MB         | ~100 KB     |
| Cost           | Higher          | Lower       |

This is why **table design matters as much as SQL** in BigQuery.

---

## 7. Business Impact for Cymbal

**Mr. X:**
Why should a business like Cymbal care?

**Mr. Artificial King:**
Because Cymbal:

* Runs **many queries**
* Has **large datasets**
* Cares about **cost and performance**

Partitioning:

* Makes dashboards more responsive
* Reduces query costs
* Scales better as data grows

For production analytics, it’s not optional—it’s essential.

---

## 8. Key Takeaway

**Mr. Artificial King:**
Partitioning doesn’t change your results.
It changes **how much BigQuery has to work to get them**.

By using partitioned tables:

* You scan less data
* Consume fewer slots
* Shuffle far less data
* Pay less
* Get results faster

This demo clearly shows why **partitioning is one of the most powerful performance and cost optimizations in BigQuery**.

---

### 📁 Suggested GitHub Filename

**bigquery-partitioned-vs-nonpartitioned-demo.md**
