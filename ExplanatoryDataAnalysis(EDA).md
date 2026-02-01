# TOPIC 5 — EXPLORATORY DATA ANALYSIS (EDA)

Exploratory Data Analysis (EDA) is the stage in the Machine Learning pipeline where we **understand cleaned data before building features or models**.

EDA is not about prediction or optimization.  
EDA is about **knowing your data deeply enough to avoid wrong decisions later**.

---

## WHY EDA EXISTS

EDA answers the question:

> **What does this data actually look like?**

Without EDA:
* Wrong model assumptions are made
* Distributions are misunderstood
* Outliers are mishandled
* Correlations are misinterpreted

Cleaning fixes errors.  
EDA reveals behavior.

---

## EDA COMES AFTER DATA CLEANING

Correct pipeline order:

1. Data Source  
2. Data Ingestion  
3. Data Storage  
4. Data Cleaning  
5. **Exploratory Data Analysis (EDA)**  
6. Feature Engineering  
7. Model Training / Inference  

EDA must always be performed on **cleaned data**, not raw data.

---

## COMPLETE EDA SUBTOPIC BREAKDOWN

EDA can be fully understood using the following **7 subtopics**:

1. **What are variables?**  
2. **Types of variables**  
3. Statistical summaries  
4. Distributions  
5. Outliers  
6. Relationships between variables (correlation)  
7. How EDA influences features and models  

This document currently covers **Subtopic 1 and Subtopic 2**.

---

# SUBTOPIC 1 — WHAT ARE VARIABLES?

---

## WHAT IS A VARIABLE? (FOUNDATION)

### Simple definition
* A **variable** is **one piece of information recorded about something**.

In datasets:
> **Each column is a variable.**

Rows represent individual records.  
Columns represent variables.

---

## REAL-WORLD EXAMPLE

Imagine a student.

Information about the student:
* Age
* Gender
* Marks
* Attendance

Each of these is a **variable**.

The student is the entity.  
The attributes are variables.

---

## VARIABLES IN A DATASET

Example dataset:

| age | gender | marks |
|-----|--------|-------|
| 20  | Female | 85    |
| 21  | Male   | 90    |

* `age` → variable  
* `gender` → variable  
* `marks` → variable  

---

## WHY VARIABLES MATTER IN EDA

EDA starts by asking:
* What variables exist?
* What do they represent?
* Do their values make sense?
* Are their values reasonable?

Without understanding variables:
* Statistics do not make sense
* Distributions do not make sense
* Correlations do not make sense

---

## COMMON DOUBT CLARIFIED

### ❓ Doubt
> Is a variable a row or a column?

### ✅ Answer
> **A variable is a column.**

Rows are observations.  
Columns are variables.

---

## INTERVIEW-READY DEFINITION

> A variable is a measurable or observable attribute recorded in a dataset, typically represented as a column.

---

# SUBTOPIC 2 — TYPES OF VARIABLES

---

## WHY VARIABLE TYPES MATTER

Variables are **not all the same kind**.

The type of a variable decides:
* Which statistics are valid
* Which plots are valid
* How models can use the data

Wrong type → wrong EDA → wrong model.

---

## BIG CLASSIFICATION OF VARIABLES

All variables fall into **two main types**:

1. **Numerical variables**
2. **Categorical variables**

Every variable belongs to **one of these**.

---

## NUMERICAL VARIABLES

### Definition
* Numerical variables represent **measurable quantities**
* Arithmetic operations make sense

---

### Examples

| Variable | Reason |
|--------|--------|
| Age | Difference and average are meaningful |
| Salary | Scale and magnitude matter |
| Distance | Measurement-based |
| Marks | Quantitative score |

---

### What you can do with numerical variables
* Mean
* Median
* Variance
* Standard deviation
* Sorting

Example:
* Age 30 > Age 20 (meaningful)
* Difference of 10 years is meaningful

---

## SUBTYPES OF NUMERICAL VARIABLES

### 1. Discrete Numerical Variables
* Countable
* Whole numbers only

Examples:
* Number of children
* Number of purchases
* Number of calls

---

### 2. Continuous Numerical Variables
* Measured on a scale
* Decimal values possible

Examples:
* Height
* Weight
* Temperature
* Time

---

## CATEGORICAL VARIABLES

### Definition
* Categorical variables represent **labels or groups**
* Arithmetic does NOT make sense

---

### Examples

| Variable | Reason |
|--------|--------|
| Gender | Label |
| City | Name |
| Product category | Group |
| Payment method | Type |

---

### What you can do with categorical variables
* Count frequencies
* Calculate percentages
* Find most common category (mode)

You **cannot** compute:
* Mean
* Variance
* Distance

---

## SUBTYPES OF CATEGORICAL VARIABLES

### 1. Nominal Variables
* No natural order
* Pure labels

Examples:
* Gender
* City
* Color

---

### 2. Ordinal Variables
* Categories have an order
* Distance between values is not measurable

Examples:
* Education level (School < College < Degree)
* Satisfaction (Low < Medium < High)
* Ratings (Poor < Average < Good)

---

## IMPORTANT DOUBTS CLARIFIED

---

### ❓ Numeric-looking but categorical?

Example:
```text
customer_id = 1023, 1024, 1025
