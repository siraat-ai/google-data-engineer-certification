## What is SaaS?

### Definition
SaaS (Software as a Service) is a cloud-based software delivery model where applications are hosted by a provider and accessed by users over the internet.

### Key Characteristics
- No local installation required
- Subscription-based pricing model
- Multi-tenant architecture (multiple customers share the same infrastructure)
- Automatically scalable
- Managed and maintained by the provider

### Examples
- E-commerce analytics platforms
- CRM systems
- Online accounting software
- Project management tools

### Why SaaS Generates Streaming Data
SaaS platforms continuously generate user interaction data such as clicks, logins, transactions, and API calls. This makes streaming data pipelines essential for real-time analytics and monitoring.

---

# Key Technical Vocabulary – Deep Technical Notes

This document explains core streaming and distributed system concepts in a technically accurate and practical way.

---

## 1️⃣ Streaming Architecture

### Definition
A streaming architecture processes data continuously as events are generated, instead of waiting for large batches.

### Characteristics
- Event-driven
- Continuous processing
- Low latency
- Near real-time analytics

### Example (SaaS)
User clicks → Event sent to Pub/Sub → Processed in Dataflow → Stored in BigQuery → Reflected in dashboard within seconds.

### Why It Matters
Used for:
- Fraud detection
- Real-time dashboards
- Monitoring systems
- Recommendation engines

---

## 2️⃣ Low Latency

### Definition
Latency is the time delay between data generation and data processing.

Low latency means minimal delay.

### Example
If a transaction happens at 10:00:00 and appears in analytics at 10:00:03 → latency = 3 seconds.

### Why It Matters
High latency can:
- Delay fraud detection
- Delay alerts
- Reduce business responsiveness

---

## 3️⃣ Distributed Processing

### Definition
Processing data across multiple machines (workers) simultaneously.

Instead of one machine handling all data, the workload is split.

### Example
1 million events:
- 1 worker → processes sequentially
- 100 workers → process in parallel

### Benefit
- Faster processing
- Better scalability
- Fault tolerance

---

## 4️⃣ Horizontal Scaling

### Definition
Adding more machines (workers) to handle increased load.

Horizontal scaling = scale out.

### Opposite Concept
Vertical scaling = increasing CPU/RAM of one machine.

### Why Cloud Uses Horizontal Scaling
- More flexible
- More reliable
- Better for distributed systems

---

## 5️⃣ Autoscaling

### Definition
Automatic adjustment of computing resources based on traffic or workload.

### In Dataflow
- Adds workers when event rate increases
- Removes workers when traffic decreases

### Benefits
- Performance stability
- Cost optimization
- No manual intervention

---

## 6️⃣ Message Acknowledgment (ACK)

### Definition
Confirmation sent by a subscriber (e.g., Dataflow) to Pub/Sub indicating successful message processing.

### Behavior
- If ACK received → message removed from subscription
- If no ACK → message redelivered

### Why It Matters
Prevents data loss.
Ensures at-least-once delivery.

---

## Subscriber (in Pub/Sub)

### Definition
A subscriber is a component or service that receives and processes messages from a Pub/Sub subscription.

In a GCP streaming architecture, Dataflow commonly acts as a subscriber.

---

### How It Works

1. A message is published to a Pub/Sub topic.
2. A subscription is attached to that topic.
3. The subscriber pulls or receives the message from the subscription.
4. After successful processing, the subscriber sends an acknowledgment (ACK).

---

### Types of Subscriptions

- **Pull Subscription**
  - Subscriber explicitly pulls messages.
  - More control over processing rate.
  - Commonly used with Dataflow.

- **Push Subscription**
  - Pub/Sub pushes messages to an HTTP endpoint.
  - Used for lightweight services or webhooks.

---

### Key Responsibilities of a Subscriber

- Receive messages
- Process messages
- Send acknowledgment (ACK)
- Handle retries if processing fails

---

### Failure Behavior

- If subscriber does NOT send ACK → message is redelivered.
- If subscriber crashes before ACK → message is redelivered.
- If subscriber ACKs successfully → message is removed from subscription.

---

### Why Subscriber Design Matters

- Prevents data loss
- Controls processing speed
- Ensures reliability
- Supports scalable streaming pipelines

---

### Example in Our SaaS System

User click event  
→ Pub/Sub topic  
→ Subscription  
→ Dataflow (Subscriber)  
→ Process event  
→ Send ACK  
→ Store in BigQuery

---

