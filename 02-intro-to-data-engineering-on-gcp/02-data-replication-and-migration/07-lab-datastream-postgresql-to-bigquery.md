# ☁️ Datastream Lab – Replicating PostgreSQL to BigQuery


::contentReference[oaicite:0]{index=0}


## 🎯 What Is the Goal of This Lab?

**Mr. X:** What is the main objective of this lab?  
**Mr. Artificial King:** In this lab, you use **Datastream** to **replicate data from PostgreSQL into BigQuery**.  
The goal is to understand how continuous data replication works from a relational database into an analytics platform.

---

## 🗄️ Preparing Cloud SQL for PostgreSQL

**Mr. X:** What is the first practical step in the lab?  
**Mr. Artificial King:** First, you **prepare and load a Cloud SQL for PostgreSQL instance**.

This means:
- Creating a PostgreSQL database in Cloud SQL  
- Loading sample data into it  
- Making sure it is ready to act as the **source database**  

This database will generate changes that Datastream will replicate.

---

## 🔌 Creating Datastream Connection Profiles

**Mr. X:** How does Datastream know where to read from and write to?  
**Mr. Artificial King:** That is done using **connection profiles**.

In this lab, you create:
- A **source connection profile** for PostgreSQL  
- A **target connection profile** for BigQuery  

These profiles securely define **how Datastream connects** to both systems.

---

## 🔄 Creating and Starting a Datastream Stream

**Mr. X:** When does the actual replication start?  
**Mr. Artificial King:** After setting up connection profiles, you create a **Datastream processing stream**.

This stream:
- Defines what data to replicate  
- Starts reading changes from PostgreSQL  
- Continuously sends them toward BigQuery  

Once created, you **start the replication**.

---

## 📊 Validating Replication in BigQuery

**Mr. X:** How do we confirm that replication is working?  
**Mr. Artificial King:** Finally, you **validate the replicated data in BigQuery**.

You check:
- Whether tables are created  
- Whether data matches the source  
- Whether new changes appear automatically  

This confirms that **near real-time replication is successful**.

---

## ✅ Final Lab Summary

**Mr. Artificial King:**  
In this lab, you:
- Prepared a Cloud SQL for PostgreSQL instance  
- Created Datastream source and target connection profiles  
- Built and started a Datastream replication stream  
- Verified replicated data in BigQuery  

This lab demonstrates how Datastream enables **continuous database replication for analytics**.

📄 Filename:  
`datastream-postgresql-to-bigquery-lab.md`
