# Knowledge Check: Ingesting and Processing Data

## Automating and Monitoring Workflows
**Mr. X:** Our company wants to improve productivity. We want to *programmatically schedule and monitor workflows*. Which tool should we use?  
**Mr. Artificial King:** When you talk about automation, scheduling, dependencies, and monitoring workflows, you’re really talking about **orchestration**.

**Mr. X:** So which tool handles orchestration best?  
**Mr. Artificial King:** **Cloud Composer** is the right choice. It’s a fully managed workflow orchestration service built on Apache Airflow. It lets you:
- Define workflows as code  
- Schedule tasks  
- Monitor execution  
- Manage dependencies between tasks  

That makes it ideal for automating complex workflows.

**✔ Correct Answer:** Cloud Composer

## Loading Clean Data into BigQuery
**Mr. X:** Another scenario: the company already has clean data, and it’s in the right format for analysis. We use BigQuery as our data warehouse. How should we move the data?  
**Mr. Artificial King:** Since the data is:
- Already clean  
- Already structured correctly  
- Ready for analysis  

There’s no need to waste time or money transforming it again.

**Mr. X:** So we skip transformations?  
**Mr. Artificial King:** Exactly. The simplest and most efficient approach is **Extract and Load (EL)**. You just move the data directly into BigQuery and start analyzing it.

**✔ Correct Answer:** Directly load the data using Extract and Load approach (EL)

## Key Takeaways
**Mr. Artificial King:** Remember these simple rules:
- Use **Cloud Composer** when you need workflow automation and monitoring  
- Use **EL** when data is already clean and analysis-ready  

Understanding *when not to overcomplicate things* is an important skill for a Professional Data Engineer.

---

**filename:** knowledge-check-workflows-and-el.md
