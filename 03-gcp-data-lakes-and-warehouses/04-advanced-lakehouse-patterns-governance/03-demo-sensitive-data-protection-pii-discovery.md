# 🛡️ Demo: Data Loss Prevention with Sensitive Data Protection

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/First-Image.max-1400x1400.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/cloud_dlp_lWJX44E.max-1200x1200.jpg)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/fig_1.max-2000x2000.jpg)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/fig_2.max-2000x2000.jpg)

---

## 🧠 Lesson Context

**Mr. X the Curious Learner:**
“Cymbal just launched a new loyalty program, and now they’ve collected a lot of customer data. Before analysts start using it, how do we make sure no sensitive information leaks out?”

**Mr. Artificial King, the Calm Guider:**
“That’s where **Sensitive Data Protection** comes in. This demo shows how to **discover and track Personally Identifiable Information (PII)** before the data is exposed to analytics users.”

---

## 🎯 Demo Goal

This hands-on demo focuses on **discovery** capabilities of **Sensitive Data Protection**:

* Identify sensitive fields automatically
* Understand where PII exists
* Reduce the risk of accidental data exposure

📌 We are **not masking or de-identifying yet** — only discovering and reporting.

---

## 🗃️ Scenario: Loyalty Program Data

**Mr. Artificial King:**
“Cymbal has loaded a new dataset into **BigQuery**.”

### Table Details

* **Table name:** `loyalty_program_customers`
* **Data includes:**

  * Names
  * Purchase history
  * Email addresses
  * Phone numbers
  * Free-text customer feedback

⚠️ This table contains **potential PII** and must be reviewed before marketing can use it.

---

## 🔍 Step 1: Discovery Setup (High-Level)

**Mr. X:**
“How do we start finding sensitive data?”

**Mr. Artificial King:**
“We begin in the **Sensitive Data Protection** console and configure a **discovery scan**.”

### Supported Data Sources

* BigQuery
* Cloud Storage
* Cloud SQL
* Vertex AI datasets

📌 In this demo, we focus on **BigQuery**, the hub of the lakehouse.

---

## ⚙️ Step 2: Configuring the Discovery Scan

### Key Configuration Choices

**Mr. Artificial King explains:**

1. **Select data source**

   * BigQuery

2. **Scope of scan**

   * Scan **one specific table** (not the entire project)

3. **Dataset & table**

   * Dataset: `BQLab`
   * Table: `users`

4. **Discovery frequency**

   * Default (runs on change or when saved)

---

## 🧪 Step 3: Inspection Templates

**Mr. X:**
“What exactly does it look for?”

**Mr. Artificial King:**
“You choose an **inspection template** that defines what sensitive data types to scan.”

### Examples of Detectors

* Email addresses
* Phone numbers
* Credit cards
* Government IDs
* Dates of birth
* National identifiers

📌 In this demo, **all detectors** are enabled for maximum coverage.

---

## 🎛️ Step 4: Rule Sets & Actions

### Likelihood Thresholds

* Very likely
* Likely
* Somewhat likely
* Unlikely

💡 Helps filter noise and focus on truly sensitive fields.

### Actions

* Publish discovery results to **BigQuery tables**
* Enables easy review and reporting

---

## ▶️ Running the Discovery Job

**Mr. Artificial King:**
“Once configured, you click **Create**, and the job runs automatically.”

In this demo:

* The scan was already run previously
* Results are stored and ready to review in BigQuery

---

## 📊 Step 5: Reviewing Results in BigQuery

**Mr. X:**
“What do the results look like?”

**Mr. Artificial King:**
“Sensitive Data Protection generates several **output tables**.”

### Key Output Tables

#### 1️⃣ Source Table (`users`)

* Contains:

  * Names
  * Address
  * City, state, postal code
* Synthetic sample data (for demo purposes)

---

#### 2️⃣ User Samples

* Shows **sample values** of detected sensitive fields
* Helps validate detection accuracy

---

#### 3️⃣ Run Information

* Metadata about:

  * Scan time
  * Configuration
  * Status

---

#### 4️⃣ User Risk

* Indicates **risk level**
* Helps prioritize remediation

---

#### 5️⃣ Inspection Results

* Most detailed output
* Shows:

  * Column name
  * Type of sensitive data
  * Likelihood score

📌 Without manually checking every column, teams instantly see **where PII exists**.

---

## 🌍 Works Across the Entire Lakehouse

**Mr. Artificial King:**
“One powerful thing to remember:”

> Sensitive Data Protection works whether data is:

* In BigQuery native tables
* In Iceberg tables via **BigLake**
* In Cloud Storage
* In transactional databases

🔍 One discovery tool
🔐 One governance view

---

## 🧠 Key Takeaway

**Mr. Artificial King:**
“This demo shows how you can **identify sensitive data at scale** before it becomes a risk.”

> **You can’t protect what you can’t see — discovery is the first step to strong data governance.**

---

## ⏭️ What’s Next

In the next lesson, you’ll learn how to **build machine learning models directly on lakehouse data** using BigQuery ML and Vertex AI.

---

### 📁 Suggested GitHub Filename

`demo-sensitive-data-protection-pii-discovery.md`
