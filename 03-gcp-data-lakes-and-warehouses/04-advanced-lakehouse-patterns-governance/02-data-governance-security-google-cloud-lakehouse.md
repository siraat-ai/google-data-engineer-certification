# 🔐 Data Governance & Security in a Unified Lakehouse Platform

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AAc9VnxBYNMA3CPd7MdiHdg.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A926/0%2AckFGKc_OF2xKNqIv)

![Image](https://docs.cloud.google.com/static/sensitive-data-protection/docs/images/concepts-method-types-storagemethods.svg)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/C8veVnYPHRp6cjC.max-2100x2100.png)

---

## 🧠 Why Governance Matters for Cymbal

**Mr. X the Curious Learner:**
“Cymbal is a global online retailer handling customer data, sales, and inventory. Why is data governance treated as a *business function*, not just a technical task?”

**Mr. Artificial King, the Calm Guider:**
“When data drives personalized marketing and supply chain efficiency, **accuracy, discoverability, and security** directly impact revenue, trust, and compliance. Governance ensures data is **usable and safe at scale**.”

---

## 🗂️ Dataplex — The Metadata Hub

### Why Metadata Matters

**Mr. X:**
“Everyone keeps saying *metadata*. Why is it so important?”

**Mr. Artificial King:**
“Metadata is simply **data about data**. It tells you:”

* Who created the data
* When it was created
* What it contains
* How it relates to other data
* Who owns it
* How sensitive it is

📌 Without metadata, data quickly becomes unusable chaos.

---

### Dataplex for Cymbal

**Mr. X:**
“How does Cymbal manage metadata across so many systems?”

**Mr. Artificial King:**
“They use **Dataplex** as a **central metadata hub**.”

### What Dataplex Does

* Acts as a **universal catalog**
* Covers data in:

  * **BigQuery**
  * **Google Cloud Storage**
  * **BigLake**
* Enables:

  * Data discovery
  * Lineage tracking
  * Metadata management

📊 Analysts find and understand datasets **without hunting across systems**.

---

### Business Impact of Dataplex

**Mr. Artificial King:**
“By acting as a single reference source, Dataplex helps Cymbal:”

* Govern data consistently
* Improve data quality
* Scale data management confidently

---

## 🔎 Sensitive Data Protection

**Mr. X:**
“Cymbal stores names, addresses, and credit card numbers. How do they protect that?”

**Mr. Artificial King:**
“They use **Sensitive Data Protection**.”

This tool automatically **discovers, classifies, and protects sensitive data** across the lakehouse.

---

### 1️⃣ Discovery

* Scans:

  * BigQuery tables
  * Cloud Storage buckets
* Detects patterns like:

  * Credit card numbers
  * Email addresses
  * Phone numbers

---

### 2️⃣ Classification

* Identified data is labeled by **sensitivity level**
* Ensures the right controls are applied automatically

---

### 3️⃣ Protection

**Mr. Artificial King:**
“Once classified, Cymbal protects data using techniques like:”

* Masking
* Tokenization

### Example

* Support agent sees: `XXXX-XXXX-XXXX-1234`
* Real credit card number is never exposed

✅ Privacy preserved
✅ Compliance supported
✅ Trust maintained

---

## 👤 Identity and Access Management (IAM)

**Mr. X:**
“How does Cymbal control *who* can access *what*?”

**Mr. Artificial King:**
“With **Identity and Access Management (IAM)**, following the **principle of least privilege**.”

---

### IAM by Service

#### ☁️ Cloud Storage

* Access at **bucket level**
* Restricted to:

  * Engineers
  * Service accounts for ingestion

#### 📊 BigQuery

* Granular control at:

  * Dataset level
  * Table level
* Examples:

  * Analysts → read-only curated data
  * Data scientists → write access in sandbox datasets

#### 🌊 BigLake

* Extends **BigQuery security controls** to Cloud Storage data
* Major advantage for lakehouse governance

---

## 🔐 Fine-Grained Security Controls

**Mr. X:**
“What if access needs to be even more specific?”

**Mr. Artificial King:**
“Cymbal uses **row-level and column-level security**.”

### Column-Level Security

* Restricts specific columns
* Example:

  * Marketing can see purchase history
  * Cannot see contact details or PII

### Row-Level Security

* Restricts which rows a user can access
* Example:

  * North America manager sees only NA sales data

📌 Ideal for global organizations like Cymbal.

---

## 🎭 Dynamic Data Masking (Simple Flow)
<img width="4642" height="1291" alt="image" src="https://github.com/user-attachments/assets/e9f1a040-0bcb-44c8-aaa0-97a93646a782" />


Here is the **plain-text masking flow**, step by step:

1. **Raw data stored**
   Example: `068-760-365`

2. **Data is accessed**
   ETL job, query, or report reads the field

3. **Masking rule applied**
   Sensitive parts are hidden or replaced

4. **Masked data produced**
   `XXX-XXX-XXX`

5. **Masked data used**
   Analysts and reports never see real values

✅ Security
✅ Privacy
✅ Compliance

---

## 🌟 Key Takeaway

**Mr. Artificial King:**
“By combining Dataplex, Sensitive Data Protection, IAM, and BigLake security, Cymbal achieves **centralized governance without sacrificing flexibility**.”

> **A unified lakehouse platform where data is discoverable, secure, and trusted.**

---

## ⏭️ What’s Next

The next lesson demonstrates how to **use Sensitive Data Protection to discover Personally Identifiable Information (PII)** in real datasets.

---

### 📁 Suggested GitHub Filename

`data-governance-security-google-cloud-lakehouse.md`
