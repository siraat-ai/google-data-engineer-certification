Streaming Job Updates and Core Dataflow Concepts (Google Data Engineering Prep)

These notes explain all key technical concepts referenced in the previous discussion, with deeper context tailored for Google Cloud Data Engineering certification preparation.

1. Dataflow Pipeline
What Is a Dataflow Pipeline?

A Dataflow pipeline is a data processing workflow built using the Apache Beam programming model and executed on Google Cloud Dataflow.

It consists of:

Sources (where data enters)

Transforms (how data is processed)

Sinks (where data is written)

Two Types of Pipelines:
Type	Description	Example
Batch pipeline	Processes finite datasets	Daily log processing
Streaming pipeline	Processes unbounded, continuous data	Real-time clickstream processing
Exam Insight

Streaming pipelines require careful handling of:

Checkpointing

State

Watermarks

Exactly-once semantics

2. Streaming Pipeline
What Is Streaming?

A streaming pipeline processes continuous, unbounded data in real time or near real time.

Examples:

IoT sensor events

Financial transactions

Log streams

Pub/Sub messages

Unlike batch jobs, streaming jobs:

Never “finish”

Continuously consume data

Maintain internal state

3. BigQuery (Streaming Sink)
What Is BigQuery?

BigQuery is Google Cloud’s fully managed, serverless data warehouse designed for analytics.

In streaming systems:

Dataflow often writes streaming data into BigQuery.

BigQuery supports streaming inserts.

Schema consistency must be maintained.

Important for Exam

Understand streaming inserts vs batch loads.

Understand how schema updates affect streaming pipelines.

Know how Dataflow integrates with BigQuery.

4. Transformation Logic
What Are Transformations?

Transformations modify, enrich, filter, or aggregate data.

Examples:

Mapping fields

Filtering invalid records

Aggregating counts

Joining streams

In Apache Beam:

ParDo

GroupByKey

Window

Combine

Why Updating Transformations Is Tricky

Streaming pipelines may:

Maintain keyed state

Use windowing logic

Depend on schema stability

Changing transformation logic can affect:

State compatibility

Checkpoints

Output format

5. Long-Running Streaming Job

Streaming jobs:

Run continuously

Maintain processing checkpoints

Track offsets from data sources

Maintain internal state

They differ from batch jobs because:

They cannot simply restart without risk

They may reprocess data if improperly restarted

6. Job State
What Is Job State?

Job state refers to internal processing memory maintained by the pipeline, such as:

Current offsets (e.g., Pub/Sub acknowledgment tracking)

Aggregation state

Window buffers

Timers

If job state is lost:

Duplicate processing may occur

Data may be lost

Windows may reset

Certification Tip

Understand how Dataflow:

Checkpoints progress

Recovers from failures

Preserves state during updates

7. Checkpointing

Checkpointing allows a streaming job to:

Periodically save progress

Resume from last known good state

Avoid reprocessing all data

In Dataflow:

Managed automatically

Critical for fault tolerance

Enables safe updates

8. In-Place Job Update
What Is an In-Place Update?

An in-place update modifies a running streaming job without stopping it.

This is done using:

The same job name

Same region

Update flag enabled

What Happens Internally?

The job’s state is preserved

Workers are gradually replaced

Transform logic is updated

Checkpoints remain intact

Why It’s Important

Without in-place updates:

Stopping the job may cause data loss

Starting a new job may cause duplication

Exam Insight

Use in-place updates when:

Updating transformation logic

Keeping same input and output

Maintaining streaming continuity

9. Job Identity (jobName and region)
Why Job Name Matters

The job name identifies the running Dataflow job.

For an update:

You must use the same job name

You must specify the same region

This tells Dataflow:

“Update the existing job instead of creating a new one.”

If you change job name:

A new job is created

State is not reused

Risk of duplicate processing

10. Data Duplication
How Duplication Happens

Duplication occurs when:

Two jobs read the same source simultaneously

A job restarts without preserved state

Offsets are not properly tracked

Streaming sources like Pub/Sub provide:

At-least-once delivery

Message redelivery if not acknowledged

Improper pipeline updates may cause:

Reprocessing of already-consumed messages

11. Data Loss

Data loss can occur if:

A job is abruptly cancelled

Messages are acknowledged before processing

State is not preserved during update

Streaming systems must carefully balance:

Acknowledgment timing

Processing guarantees

Fault tolerance

12. Drain vs Cancel (Pipeline Shutdown Methods)
Drain

Drain:

Stops accepting new data

Finishes processing buffered data

Gracefully shuts down

Used when:

Permanently stopping a job

Ensuring all in-flight data is processed

Downside:

Takes time

Causes downtime

Cancel

Cancel:

Immediately stops the job

May leave in-flight data unprocessed

Faster but riskier

Used when:

Emergency termination

Non-critical workloads

13. Minimal Downtime

In real-time systems:

Even short interruptions can cause gaps

Analytics dashboards may show incomplete data

SLAs may be violated

In-place updates minimize:

Service disruption

Operational complexity

Data inconsistencies

14. Streaming Continuity

Streaming continuity means:

Data ingestion never stops

No message gaps

No reprocessing overlaps

Output remains consistent

Best achieved using:

State-preserving updates

Managed checkpointing

Proper job configuration

15. Apache Beam (Underlying Model)

Google Cloud Dataflow executes pipelines written in Apache Beam.

Beam concepts relevant for certification:

PCollection

Windowing

Triggers

Watermarks

State & timers

Understanding Beam helps explain:

Why state must be preserved

Why updates must be compatible

How streaming semantics work

16. Exactly-Once vs At-Least-Once Semantics
At-Least-Once

Messages may be delivered multiple times.

Must handle deduplication.

Exactly-Once

Each event processed exactly once.

More complex to guarantee.

Dataflow aims for:

Exactly-once processing within the pipeline

Depending on source/sink capabilities

Exam tip:
Understand how Pub/Sub + Dataflow + BigQuery interact for delivery guarantees.

17. Best Practice Summary for Exam

When updating a running streaming pipeline:

✔ Use in-place update
✔ Keep same job name and region
✔ Preserve state
✔ Avoid stopping and recreating jobs

Avoid:
✘ Canceling abruptly
✘ Creating parallel duplicate pipelines
✘ Changing incompatible state logic without migration plan

Final Conceptual Takeaway

Streaming systems are stateful, continuous, and sensitive to interruptions.

For certification preparation, remember:

In streaming architectures, updating safely means preserving state, maintaining checkpoint integrity, and avoiding duplication or data loss.

Understanding these core principles will help you solve scenario-based questions involving:

Dataflow streaming jobs

Production pipeline updates

Fault tolerance

Delivery guarantees

Operational best practices

