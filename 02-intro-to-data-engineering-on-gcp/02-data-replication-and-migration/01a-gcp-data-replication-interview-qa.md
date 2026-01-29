

# ☁️ Google Cloud Data Replication & Migration – Interview Q&A

---

### **1. What is meant by the baseline data replication and migration architecture in Google Cloud?**

The **baseline architecture** explains how data is **moved or replicated** from **on-premises systems** or **other cloud environments** into **Google Cloud**. It provides a **standard foundation** to evaluate **migration requirements** and helps in selecting the **most appropriate migration tools** for different scenarios.

---

### **2. Why is the gcloud command-line tool important for data migration?**

The **gcloud CLI** enables management of **Google Cloud resources** through **command-line automation** instead of the UI. It is especially useful for **automation**, **scripting**, and **large-scale or repeatable migration tasks** where manual operations are inefficient.

---

### **3. When should Storage Transfer Service be used?**

**Storage Transfer Service** is used for **large-scale online data transfers**, such as migrating data from **on-premises environments** or **other cloud providers** to **Cloud Storage**. It supports **scheduled** and **recurring transfers** and reduces the need for **custom migration solutions**.

---

### **4. In which scenarios is Transfer Appliance the best option?**

**Transfer Appliance** is recommended when migrating **very large datasets** or when **network bandwidth is limited**. Data is copied locally to a **physical appliance**, **securely shipped to Google**, and uploaded into **Cloud Storage**. This is ideal for **offline, one-time bulk migrations**.

---

### **5. What is Datastream and when is it used?**

**Datastream** is a **managed service** for **continuous data replication**. It captures **database changes** in **near real time** and is commonly used for **Change Data Capture (CDC)** pipelines. Datastream is best suited for **ongoing data synchronization**, not **one-time transfers**.

---

### **6. How do these tools fit together in a migration strategy?**

* **Storage Transfer Service** → **Online bulk data migration**
* **Transfer Appliance** → **Offline, large-scale data migrations**
* **Datastream** → **Continuous, real-time replication**
* **gcloud CLI** → **Automation and operational control**

Together, these tools provide a **comprehensive end-to-end data replication and migration strategy** on **Google Cloud**.

---

