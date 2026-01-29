# Diagnostic Questions: Storing the Data (Explained)

## Designing BigQuery Schema for Analytics
**Mr. X:** We’re moving transactional database tables into BigQuery so analysts can explore them. Should we keep the same schema?  
**Mr. Artificial King:** BigQuery is optimized for analytics, not transactions. For analytics, **denormalized schemas** work best. Using **nested and repeated fields** reduces joins and improves query performance.

**✔ Correct Approach:** Redesign the schema to denormalize the data with nested and repeated data.

## Improving Data Understanding and Ownership
**Mr. X:** Analysts don’t understand what columns mean or who owns the data. Searching data is also hard. What can we do?  
**Mr. Artificial King:** This is a metadata and governance problem. **Cloud Catalog** allows you to tag datasets, tables, and columns with ownership and business meaning, making data searchable and understandable.

**✔ Correct Approach:** Create tags for data entries in Cloud Catalog.

## Cost-Effective Long-Term Data Storage
**Mr. X:** Our data is heavily used in the first month, then mostly kept for audits years later. How do we save costs?  
**Mr. Artificial King:** This is a classic lifecycle-based storage problem. With **Cloud Storage lifecycle policies**, data can automatically move to cheaper storage classes over time.

**✔ Correct Approach:** Configure a lifecycle policy on Cloud Storage.

## Reducing Repeated Query Effort in BigQuery
**Mr. X:** Analysts keep running the same complex queries again and again. Data changes often. How can we make their work easier?  
**Mr. Artificial King:** A **BigQuery view** stores the query logic, not the data. Analysts can query the view directly and always get fresh results without rewriting complex SQL.

**✔ Correct Approach:** Create a view of the frequently queried data.

## Choosing a Transactional Database with Low Admin Overhead
**Mr. X:** We need a transactional database. Users are mostly in one region, and we don’t want to manage infrastructure.  
**Mr. Artificial King:** **Cloud SQL** is fully managed, regional, and ideal for transactional workloads when global scalability isn’t required.

**✔ Correct Approach:** Use Cloud SQL.

## Selecting Storage for Quarterly Reports
**Mr. X:** We store data long-term and only access it every quarter. Which storage class fits best?  
**Mr. Artificial King:** **Coldline** storage is designed for infrequent access (a few times per year) at a much lower cost than standard storage.

**✔ Correct Approach:** Coldline.

## Auditing Access to Cloud Storage Objects
**Mr. X:** A manager is worried about unauthorized access to objects in Cloud Storage. How can we evaluate all object access?  
**Mr. Artificial King:** You need visibility into **who accessed what data**. This information is recorded in **Data Access audit logs**, which track object-level access.

**✔ Correct Approach:** Enable and then review the Data Access audit logs.

## Organizing Data in Dataplex for Discoverability
**Mr. X:** We have processed and unprocessed data across Cloud Storage and BigQuery, managed through Dataplex. How do we make it easy to discover?  
**Mr. Artificial King:** Dataplex best practice is to separate data by **state**, not by storage type. A **raw zone** holds unprocessed data, while a **curated zone** holds processed, analytics-ready data.

**✔ Correct Approach:** Create a raw zone for unprocessed data and a curated zone for processed data.

## Partitioning BigQuery Tables for Fast Queries
**Mr. X:** We’re ingesting data very fast across many dates. How should we partition the table?  
**Mr. Artificial King:** When data arrives continuously and query patterns are time-based, **ingestion-time daily partitioning** is simple and highly effective for performance.

**✔ Correct Approach:** Create an ingestion-time partitioned table with daily partitioning type.

## Understanding IAM and ACL Access in Cloud Storage
**Mr. X:** We’re using both IAM and ACLs for Cloud Storage access. How is access actually decided?  
**Mr. Artificial King:** Cloud Storage uses an **OR logic** between IAM and ACLs. If either one grants access, the user can access the object.

**✔ Correct Approach:** The user has access if either IAM or ACLs grant a permission.

## Final Takeaway
**Mr. Artificial King:** These scenarios test your ability to:
- Choose the right storage model  
- Optimize for analytics and cost  
- Apply governance and lifecycle controls  
- Improve usability and discoverability of data  

Understanding *why* an option is correct is what prepares you for the exam—not just memorizing answers.

---

**filename:** module-3-diagnostic-questions-explained.md
