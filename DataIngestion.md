# TOPIC 2 — DATA INGESTION (COMPLETE FROM ZERO TO INDUSTRY)

These notes explain **data ingestion from first principles**, including:
- Why ingestion exists
- Batch vs streaming ingestion
- Why files are sometimes enough
- Why Kafka exists
- Why code is needed
- How ingestion fits into the ML pipeline
- Interview-ready definitions

Read slowly. These notes are meant to **build understanding**, not just list facts.

---

## WHAT IS DATA INGESTION?

### Simple definition
* **Data ingestion** is the process of **moving data from where it is created to where it can be stored or processed**.

In plain words:
> Data ingestion answers the question:  
> **How does data travel from the source into our system?**

---

## DATA SOURCE vs DATA INGESTION (IMPORTANT)

* **Data Source**
  * The system that **creates** data
  * Examples: backend server, website, mobile app, sensor, API

* **Data Ingestion**
  * The process that **moves** data
  * Does not create data
  * Does not analyze data

> A data source produces data.  
> Data ingestion only transports it.

---

## WHY DATA INGESTION IS NEEDED

Data is useless if:
* It stays at the source
* It arrives too late
* It gets lost
* It cannot be accessed by other systems

Data ingestion exists to ensure:
* Reliable movement
* Availability
* Timeliness
* Consistency

---

## TWO FUNDAMENTAL INGESTION MODES

There are **only two ways** data can be ingested.

> **All ingestion systems are either BATCH or STREAMING.**

---

## BATCH DATA INGESTION

### What batch ingestion means
* Data is collected over time
* The system **waits**
* Data is ingested **together later**

Batch ingestion is about **waiting first, then processing**.

---

### Real-world analogy
* You collect dishes all day
* You wash them at night

This is batch.

---

### Data example
1. Transactions happen all day
2. At midnight, a CSV file is created
3. The CSV is ingested into the system

---

### Characteristics of batch ingestion
* High latency (results come late)
* Easier to debug
* Easier to re-run
* Stable and predictable

---

### Where batch ingestion is used
* ML model training
* Historical analysis
* Reporting
* Backfills

> Most ML training pipelines use batch ingestion.

---

## STREAMING DATA INGESTION

### What streaming ingestion means
* Data is ingested **as soon as it is created**
* No waiting
* Continuous flow

Streaming ingestion is about **processing immediately**.

---

### Real-world analogy
* A live microphone
* Sound is captured instantly

---

### Data example
1. User clicks a button
2. Event is ingested immediately
3. Downstream systems react instantly

---

### Characteristics of streaming ingestion
* Low latency (fast response)
* More complex systems
* Harder debugging
* Ordering and duplication issues

---

### Where streaming ingestion is used
* Fraud detection
* Live recommendations
* Monitoring and alerts
* Real-time dashboards

---

## WHAT IS LATENCY?

### Plain meaning
* **Latency = delay**
* Time between an event happening and the system responding

---

### Examples
* Click button → response after 2 seconds → latency = 2 seconds
* Payment → fraud detected after 1 hour → latency = 1 hour

---

### Latency in ingestion
* Batch ingestion → high latency
* Streaming ingestion → low latency

---

## FILE-BASED INGESTION (WHEN FILES ARE ENOUGH)

### When files work perfectly
* Data is finite
* Data stops accumulating
* Waiting is acceptable

---

### Examples
* Attendance sheets
* Exam results
* Monthly sales reports
* Historical datasets

---

### Typical file-based flow
1. Data is generated
2. Data is exported to CSV / Excel
3. File is downloaded
4. Data is cleaned
5. Model is trained

This is:
* Batch ingestion
* Simple
* Reliable

> Kafka is NOT required here.

---

## WHEN FILES BREAK DOWN

Files fail when:
* Data never stops
* Data arrives continuously
* You cannot wait for a “download moment”

---

### Examples
* Website clicks
* Backend logs
* Payment events
* Sensor readings

In these cases:
> **You cannot download data.  
> You must listen to data.**

This is why Kafka exists.

---

## WHAT IS KAFKA?

### What Kafka is NOT
* Not a database
* Not storage
* Not ML
* Not cleaning

---

### Correct definition
> **Kafka is a system that receives events continuously and makes them available for other systems to read reliably.**

Kafka is an **ingestion infrastructure**.

---

## WHAT IS AN EVENT?

### Definition
* An **event** is a record that **something happened at a specific time**.

---

### Examples
* User clicked login
* Payment failed
* Sensor measured temperature

Kafka only moves events.  
It does not understand them.

---

## WHY KAFKA IS NEEDED IN INGESTION

Kafka solves ingestion problems:
* Continuous data
* High volume
* Multiple consumers
* Failure recovery
* Ordering

Kafka acts as a **central event hub**.

---

## WHY CODE IS REQUIRED WITH KAFKA

With files:
* You download once
* You process once

With Kafka:
* Data never stops
* There is nothing to download

So you write **code that continuously reads data**.

This code is called:
* Ingestion service
* Consumer
* Reader

---

## INGESTION SYSTEM (CLEAR DEFINITION)

### What an ingestion system is
> A program that continuously reads events from Kafka and moves them to storage or processing systems.

---

### What ingestion systems do
* Read events
* Handle retries
* Forward data
* Ensure delivery

---

### What ingestion systems do NOT do
* Data cleaning
* Feature engineering
* Modeling

Ingestion ends when data is delivered safely.

---

## KAFKA AND THE ML PIPELINE

Kafka appears **only at the ingestion stage**.

---

### Batch ML pipeline
1. Data source generates events
2. Events go to Kafka
3. Ingestion system reads events
4. Raw data stored
5. Cleaning happens later
6. Features created
7. Model trained

---

### Streaming ML pipeline
1. Data source generates event
2. Event goes to Kafka
3. Ingestion system reads immediately
4. Event sent to ML model
5. Prediction made in real time

---

## KAFKA DOES NOT REPLACE FILES

* Files → finite, batch data
* Kafka → continuous, streaming data

Both coexist in real systems.

---

## WHEN NOT TO USE KAFKA

Do NOT use Kafka when:
* Data is finite
* Batch processing is enough
* Latency does not matter
* Simplicity is preferred

Kafka everywhere = overengineering.

---

## INTERVIEW-READY DEFINITIONS

### Data Source
> A system that produces data.

### Data Ingestion
> The process of moving data from source systems into storage or processing systems.

### Batch Ingestion
> Ingesting data in chunks after waiting for a period of time.

### Streaming Ingestion
> Ingesting data continuously as it is generated.

### Event
> A record that something happened at a specific time.

### Kafka
> A distributed event streaming platform used to reliably transport events between systems.

### Latency
> The delay between data generation and system response.

---

## FINAL TAKEAWAY

* Files are enough for finite data
* Kafka is needed for continuous data
* Continuous data cannot be downloaded
* Code is required to listen continuously
* Kafka is ingestion, not cleaning or ML
* Your reasoning was correct
