

### Using SQL to Predict Customer Churn

**Mr. X the Curious Learner:**
“At Cymbal E-commerce, we already have tons of customer data in BigQuery. I want to predict customer churn, but I’m not a hardcore ML engineer. Is there a way to build machine learning models **directly using SQL**?”

**Mr. Artificial King, the Calm Guider:**
“Yes. **BigQuery ML** allows data analysts to **build, train, and deploy machine learning models using simple SQL queries**, without leaving BigQuery.”

---

### Keeping Track of All Data in the Lakehouse

**Mr. X the Curious Learner:**
“Our data is spread across BigQuery, Cloud Storage, and BigLake. I’m worried about losing visibility and governance. What service helps us **catalog and manage all data assets centrally**?”

**Mr. Artificial King, the Calm Guider:**
“That’s the role of **Dataplex**. It acts as a **universal catalog**, organizing and governing data across BigQuery, Cloud Storage, and BigLake.”

---

### Managing PII the Right Way

**Mr. X the Curious Learner:**
“To meet privacy regulations, we need a structured way to handle Personally Identifiable Information (PII). What are the **core steps** involved in Sensitive Data Protection?”

**Mr. Artificial King, the Calm Guider:**
“The process focuses on **Discovery, Classification, and Protection**—first finding sensitive data, then identifying its type, and finally securing it.”

---

### Protecting Emails Without Losing Insights

**Mr. X the Curious Learner:**
“I want to protect customer email addresses, but analysts still need to count unique customers. The data should be hidden and **not reversible**. What transformation works best?”

**Mr. Artificial King, the Calm Guider:**
“Use **tokenization with a cryptographic hash**. It replaces emails with consistent tokens, preserving uniqueness without revealing the original data.”

---

### Hiding Sensitive Columns from Analysts

**Mr. X the Curious Learner:**
“Our marketing analyst needs access to customer data but must not see contact details like email or phone numbers. What’s the **most effective security control** for this?”

**Mr. Artificial King, the Calm Guider:**
“**Column-level security** is the best solution. It restricts access to sensitive columns while allowing visibility into the rest of the table.”

---

### Where Analytics-Ready Data Lives

**Mr. X the Curious Learner:**
“In the Medallion Architecture, data flows through multiple refinement stages. Where does the **final, business-ready data** live?”

**Mr. Artificial King, the Calm Guider:**
“That data belongs in the **Gold Zone**, which contains highly refined, aggregated data optimized for analytics and reporting.”

---

### When BigQuery ML Isn’t Enough

**Mr. X the Curious Learner:**
“For advanced use cases like a custom product recommendation engine, SQL-based ML feels limiting. Which service gives data scientists a **full end-to-end ML platform**?”

**Mr. Artificial King, the Calm Guider:**
“For complex and custom ML workloads, **Vertex AI** is the right choice. It integrates seamlessly with BigQuery and supports the full ML lifecycle.”

---

### Starting a Machine Learning Model in BigQuery

**Mr. X the Curious Learner:**
“When I’m ready to train a new machine learning model in BigQuery ML, which SQL statement actually **starts the training process**?”

**Mr. Artificial King, the Calm Guider:**
“You begin model training with the **CREATE MODEL** statement.”

---


