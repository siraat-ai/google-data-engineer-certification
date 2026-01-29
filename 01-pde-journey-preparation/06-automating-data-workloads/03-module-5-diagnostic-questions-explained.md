# Diagnostic Questions: Maintaining and Automating Data Workloads (Explained)

## Capturing Erroneous Data in a Production Dataflow Pipeline
**Mr. X:** Our Dataflow pipeline sometimes receives bad input data. I want to keep processing good data, but also capture the bad records for later analysis. What’s the best way?  
**Mr. Artificial King:** Dataflow supports **side outputs** exactly for this case. You read the data once, process it efficiently, and send invalid records to a separate output without re-reading or duplicating work.

**✔ Correct Approach:** Create a side output for the erroneous data.

## Proactively Detecting Pipeline Delays
**Mr. X:** Some Dataflow jobs get stuck longer than usual, causing delays. I want to detect this early and fix it.  
**Mr. Artificial King:** Manual checks don’t scale. The reliable approach is to use **Cloud Monitoring alerts** based on **system lag metrics**, so you’re notified automatically when something goes wrong.

**✔ Correct Approach:** Set up alerts on Cloud Monitoring based on system lag.

## When to Enable Dataproc Autoscaling
**Mr. X:** A teammate asked when autoscaling should be enabled for Dataproc. What’s the recommended case?  
**Mr. Artificial King:** Autoscaling is best when you run **single-job clusters** that need to scale up during heavy processing and scale down afterward to save costs.

**✔ Correct Approach:** When you want to scale out single-job clusters.

## Handling Too Many Concurrent BigQuery Queries
**Mr. X:** Analysts run interactive queries, and thousands of reports run at the same time. We keep hitting concurrent query limits. How do we fix this?  
**Mr. Artificial King:** Separate workloads by priority. Run report-generation queries in **batch mode**, which doesn’t compete with interactive queries and helps avoid concurrency limits.

**✔ Correct Approach:** Run the report generation queries in batch mode.

## Disaster Recovery for Streaming Dataflow Pipelines
**Mr. X:** We process streaming data with Dataflow and Pub/Sub. How do we protect against zonal failures?  
**Mr. Artificial King:** **Dataflow snapshots** allow you to periodically save pipeline state, making recovery faster and more reliable during failures.

**✔ Correct Approach:** Take Dataflow snapshots periodically.

## Running Many Small Dataproc Jobs Efficiently
**Mr. X:** We have many small jobs, some high priority, some not. What’s the best Dataproc setup?  
**Mr. Artificial King:** **Ephemeral clusters** are ideal here. Each job gets a fresh cluster, avoiding resource contention and reducing idle costs.

**✔ Correct Approach:** Use ephemeral clusters.

## Resolving Hot Key Issues in Dataflow
**Mr. X:** Dataflow logs say a “hot key” was detected. Performance is bad. What should I do?  
**Mr. Artificial King:** Hot keys mean data isn’t evenly distributed. You must **rebalance or redesign the key** so work is spread evenly across workers.

**✔ Correct Approach:** Ensure that your data is evenly distributed.

## Minimizing Downtime for Cloud SQL Transactions
**Mr. X:** Our Cloud SQL database must always be available for transactions. How do we minimize downtime?  
**Mr. Artificial King:** **High availability (HA)** is the correct solution. It provides automatic failover, ensuring minimal disruption during failures.

**✔ Correct Approach:** Configure high availability.

## Managing Monday Morning BigQuery Spikes Cost-Effectively
**Mr. X:** Every Monday morning, analysts overload BigQuery. I want a flexible and cost-effective solution.  
**Mr. Artificial King:** **Flex Slots** let you temporarily add BigQuery capacity during peak times without long-term commitments.

**✔ Correct Approach:** Use Flex Slots.

## Designing Best-Practice Cloud Composer Tasks
**Mr. X:** I’m building repeatable workflows in Cloud Composer. What’s the best design practice?  
**Mr. Artificial King:** Follow the **single responsibility principle**. Each task should do **one operation only**, making workflows easier to debug, maintain, and scale.

**✔ Correct Approach:** Write each task to be responsible for one operation.

## Final Takeaway
**Mr. Artificial King:** These scenarios test your ability to:
- Monitor and alert proactively  
- Automate and scale workloads  
- Handle failures gracefully  
- Balance cost, reliability, and performance  

Strong data engineers don’t just build pipelines—they keep them running smoothly at scale.

---

**filename:** module-5-diagnostic-questions-explained.md
