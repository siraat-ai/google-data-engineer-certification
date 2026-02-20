# SaaS Streaming Analytics System – Professional Notes

---

## 1️⃣ High-Level Architecture Overview

We are designing a **real-time SaaS analytics pipeline** in Google Cloud.

### Business Requirements

* Track user clicks
* Monitor sales
* Detect fraud
* Provide real-time dashboards
* Scale automatically during traffic spikes

---

## 2️⃣ End-to-End Streaming Pipeline

### Architecture Flow

User Application
⬇
Pub/Sub
⬇
Dataflow
⬇
BigQuery
⬇
Dashboard (Looker)

---

## 3️⃣ Service Responsibilities

### 🔹 Pub/Sub – Messaging Layer

**Purpose:**

* Ingest real-time events
* Decouple producers and consumers
* Buffer traffic spikes

**Key Characteristics:**

* Horizontally scalable
* At-least-once delivery
* Message retention (default up to 7 days)
* Acknowledgment (ACK) mechanism

**Important Concept:**
If Dataflow crashes before ACK → Pub/Sub redelivers the message.

---

### 🔹 Dataflow – Processing Engine

**Purpose:**

* Distributed stream and batch processing
* Apply transformations
* Validate data
* Remove duplicates
* Perform aggregations
* Detect fraud

**Technical Concept:**
Dataflow uses workers (virtual machines) for parallel processing.

#### What is a Worker?

A worker is a compute instance that processes a portion of the pipeline data.

More workers = more parallelism.

#### Autoscaling

Dataflow can automatically:

* Scale up when traffic increases
* Scale down when traffic decreases

This ensures:

* Performance stability
* Cost optimization

---

### 🔹 BigQuery – Data Warehouse

**Purpose:**

* Store processed analytical data
* Execute SQL queries
* Power dashboards

BigQuery is not ideal for heavy validation logic.
Validation should occur before storage (preferably in Dataflow).

---

## 4️⃣ Reliability & Failure Handling

### Scenario: Dataflow Crash

If Dataflow crashes:

* If message NOT acknowledged → Pub/Sub redelivers
* If acknowledged but failure happens later → possible duplicate processing

Therefore, pipelines should be:

* Idempotent (safe to process same message multiple times)

---

## 5️⃣ Scaling Scenario – 1 Million Events per Minute

1 million per minute ≈ 16,600 per second

Cloud systems are designed for this scale.

### Pub/Sub

Handles very high throughput automatically.

### Dataflow

Scales using autoscaling workers.

### Possible Bottleneck

Often downstream systems (e.g., BigQuery writes).

---

## 6️⃣ BigQuery Write Bottleneck Problem

If events are written one-by-one:

* Too many API calls
* Throughput limits reached
* Increased latency
* Higher cost

---

## 7️⃣ Solution – Write Batching (Micro-Batching)

Instead of inserting every event individually:

Batch multiple events (e.g., 500–1000 records)
Write together.

**Benefits:**

* Fewer API calls
* Better throughput
* Lower cost
* More stable performance

---

## 8️⃣ Engineering Mindset Developed

* Cloud does not mean “infinite automatically”
* Systems scale only if designed properly
* Bottlenecks often occur downstream
* Autoscaling controls compute resources
* Pub/Sub prevents data loss
* Dataflow enables distributed processing
* BigQuery is optimized for analytics, not ingestion logic

---

## 9️⃣ Key Technical Vocabulary

* Streaming Architecture
* Low Latency
* Distributed Processing
* Horizontal Scaling
* Autoscaling
* Message Acknowledgment
* Idempotent Processing
* Throughput
* Bottleneck
* Micro-batching

---

## 🔟 Junior-Level Summary Statement

> We designed a streaming analytics pipeline using Pub/Sub for ingestion, Dataflow for distributed real-time processing with autoscaling, and BigQuery for analytical storage. We implemented micro-batching to optimize write throughput and prevent BigQuery bottlenecks. The architecture ensures scalability, reliability, and cost efficiency.
