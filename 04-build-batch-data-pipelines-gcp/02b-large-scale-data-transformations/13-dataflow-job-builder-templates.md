# Using Job Builder UI and Dataflow Templates

## Overview

**Mr. X:** I want to do joins and aggregations in Dataflow, but I don’t want to write code. Is that possible?

**Mr. Artificial King:** Yes, absolutely. You can use the **Job Builder UI** in **Google Cloud Dataflow** along with ready-made **Dataflow templates**. This lets you build powerful data pipelines using simple configuration forms instead of writing Apache Beam code.

![Image](https://docs.cloud.google.com/static/dataflow/images/job-builder.png?hl=ko)

![Image](https://www.slideteam.net/media/catalog/product/cache/1280x720/d/a/data_flow_architecture_presentation_design_Slide01.jpg)

![Image](https://miro.medium.com/1%2AVI4sWcx3dyXnqbUanCFOrg.png)

![Image](https://miro.medium.com/1%2AvxIjQOJVkbnFuZI9EjPkuA.png)

## What Is the Job Builder UI?

**Mr. X:** What exactly is the Job Builder UI?

**Mr. Artificial King:** The Job Builder UI is a **form-based interface** in the Google Cloud Console. It helps you:

* Select a **pre-built or custom Dataflow template**
* Fill in required parameters (like input files and output tables)
* Launch a Dataflow job without coding

Behind the scenes, the template already contains the required **Apache Beam logic**, so you don’t have to worry about implementation details.

## Using Templates for Joins

**Mr. X:** How do I join two datasets using this UI?

**Mr. Artificial King:** You simply choose a join-related template, such as **Join_two_files_and_write_to_BigQuery**, and configure its parameters in a YAML file or directly through the UI.

### Common Join Parameters

* **inputFile1** – Cloud Storage path of the first dataset
* **inputFile2** – Cloud Storage path of the second dataset
* **joinKey1** – Column name used as the join key in the first file
* **joinKey2** – Column name used as the join key in the second file
* **outputTable** – Destination table in **BigQuery**

**Mr. Artificial King:** Internally, the template uses Beam transforms like **CoGroupByKey** to perform the join, but you never have to write or manage that code.

## Using Templates for Aggregations

**Mr. X:** What about aggregations like sums or counts?

**Mr. Artificial King:** For that, you select an aggregation-specific template. You then define parameters such as:

* Input data location
* Grouping fields
* Aggregation logic (sum, count, average, etc.)
* Output destination

These templates internally use Beam operations like **GroupByKey** and **Combine**.

## Why This Approach Is Useful

**Mr. X:** Why should I use templates instead of coding?

**Mr. Artificial King:** This approach is helpful because:

* You can build **complex pipelines without writing code**
* The templates hide Beam complexity from you
* You focus on **pipeline logic**, not implementation
* It’s faster and less error-prone for common use cases

All of this is powered by **Apache Beam**, but you interact with it only through configuration.

## Where to Learn More

**Mr. Artificial King:** To go deeper:

* Check the official **Job Builder UI documentation** to understand the UI flow
* Explore the **Dataflow Templates documentation** to see available templates and their parameters

These resources help you understand which template to choose and how to configure it properly.

---

**Suggested filename:**
`dataflow-job-builder-templates.md`