## 7️⃣ Idempotent Processing

### Definition
An operation that produces the same result even if executed multiple times.

### Example
If the same transaction is processed twice:
- Final database state remains correct
- No duplicate revenue counted

### Why It Matters
Streaming systems may re-deliver messages.
Idempotency prevents duplicate effects.

### Simple Explanation of Idempotent Processing

Idempotent processing means:

If the same message or operation is executed multiple times, the final result remains the same.

In simple words:

Even if the system processes the same event again by mistake, it does not create duplicate results or incorrect data.

---

### Easy Example

Suppose a payment of 100 SEK is processed.

If the message is accidentally processed twice:

- Without idempotency → Total becomes 200 SEK ❌
- With idempotency → Total remains 100 SEK ✅

---

### Why It Is Important in Streaming Systems

In systems like Pub/Sub:

- Messages can be redelivered
- Failures can cause retries

If processing is not idempotent:
- Duplicate records
- Wrong revenue numbers
- Incorrect analytics

If processing is idempotent:
- System remains correct
- No duplicate impact
- Safe retries

---

## 8️⃣ Throughput

### Definition
The amount of data processed per unit of time.

Example:
- 10,000 events per second

### High Throughput System
Can handle large event volumes without backlog.

---

## 9️⃣ Bottleneck

### Definition
A component in the system that limits overall performance.

### Example
- BigQuery write limits
- Slow external API
- Insufficient workers

### Engineering Principle
The slowest component determines overall system speed.


In simple words:

Even if the whole system is fast, one slow component can slow down everything.

---

### Engineering Principle

The slowest component determines the overall system speed.

If one part cannot handle the load, the entire pipeline slows down.

---

## 🔹 Example 1: BigQuery Write Limits

### What Does "BigQuery Write Limits" Mean?

BigQuery has limits on how fast data can be written into a table.

If:

- Too many rows are inserted per second
- Too many streaming insert requests are sent
- Too many small write operations happen

Then BigQuery may:

- Slow down writes
- Return errors
- Create delays

### Why This Becomes a Bottleneck

If Dataflow processes data very fast  
but BigQuery cannot accept writes at the same speed,

Then:

Dataflow will start waiting  
Backlog may increase  
Latency will increase  

The warehouse becomes the limiting factor.

---

## 🔹 Example 2: Slow External API

### What is an API?

API = Application Programming Interface

It is a way for one system to communicate with another system.

Example:
- Your pipeline calls a currency exchange API
- Or calls a fraud detection service
- Or fetches user data from another service

### What Happens If the API Is Slow?

If:

- Each API call takes 2 seconds
- And you are processing 10,000 events per second

Then:

Workers must wait for the API response  
Processing slows down  
Throughput decreases  

Even if Pub/Sub and Dataflow are fast,  
the slow API becomes the bottleneck.

---

## 🔹 Example 3: Insufficient Workers

### What Does "Insufficient Workers" Mean?

Workers are virtual machines that process data in parallel.

If:

- Event rate increases
- But worker count remains low
- Or autoscaling is disabled

Then:

Each worker gets too much data  
Processing becomes slow  
Pub/Sub backlog increases  

### Simple Explanation

Imagine:

1 cashier handling 1000 customers  
vs  
10 cashiers handling 1000 customers  

More workers = more parallel processing.

If workers are not enough, the processing layer becomes the bottleneck.

---

## 🧠 Key Understanding

A bottleneck is not about total system power.

It is about imbalance.

If one component cannot match the speed of others,  
it limits the entire pipeline.

---

## 🎯 Real SaaS Example

If your system handles:

- 50,000 events per second in Pub/Sub  
- 50,000 events per second in Dataflow  

But BigQuery can only handle:

- 10,000 writes per second  

Then BigQuery becomes the bottleneck.

The whole system effectively runs at 10,000 per second.

---

## 🔟 Micro-batching

### Definition
Collecting small groups of events and processing them together instead of individually.

### Example
Instead of writing 1 event at a time to BigQuery:
- Collect 500 events
- Write in a single batch

### Benefits
- Reduced API calls
- Higher throughput
- Lower cost
- Better efficiency

---

# Final Engineering Summary

A well-designed streaming system:
- Uses distributed processing
- Scales horizontally
- Enables autoscaling
- Handles acknowledgments correctly
- Ensures idempotent processing
- Monitors throughput
- Identifies bottlenecks early
- Uses micro-batching for optimization

These concepts form the foundation of production-grade GCP data engineering.

