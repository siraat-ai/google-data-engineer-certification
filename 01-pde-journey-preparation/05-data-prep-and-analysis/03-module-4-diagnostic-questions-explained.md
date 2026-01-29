# Diagnostic Questions: Preparing and Using Data for Analysis (Explained)

## Designing a Performant BigQuery Schema
**Mr. X:** Our data comes from PostgreSQL, is hierarchical, and tables are often queried together. How should we design the BigQuery schema for analytics?  
**Mr. Artificial King:** BigQuery works best with **denormalized schemas**. Since the data is hierarchical and frequently queried together, using **nested and repeated fields** reduces joins and improves performance.

**✔ Correct Approach:** Use nested and repeated fields.

## Sharing Processed Data with Partners Securely
**Mr. X:** We’ve processed industry data that partners are willing to pay for. How do we share it with proper access control?  
**Mr. Artificial King:** You need a managed, secure data-sharing platform. **Analytics Hub** lets you share datasets with partners while controlling access, without copying data.

**✔ Correct Approach:** Host the data on Analytics Hub.

## Abstracting Multiple Data Sources for Analysts
**Mr. X:** Analysts need to analyze, visualize, and publish reports using data from many sources. How do we simplify this?  
**Mr. Artificial King:** You should use a semantic layer that abstracts data complexity. **Looker** provides centralized modeling, consistent metrics, and governed access for both internal and external reporting.

**✔ Correct Approach:** Looker.

## Restricting Access to Sensitive Columns
**Mr. X:** Some BigQuery columns are extremely sensitive. Only certain users should see them. What’s the right way?  
**Mr. Artificial King:** This is a classic **column-level security** requirement. **Policy tags** let you control access to specific columns based on user permissions.

**✔ Correct Approach:** Use policy tags.

## Troubleshooting Dataplex Discovery Issues
**Mr. X:** We created lakes and zones in Dataplex, but some files aren’t being discovered. Why?  
**Mr. Artificial King:** Dataplex discovery can exclude files based on patterns. If an **exclude pattern matches the files**, they won’t be discovered—even if formats are supported.

**✔ Correct Approach:** You have an exclude pattern that matches the files.

## Improving Poor ML Model Performance
**Mr. X:** Our ML models aren’t performing well in production. The data doesn’t fully represent business goals. What should we do?  
**Mr. Artificial King:** This is a data quality and relevance issue. The most effective fix is **feature engineering**—using domain knowledge to create better, more meaningful features.

**✔ Correct Approach:** Perform feature engineering and enhance the column data using domain knowledge.

## Optimizing Repeated Queries on Changing Data
**Mr. X:** We repeatedly run the same complex joins, and source tables change many times a day. How do we optimize queries?  
**Mr. Artificial King:** **Materialized views** store precomputed results and automatically refresh when data changes, giving faster queries with minimal effort.

**✔ Correct Approach:** Materialized views.

## Computing Values Across Rows Efficiently
**Mr. X:** I need to compute values across a group of rows and return a result for each row. What should I use?  
**Mr. Artificial King:** That’s exactly what **window functions** are for. Using an **OVER clause**, you can compute aggregates without collapsing rows.

**✔ Correct Approach:** Use a window function with an OVER clause.

## Optimizing BigQuery Performance Without Partitioning
**Mr. X:** Our BigQuery tables aren’t partitioned or clustered. How can we still improve performance?  
**Mr. Artificial King:** Reducing write overhead helps. **Batching updates and inserts** improves efficiency and overall query performance.

**✔ Correct Approach:** Batch your updates and inserts.

## Analyzing BigQuery Data Using Familiar Tools
**Mr. X:** Leadership uses Google Workspace and wants a cost-effective way to analyze and visualize BigQuery data using familiar tools. What should we do?  
**Mr. Artificial King:** **Connected Sheets** lets users analyze BigQuery data directly in Google Sheets—no new tools to learn and very cost-effective.

**✔ Correct Approach:** Configure Connected Sheets.

## Final Takeaway
**Mr. Artificial King:** These scenarios test your ability to:
- Design analytics-friendly schemas  
- Secure and share data responsibly  
- Enable analysts with the right tools  
- Optimize BigQuery performance  
- Prepare data effectively for machine learning  

Understanding *why* each choice works is what prepares you for real-world data engineering—and the exam.

---

**filename:** module-4-diagnostic-questions-explained.md
