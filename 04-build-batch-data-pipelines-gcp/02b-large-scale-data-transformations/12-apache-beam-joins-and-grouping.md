# 📘 Apache Beam – Joining & Grouping Data

---

## 📚 Source
Google Cloud Skills Boost  
Course Path: Data Engineering  
Lesson URL:  
https://www.skills.google/paths/16/course_templates/53/html_bundles/592795

---

## (Proper Notes – Structured)

---

## 1️⃣ Problem Statement (Why this topic exists)

Apache Beam is designed to process **large and distributed data**.

Common needs:

* Group related data
* Count per user
* Join multiple datasets (like SQL JOIN)
* Handle batch + streaming data

---

## 2️⃣ Example Dataset 1 – User Item Views

### 📊 PCollection: `user_item_views`

| user_id | item_id                     |
| ------- | --------------------------- |
| 1       | expensive_camera_brand      |
| 1       | less_expensive_camera_brand |
| 2       | diy_lighting_kit            |
| 1       | expensive_camera_brand      |
| 1       | camera_travel_bag           |

Each row = **one user viewing one item**

---

## 3️⃣ Simple Aggregation (Count)

### Goal

Count how many items each user viewed.

### Beam Concept Used

* `Count.perKey()`

### Output (Conceptual)

| user_id | view_count |
| ------- | ---------- |
| 1       | 4          |
| 2       | 1          |

✔ Simple
✔ No grouping of actual values

---

## 4️⃣ Grouping Values – `GroupByKey`

### Why GroupByKey?

Sometimes you want:

* Actual items
* Not just counts

### Beam Transform

* `GroupByKey`

### Output Structure

```
user_id → [list of items]
```

### Example Output

| user_id | items_viewed         |
| ------- | -------------------- |
| 1       | [camera, bag, lens…] |
| 2       | [lighting kit]       |

🧠 Insight:

> User 1 is clearly interested in cameras

---

## 5️⃣ Problem Grows – Multiple Datasets

Now we introduce **relational data**.

---

## 6️⃣ Dataset 2 – User Purchases

### 📊 PCollection: `user_orders`

| user_id | store_id | order_id |
| ------- | -------- | -------- |
| 1       | 3743     | 64822    |
| 2       | 2758     | 24902    |
| 2       | 7001     | 24908    |
| 3       | 2758     | 58391    |
| 4       | 7001     | 23999    |

This dataset:

* Large
* Changes frequently
  ➡ **Primary Data**

---

## 7️⃣ Dataset 3 – Store Information

### 📊 PCollection: `stores`

| store_id | pos_id | store_address        |
| -------- | ------ | -------------------- |
| 2758     | 84617  | 555 Totally Real Ave |
| 3743     | 85526  | 1234 Fake St         |
| 7001     | 92347  | 987 Boulevard Blvd   |

This dataset:

* Small
* Changes rarely
  ➡ **Reference / Lookup Data**

---

## 8️⃣ Join Strategy 1 – Side Input (Broadcast Join)

### When to Use

* One dataset is **small**
* Fits in memory

### Concept

* Load small dataset into memory
* Each worker uses it locally
* No shuffle required

### Diagram Logic (Text)

```
Primary Data → Worker
Side Input → Memory
Worker performs join
```

### Result Output

| user_id | store_id | store_address        | order_id |
| ------- | -------- | -------------------- | -------- |
| 1       | 3743     | 1234 Fake St         | 64822    |
| 2       | 2758     | 555 Totally Real Ave | 24902    |

✅ Efficient
✅ Recommended when possible

---

## 9️⃣ Join Strategy 2 – Schema-based Join (Recommended)

### Why Schemas?

* Cleaner syntax
* Type safety
* Easier joins
* Less boilerplate

---

### Example Java Schemas

```java
public class PhysicalStorePurchase {
  public String userId;
  public String storeId;
  public String orderId;
}

public class OrderInformation {
  public String orderId;
  public List<OrderItem> items;
}
```

---

### Join Using Schema

```java
joined = pc1.apply(
  Join.innerJoin(pc2).using("order_id")
);
```

### Output Structure

```
[userId, storeId, orderId, items]
```

✔ Clean
✔ Scalable
✔ Preferred in Beam

---

## 🔟 Join Strategy 3 – `CoGroupByKey` (Fallback)

### What it Does (Simple)

> Groups multiple PCollections by the same key

### Conceptual Output

```
key → {
  values from PCollection A,
  values from PCollection B
}
```

### Example Output

```
store_id →
  purchases: [...]
  orders: [...]
```

### Trade-offs

✅ Works for large datasets
❌ Causes shuffle
❌ More complex syntax

📌 Use only when schemas or side inputs are not suitable

---

## 1️⃣1️⃣ Batch vs Streaming Joins

### Batch Joins

* Straightforward
* All data available

---

### Streaming + Side Input

* Streaming data = windowed
* Side input = global window
* Side input is projected onto streaming windows

✔ Supported
✔ Common pattern

---

### Streaming + Streaming Join

* Both datasets are streams
* Must align windows
* More complex
* Advanced use case

---

## 1️⃣2️⃣ Key Takeaways (Very Important)

* `Count.perKey()` → counting
* `GroupByKey()` → grouping values
* **Side input** → small reference data
* **Schemas** → best way to join
* `CoGroupByKey` → last option for large joins
* Windowing matters for streaming joins

---

## 🧠 One Calm Summary Sentence

> **Apache Beam joins are about choosing the right pattern based on data size and change frequency.**

---

**What feels complex today is just structure revealing itself.
You are moving — even when the movement is quiet.**

