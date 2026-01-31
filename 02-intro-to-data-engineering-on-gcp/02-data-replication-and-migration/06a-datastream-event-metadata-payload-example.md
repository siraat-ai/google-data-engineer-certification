## 📦 Example of a Datastream Event: Metadata vs Payload

**Mr. X:** You said each Datastream event has Metadata and Payload. Can you show a simple example of both?  
**Mr. Artificial King:** Sure. Let’s take an example where a new row is inserted into a `customers` table.

---

### 🧾 Example: Metadata

**Mr. Artificial King:** Metadata gives **context** about the change. It describes *where* the change came from and *what kind* of change it is.

```json
{
  "source_database": "sales_db",
  "schema": "public",
  "table": "customers",
  "change_type": "INSERT",
  "event_timestamp": "2026-01-31T10:15:30Z",
  "transaction_id": "tx_987654"
}
````

📌 This tells us:

* Which database and table changed
* What type of change happened (INSERT)
* When the change occurred

---

### 📊 Example: Payload

**Mr. X:** Okay, so what does the payload look like?
**Mr. Artificial King:** The payload contains the **actual data values** that changed.

```json
{
  "customer_id": 101,
  "name": "John Doe",
  "email": "john.doe@example.com",
  "country": "USA"
}
```

📌 This represents:

* The row data that was inserted or modified
* Column names with their corresponding values

---

## 🔗 How Metadata and Payload Work Together

**Mr. Artificial King:**

* **Metadata** answers: *What changed, where, and when?*
* **Payload** answers: *What is the actual data?*

Together, they allow Datastream to:

* Track data lineage
* Replicate changes accurately
* Enable near real-time analytics in BigQuery or other destinations

---

📄 Filename:
`datastream-event-metadata-payload-example.md`

```
```
