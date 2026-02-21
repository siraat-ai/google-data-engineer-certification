# Exactly-Once Processing – Technical Learning Notes

---

## Introduction

In streaming systems, especially in financial pipelines, it is critical to ensure that each transaction is processed exactly one time.

Exactly-once processing does not simply mean that a message is delivered once. It means that the final logical result of processing happens only once, even if failures or retries occur.

Achieving true exactly-once behavior requires multiple techniques working together.

---

# 1️⃣ Idempotent Processing

## Definition

Idempotent processing means that if the same transaction is processed multiple times, the final result remains the same.

## Why It Is Important

Streaming systems may redeliver messages due to:

- Network failures
- Worker crashes
- Retries
- Acknowledgment timeouts

If processing is not idempotent, duplicate messages can cause incorrect results.

## Example

Transaction ID: TX1001  
Amount: 1000 SEK

If processed twice:

- Without idempotency → 2000 SEK deducted ❌
- With idempotency → Still 1000 SEK deducted ✅

## How It Is Implemented

- Use unique transaction IDs
- Check if transaction ID already exists before applying changes
- Use database constraints (e.g., primary keys)

---

# 2️⃣ Deduplication Logic

## Definition

Deduplication logic detects and removes duplicate messages before applying business logic.

## Why It Is Needed

Pub/Sub and other messaging systems typically provide at-least-once delivery. This means messages can be delivered more than once.

Deduplication ensures that duplicates do not affect downstream systems.

## Common Techniques

- Store processed message IDs
- Use window-based deduplication in Dataflow
- Compare event timestamps and unique keys

---

# 3️⃣ Transactional Sinks

## Definition

A transactional sink is a storage system that supports atomic and consistent writes.

Atomic means:
- Either the entire write succeeds
- Or nothing is written

## Why It Is Important

If a system crashes during a write operation, transactional sinks prevent partial updates.

Examples:

- BigQuery with proper streaming design
- Cloud Spanner
- Relational databases with transactions

Transactional sinks help maintain data consistency.

---

# 4️⃣ Checkpointing

## Definition

Checkpointing is a mechanism where the processing system periodically saves its progress state.

## Why It Matters

If Dataflow crashes:

- It can restart from the last checkpoint
- It does not need to reprocess all historical data
- It avoids duplicate processing effects

Checkpointing improves fault tolerance and recovery.

---

# 5️⃣ Message Acknowledgment Handling

## Definition

Acknowledgment (ACK) confirms that a message has been successfully processed.

## Behavior

- If ACK is sent → message removed from subscription
- If no ACK → message redelivered

Correct acknowledgment timing is critical.

ACK should only be sent after successful processing and writing to the sink.

---

# 6️⃣ Exactly-Once System Concept

Exactly-once processing is achieved by combining:

- Idempotent business logic
- Deduplication
- Checkpointing
- Reliable message acknowledgment
- Transactional sinks

It is not a single feature. It is a system design pattern.

---

# Practical Financial Pipeline Example

1. Transaction published to Pub/Sub
2. Dataflow receives message
3. Deduplication logic checks transaction ID
4. Business logic processes transaction
5. Write to transactional sink (e.g., BigQuery or database)
6. Send acknowledgment
7. Checkpoint state updated

If failure occurs:

- Message may be redelivered
- Idempotency prevents duplicate effect
- Checkpointing restores correct state

---

# Interview-Level Summary

Exactly-once processing in streaming systems is achieved through a combination of idempotent logic, deduplication strategies, transactional storage systems, checkpointing, and careful acknowledgment handling. It ensures that each financial transaction produces only one logical result, even in the presence of retries or failures.

---

# Final Understanding

Exactly-once is not magic.
It is disciplined system design.

In production-grade financial systems, these mechanisms work together to ensure correctness, reliability, and data integrity.

