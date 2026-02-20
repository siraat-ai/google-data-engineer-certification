# BigQuery Table Design for Streaming SaaS System

---

## 1️⃣ Single Events Table Strategy

### Concept

In most streaming SaaS architectures, we store all events in **one main table** called something like:

`events`

Instead of creating separate tables for:
- clicks
- cart
- payments

We store all events together and differentiate them using:

`event_type` column

---

### Example Schema

events table:

- user_id (STRING)
- product_id (STRING)
- event_type (STRING)   -- click, cart, payment
- amount (FLOAT)        -- nullable (only for payments)
- country (STRING)
- timestamp (TIMESTAMP)

---

### Why Use a Single Table?

- Simpler ingestion pipeline
- Easier streaming writes
- Better scalability
- Lower operational complexity
- Common pattern in real production systems

This is called:

**Append-only event table design**

---

# 2️⃣ Partitioned Tables

## What is Partitioning?

Partitioning splits a large table into smaller logical pieces based on a column.

In streaming systems, we usually partition by:

`timestamp`

Example:
- 2026-02-18 partition
- 2026-02-19 partition
- 2026-02-20 partition

---

## Why Partition by Timestamp?

Because most queries filter by date:

Example:

```sql
SELECT *
FROM events
WHERE DATE(timestamp) = '2026-02-20'
