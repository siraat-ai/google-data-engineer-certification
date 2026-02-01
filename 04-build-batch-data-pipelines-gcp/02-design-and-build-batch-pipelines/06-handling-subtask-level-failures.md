# ⚠️ When Failures Happen in Distributed Batch Pipelines

![Image](https://substackcdn.com/image/fetch/%24s_%21PY1d%21%2Cf_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F748b6ba3-9a97-47af-b0e9-35d6008fcf38_1099x573.png)

![Image](https://substackcdn.com/image/fetch/f_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8a8f6a06-24d2-424a-8cb9-b20f7801fbf6_1866x954.png)

![Image](https://docs.databricks.com/aws/en/assets/images/expectations-flow-graph-02ab5dd2011b18ad791c67c0e8449af6.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1358/format%3Awebp/0%2AGBNyDbncZpNc24Z5)

---

## 🧠 Not All Failures Are the Same

**Mr. X the Curious Learner:**
“I thought any failed task could just be retried on another worker. But I’m hearing that’s not always true?”

**Mr. Artificial King, the Calm Guider:**
“Correct. **Where the failure happens matters**. Some failures are about *workers*, others are about the *data or subtask itself*. Only the first type can be fixed automatically by reassignment.”

---

## ❌ Failure *Before* Processing Starts (Subtask-Level Failure)

This scenario occurs **between the larger task and a subtask**.

### What This Means

* The **subtask definition itself is faulty**
* Or the **data assigned to that subtask is corrupted or invalid**
* The failure happens *before* any worker can successfully process it

📌 Because the problem is with the **subtask or its data**, reassigning it to another worker **won’t help**.

---

## 🔍 Why Reassignment Doesn’t Work Here

**Mr. Artificial King:**
“If the data chunk itself is broken, every worker will fail in the same way.”

Examples:

* Corrupted files
* Schema violations
* Invalid data ranges
* Logical contradictions in the data

👉 This is fundamentally different from a worker crash or timeout.

---

## 🛠️ How Systems Handle This Type of Failure

When the issue lies with the **subtask/data**, systems typically take one (or more) of the following actions:

---

### 📝 1. Error Reporting & Logging (Always)

**Mr. Artificial King:**
“The first step is visibility.”

* The system logs:

  * Which subtask failed
  * Which data range caused the issue
  * The error details
* Alerts may be triggered for operators

📌 This is essential for diagnosis and auditing.

---

### ⏭️ 2. Skipping the Subtask (Conditional)

**Mr. X:**
“Can the pipeline just skip it?”

**Mr. Artificial King:**
“Sometimes—but only if the business allows it.”

* Used in **non-critical pipelines**
* May be acceptable for:

  * Exploratory analytics
  * Non-financial reports

🚫 Rarely acceptable for:

* Financial reporting
* Billing
* Audits

📌 Skipping trades completeness for availability.

---

### 👩‍💻 3. Human Intervention & Data Curation (Most Common)

**Mr. Artificial King:**
“In critical pipelines, this is the usual resolution.”

* Engineers or analysts:

  * Inspect the raw data
  * Fix corruption or schema issues
  * Correct transformation logic
* The job is then:

  * Re-run fully, or
  * Re-run for the affected subtask

📌 This preserves **data correctness and trust**.

---

## 🆚 Compare: Subtask Failure vs Worker Failure

| Failure Type         | Cause                      | Can Reassign? | Typical Resolution                |
| -------------------- | -------------------------- | ------------- | --------------------------------- |
| Worker-level failure | Crash, timeout, node issue | ✅ Yes         | Retry on another worker           |
| Subtask/data failure | Bad data or logic          | ❌ No          | Log, fix data, human intervention |

---

## 🌟 Big Picture Insight

**Mr. Artificial King:**
“Fault tolerance doesn’t mean *everything* is automatic.”

> **Distributed systems can recover from infrastructure failures automatically—but data quality failures often require human judgment.**

---

## 🧠 Final Takeaway

> **When a failure occurs at the subtask or data-definition level, reassignment to another worker won’t fix the issue. These failures require logging, possible skipping (if allowed), or human intervention to correct the data or logic before the pipeline can complete successfully.**

---

### 📁 Suggested GitHub Filename

`handling-subtask-level-failures.md`
