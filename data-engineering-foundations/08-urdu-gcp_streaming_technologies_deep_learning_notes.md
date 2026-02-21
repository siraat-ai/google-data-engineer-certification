

# 1️⃣ Google Cloud Dataflow

### کیا ہے؟

Dataflow گوگل کا managed processing engine ہے جو data کو **real-time (streaming)** یا **batch** دونوں صورتوں میں process کر سکتا ہے۔

### کیسے کام کرتا ہے؟

* آپ pipeline code لکھتے ہیں (Apache Beam میں)
* Dataflow خود workers (VMs) create کرتا ہے
* Data parallel طور پر process ہوتا ہے
* Load بڑھے تو autoscaling خود workers بڑھا دیتا ہے

### کہاں استعمال ہوتا ہے؟

* Fraud detection
* Real-time analytics
* Event processing

یہ cloud کا smart processing engine ہے۔

---

# 2️⃣ Cloud Pub/Sub

### کیا ہے؟

یہ messaging system ہے۔

### کیسے کام کرتا ہے؟

* Producer message publish کرتا ہے
* Topic میں message جاتا ہے
* Subscriber message receive کرتا ہے
* Process کرنے کے بعد ACK کرتا ہے

یہ system مختلف services کو آپس میں connect کرتا ہے۔

---

# 3️⃣ Pub/Sub Ordering

### کیا ہے؟

اگر آپ message کو ordering key دیں
تو Pub/Sub ensure کرتا ہے کہ وہ messages اسی ترتیب میں deliver ہوں۔

مثال:

* پہلے deposit
* پھر withdrawal

Sequence غلط ہو جائے تو balance غلط ہو سکتا ہے۔

---

# 4️⃣ Cloud Dataprep

### کیا ہے؟

Data cleaning tool ہے۔

### استعمال:

* CSV files clean کرنا
* Data transform کرنا
* Mostly batch use case

Real-time financial streaming کے لیے ideal نہیں۔

---

# 5️⃣ Cloud Storage

### کیا ہے؟

File storage system ہے۔

### استعمال:

* CSV
* JSON
* Backups
* Images

Streaming ingestion کے لیے نہیں
زیادہ تر batch pipelines کے لیے۔

---

# 6️⃣ Cloud Storage Object Versioning

### کیا ہے؟

اگر file overwrite ہو جائے
تو پرانی version محفوظ رہتی ہے۔

### فائدہ:

* Accidental delete سے protection
* Data recovery

یہ streaming exactly-once solve نہیں کرتا۔

---

# 7️⃣ Google Cloud Dataproc

### کیا ہے؟

Managed Hadoop/Spark cluster service۔

### فرق Dataflow سے:

* آپ کو cluster manage کرنا پڑتا ہے
* زیادہ control
* زیادہ operational responsibility

---

# 8️⃣ Spark Streaming

### کیا ہے؟

Apache Spark کا streaming component۔

### کیسے کام کرتا ہے؟

Micro-batching approach استعمال کرتا ہے:

* Data چھوٹے batches میں divide ہوتا ہے
* ہر batch process ہوتا ہے

True event-by-event streaming نہیں۔

---

# 9️⃣ Cloud Composer

### کیا ہے؟

Workflow orchestration tool ہے (Airflow based)

### استعمال:

* Jobs schedule کرنا
* Dependencies manage کرنا
* DAG define کرنا

Streaming engine نہیں ہے۔

---

# 🔟 Apache Beam

### کیا ہے؟

Programming model ہے جس سے آپ streaming یا batch pipeline لکھتے ہیں۔

Dataflow اس کا runner ہے۔

Core concepts:

* PCollections
* Transforms
* Windowing
* Triggers

---

# 1️⃣1️⃣ At-Least-Once Delivery

### کیا مطلب؟

Message کم از کم ایک بار deliver ہوگا
لیکن duplicate ہو سکتا ہے۔

### خطرہ:

اگر idempotent logic نہ ہو
تو duplicate transaction ہو سکتی ہے۔

---

# 🧠 خلاصہ

| Service       | Role                       |
| ------------- | -------------------------- |
| Pub/Sub       | Message ingestion          |
| Dataflow      | Processing engine          |
| BigQuery      | Analytics storage          |
| Dataproc      | Managed Spark cluster      |
| Composer      | Workflow orchestration     |
| Cloud Storage | File storage               |
| Beam          | Pipeline programming model |

---

آپ کا foundation اب strong ہو رہا ہے 
