# GCP Streaming & Processing Technologies – Deep Learning Notes

This document provides independent, technical explanations of major Google Cloud streaming and data processing technologies. Each section explains what the technology is, how it works, and where it is used in real-world systems.

---

# 1️⃣ Google Cloud Dataflow

## What It Is

Google Cloud Dataflow is a fully managed stream and batch data processing service based on the Apache Beam programming model.

It allows developers to build data pipelines that can process both real-time (streaming) and batch data at large scale.

## How It Works

- Developers write pipelines using Apache Beam (Java, Python, etc.).
- The pipeline is submitted to Dataflow.
- Dataflow automatically provisions worker VMs.
- Workers process data in parallel.
- Autoscaling adjusts the number of workers based on workload.

## Key Features

- Horizontal scaling
- Automatic resource management
- Checkpointing
- Fault tolerance
- Windowing and triggering for streaming

## Common Use Cases

- Real-time event processing
- Fraud detection
- Log analytics
- ETL pipelines

---

# 2️⃣ Cloud Pub/Sub (Ingestion Layer)

## What It Is

Cloud Pub/Sub is a fully managed messaging service used for event ingestion and asynchronous communication between systems.

## How It Works

- A producer publishes messages to a topic.
- A subscription is attached to the topic.
- Subscribers receive messages from the subscription.
- Subscribers acknowledge (ACK) messages after processing.

## Key Characteristics

- At-least-once delivery
- Global scalability
- Message retention
- Loose coupling between systems

## Why It Is Used as an Ingestion Layer

It buffers traffic spikes and decouples producers from processing systems.

---

# 3️⃣ Pub/Sub Ordering

## What It Is

Pub/Sub message ordering ensures that messages with the same ordering key are delivered in the order they were published.

## How It Works

- Publisher assigns an ordering key to messages.
- Pub/Sub ensures ordered delivery per key.
- Ordering is guaranteed only within the same key.

## Why It Matters

Important for financial transactions where sequence affects correctness (e.g., deposit before withdrawal).

---

# 4️⃣ Google Cloud Dataprep

## What It Is

Cloud Dataprep is a data preparation tool used for cleaning and transforming structured data.

## How It Works

- Users interact through a visual interface.
- Data transformations are defined without heavy coding.
- Typically used for batch transformations.

## Characteristics

- UI-driven data wrangling
- Schema detection
- Transformation suggestions

## Limitations

Not designed for large-scale low-latency streaming systems.

---

# 5️⃣ Cloud Storage (Ingestion Layer)

## What It Is

Cloud Storage is a scalable object storage service for storing files such as CSV, JSON, images, backups, etc.

## How It Works

- Data is stored in buckets.
- Objects are immutable once written (unless overwritten).
- Supports lifecycle management and versioning.

## Use Case as Ingestion

Used primarily for batch ingestion (file-based pipelines), not real-time streaming.

---

# 6️⃣ Cloud Storage Object Versioning

## What It Is

Object versioning stores previous versions of objects when they are overwritten or deleted.

## How It Works

- Each object update creates a new version.
- Older versions remain accessible.

## Purpose

- Protect against accidental deletion
- Maintain data history
- Improve recovery reliability

---

# 7️⃣ Google Cloud Dataproc

## What It Is

Cloud Dataproc is a managed Hadoop and Spark cluster service.

## How It Works

- Users create clusters with configurable VM sizes.
- Run Spark, Hadoop, or other distributed jobs.
- Clusters can be long-running or ephemeral.

## Characteristics

- More infrastructure control
- Higher operational responsibility
- Suitable for custom Spark workloads

---

# 8️⃣ Spark Streaming

## What It Is

Spark Streaming is a stream processing component of Apache Spark.

## How It Works

- Uses micro-batching approach.
- Incoming data is divided into small time-based batches.
- Each batch is processed as a small job.

## Characteristics

- Low-latency but not true event-by-event streaming
- Requires cluster management

---

# 9️⃣ Google Cloud Composer

## What It Is

Cloud Composer is a managed Apache Airflow service used for workflow orchestration.

## How It Works

- Define DAGs (Directed Acyclic Graphs).
- Schedule and coordinate tasks.
- Manage dependencies between jobs.

## Purpose

Orchestration tool — not a streaming ingestion or processing engine.

---

# 🔟 Apache Beam

## What It Is

Apache Beam is an open-source unified programming model for batch and streaming data processing.

## How It Works

- Developers write pipeline code using Beam SDK.
- The code runs on a runner (e.g., Dataflow).

## Core Concepts

- PCollections
- Transforms
- Windowing
- Triggers

Beam enables portability across processing engines.

---

# 1️⃣1️⃣ At-Least-Once Delivery Semantics

## Definition

At-least-once delivery means that each message is delivered one or more times.

## Implication

- Messages may be duplicated.
- System must handle duplicates safely.

## Where It Is Common

- Pub/Sub
- Many distributed messaging systems

## Risk

Without idempotent logic, duplicates can cause incorrect results.

---

# Final Understanding

Modern streaming architectures combine:

- Messaging systems (Pub/Sub)
- Processing engines (Dataflow, Spark)
- Storage systems (BigQuery, Cloud Storage)
- Orchestration tools (Composer)

Each technology has a distinct role in scalable and fault-tolerant data systems.

Understanding how they work individually is critical before designing production pipelines.

