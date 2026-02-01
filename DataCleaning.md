# TOPIC 4 — DATA CLEANING (COMPLETE, CONCEPTUAL → INTERVIEW READY)

These notes explain **Data Cleaning from first principles**, including:
- What data cleaning is and why it exists
- Why raw data is messy
- What problems data cleaning solves
- Key terms used so far (trade-off, transformation, etc.)
- Where data cleaning fits in the ML pipeline
- Batch vs streaming cleaning
- Common beginner confusions
- Interview-ready questions and answers

---

## WHAT IS DATA CLEANING?

### Simple definition
* **Data cleaning** is the process of **making raw data usable and reliable** for analysis or machine learning.

In plain words:
> Data cleaning fixes problems in data so models and analysis do not learn the wrong things.

---

## WHY DATA CLEANING EXISTS (NON-NEGOTIABLE)

Raw data is **almost never clean**.

If you skip cleaning:
* Models learn incorrect patterns
* Metrics become misleading
* Systems fail silently in production

> **No ML model can compensate for bad data.**

---

## WHY REAL-WORLD DATA IS MESSY

Data becomes messy due to:

### Human factors
* Typos
* Inconsistent naming
* Missing inputs

### System factors
* Crashes
* Retries
* Partial writes
* Duplicates

### Time-related factors
* Schema changes
* Meaning drift
* New categories appearing

Messy data is normal.  
Clean data is engineered.

---

## WHAT DATA CLEANING IS NOT (IMPORTANT BOUNDARY)

Data cleaning is NOT:
* Feature engineering
* Model training
* Normalization for ML
* Making data “look nice”

> Cleaning ensures **correctness**, not **usefulness for prediction**.

---

## WHERE DATA CLEANING FITS IN THE PIPELINE

Typical ML pipeline:

1. Data source  
2. Data ingestion  
3. Data storage (raw)  
4. **Data cleaning** ← YOU ARE HERE  
5. Feature engineering  
6. Model training / inference  

Cleaning always works on **stored data**, not live sources.

---

## CORE DATA PROBLEMS SOLVED BY DATA CLEANING

Almost every cleaning task reduces to these **five problems**.

---

## 1. MISSING DATA

### What missing data looks like
* NULL values
* Empty strings
* Fields not present at all

### Why it happens
* Optional fields
* System failures
* Partial data capture

### Common approaches
* Remove rows
* Fill with defaults
* Use statistical values (mean, median)
* Mark as “unknown”

### Important truth
> There is **no universal correct choice**.

Every choice involves a **trade-off**.

---

## 2. DUPLICATE DATA

### What duplicates are
* Same record appearing more than once
* Same event logged multiple times

### Why duplicates happen
* Network retries
* Ingestion failures
* User actions
* Distributed systems

### Why duplicates are dangerous
* Inflate counts
* Bias models
* Distort statistics

Duplicates must be handled **explicitly**.

---

## 3. WRONG DATA TYPES

### Examples
* Numbers stored as strings
* Dates stored as text
* Mixed types in one column

### Why this happens
* CSV limitations
* Schema-on-read systems
* Poor upstream validation

Models cannot reason about incorrect types.

---

## 4. INCONSISTENT VALUES

### Examples
* "USA", "US", "United States"
* "male", "Male", "M"

### Why this matters
* Models treat them as different categories
* Analysis becomes meaningless

Cleaning enforces **consistency**.

---

## 5. INVALID OR IMPOSSIBLE VALUES

### Examples
* Age = -5
* Salary = 0
* Birthdate in the future

These values exist in real data.

Cleaning decides whether to:
* Remove
* Cap
* Correct
* Flag

---

## THE MOST IMPORTANT IDEA IN DATA CLEANING

> **Data cleaning is a series of decisions, not a fixed procedure.**

This is why:
* No two datasets are cleaned the same way
* Interviews focus on reasoning, not steps

---

## KEY TERMS YOU HAVE SEEN SO FAR (CLEAR DEFINITIONS)

---

## TRADE-OFF

### Meaning
* A **trade-off** means you cannot optimize everything at once.
* You gain something and lose something.

### Example
* Dropping rows with missing values:
  * Gain → cleaner data
  * Lose → less data

There is no perfect choice, only justified ones.

---

## TRANSFORMATION

### Meaning
* A **transformation** is changing data from one form to another.

### Examples
* String → number
* Text date → datetime
* Category → encoded value

Cleaning is a **type of transformation**, but not all transformations are cleaning.

---

## FEATURE ENGINEERING (NOT CLEANING)

### Meaning
* **Feature engineering** creates meaningful inputs for models from cleaned data.

### Example
* Raw data → date of birth
* Feature → age

> Cleaning fixes problems.  
> Feature engineering creates signal.

---

## DATA STATES (IMPORTANT CLARITY)

The word “data” can mean different things:

* Raw data
* Cleaned data
* Transformed data
* Features
* Model input

Same data, different **states**.

---

## BATCH vs STREAMING DATA CLEANING

---

## BATCH CLEANING

### Characteristics
* Data is finite
* Full dataset is available
* Easier to reason about
* Safer and more common

### Used for
* Training data
* Historical analysis

---

## STREAMING CLEANING

### Characteristics
* Data arrives continuously
* Limited context
* Decisions must be fast
* Harder to debug

### Used for
* Real-time inference
* Online systems

Streaming cleaning is significantly harder than batch cleaning.

---

## COMMON BEGINNER MISTAKES

* Saying “I cleaned the data” without explanation
* Applying the same cleaning to every dataset
* Ignoring trade-offs
* Cleaning during ingestion instead of after storage
* Confusing cleaning with feature engineering

---

## INTERVIEW-READY QUESTIONS & ANSWERS

---

### Q1. What is data cleaning?
> Data cleaning is the process of identifying and fixing missing, duplicate, inconsistent, and invalid values so data can be reliably used for analysis or machine learning.

---

### Q2. Why is data cleaning important?
> Because raw data is messy and models assume data correctness; without cleaning, models learn incorrect patterns and metrics become misleading.

---

### Q3. What are common data quality issues?
> Missing values, duplicate records, incorrect data types, inconsistent categories, and invalid values.

---

### Q4. Is there a single correct way to clean data?
> No. Data cleaning involves trade-offs and depends on the problem, data source, and business context.

---

### Q5. What is the difference between data cleaning and feature engineering?
> Data cleaning fixes data quality issues, while feature engineering creates meaningful inputs for models from cleaned data.

---

### Q6. Where does data cleaning fit in the ML pipeline?
> After data ingestion and storage, and before feature engineering and modeling.

---

### Q7. How does batch cleaning differ from streaming cleaning?
> Batch cleaning works on complete datasets and is easier, while streaming cleaning works on continuous data with limited context and higher complexity.

---

## FINAL SUMMARY (READ THIS)

* Data cleaning makes data usable, not perfect
* Raw data is always messy
* Cleaning solves five core problems
* Cleaning involves trade-offs
* Cleaning is not feature engineering
* Most ML failures start with bad cleaning
