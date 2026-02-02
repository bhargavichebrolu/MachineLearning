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
# EDA — SUBTOPIC 3: STATISTICAL SUMMARIES

This section explains **why statistical summaries exist**, what each measure means,
what they are **used for**, and what they are **not used for** during Exploratory Data Analysis (EDA).

It also explicitly addresses a common wrong assumption:
> Statistical summaries are NOT meant to detect outliers or row-level errors.

---

## WHAT ARE STATISTICAL SUMMARIES?

### Definition
* **Statistical summaries** are numerical measures that describe the **overall behavior of a numerical variable**.

They operate at the **population level**, not at the individual row level.

---

## WHAT STATISTICAL SUMMARIES DO NOT DO

Statistical summaries:
* Do NOT inspect individual rows
* Do NOT say “this row is wrong”
* Do NOT automatically detect outliers
* Do NOT clean data

---

## WHAT STATISTICAL SUMMARIES ACTUALLY DO

They exist to:
* Compress large datasets into a few interpretable numbers
* Describe what is typical
* Describe how spread out the data is
* Signal where deeper exploration is needed

> Statistical summaries are **navigation tools**, not microscopes.

---

## WHY STATISTICAL SUMMARIES EXIST

In real-world datasets:
* You may have thousands or millions of rows
* Manual inspection is impossible

Statistics exist to:
> **Summarize overall data behavior so humans can decide what to investigate next.**

---

## COMMON WRONG ASSUMPTION (CORRECTED)

### ❌ Wrong assumption
> Statistical measures are used to detect outliers or errors in specific rows.

### ✅ Correct understanding
> Statistical measures describe overall patterns and may only **signal** that unusual values exist.

Actual outlier detection requires:
* Distributions
* Plots
* Percentiles
* Row-level inspection

---

## CORE STATISTICAL SUMMARIES USED IN EDA

EDA primarily relies on **five key statistical measures**:

1. Mean  
2. Median  
3. Minimum  
4. Maximum  
5. Variance / Standard Deviation  

These apply **only to numerical variables**.

---

## MEAN (AVERAGE)

### What the mean is
* Mean = sum of all values ÷ number of values
* Represents a balanced average

---

### Example
Data:
20, 21, 22

makefile
Copy code

Mean:
(20 + 21 + 22) / 3 = 21

yaml
Copy code

Here, the mean correctly represents a typical value.

---

### Where mean fails

Data:
20, 21, 22, 90

makefile
Copy code

Mean:
(20 + 21 + 22 + 90) / 4 = 38.25

yaml
Copy code

Question:
> Is 38 a typical value here?

Answer:
> No.

---

### Key property of mean
* Mean is **sensitive to extreme values (outliers)**.
* A single extreme value can distort it.

---

### When mean is useful
* Data is symmetric
* No extreme values
* Controlled or physical systems

Examples:
* Average temperature
* Average machine output
* Average exam score (well-controlled)

---

## MEDIAN

### What the median is
* The **middle value** when data is sorted
* Represents what a **typical individual experiences**

---

### Example without outlier
Data:
20, 21, 22

makefile
Copy code

Median:
21

yaml
Copy code

---

### Example with outlier
Data:
20, 21, 22, 90

makefile
Copy code

Sorted:
20, 21, 22, 90

makefile
Copy code

Median:
(21 + 22) / 2 = 21.5

yaml
Copy code

---

## ROBUSTNESS (IMPORTANT CONCEPT)

### What does “robust” mean?
* A statistic is **robust** if extreme values do not significantly affect it.

---

### Why median is robust
* Median stays near where most values lie
* Mean shifts heavily due to extremes

---

### Important clarification
> Median does NOT detect outliers.  
> Median **resists being distorted by them**.

---

## WHY MEDIAN IS USED FOR INCOME AND SALARY

Income data is usually skewed.

Example:
30k, 32k, 35k, 40k, 10,00,000

yaml
Copy code

---

### Mean income
≈ 2,27,400

yaml
Copy code

Question:
> Does this represent what most people earn?

Answer:
> No.

---

### Median income
35k

yaml
Copy code

Question:
> Does this represent the majority experience?

Answer:
> Yes.

---

### Conclusion
* Income and salary distributions contain extreme values
* Mean becomes misleading
* Median represents typical individuals

That is why **median income** is reported, not mean income.

---

## MINIMUM AND MAXIMUM

### What they represent
* Minimum = smallest observed value
* Maximum = largest observed value

They answer:
* What are the boundaries of the data?
* Are values logically possible?

---

### Example
Age:
min = -2
max = 150

yaml
Copy code

This signals:
* Possible data errors
* Extreme or invalid values

---

### Important note
* Min and max **signal potential issues**
* They do NOT diagnose them

---

## VARIANCE AND STANDARD DEVIATION

### What they measure
* **Spread** of data
* How far values typically deviate from the center

---

### Simple intuition
* Low variance → values are similar
* High variance → values vary widely

---

### Example

Dataset A:
50, 50, 50, 50

css
Copy code

Dataset B:
10, 30, 70, 90

yaml
Copy code

Both have mean = 50  
Dataset B has much higher variance.

---

### Why variance matters in EDA
Variance helps understand:
* Diversity of behavior
* Stability vs volatility
* Whether one number represents the dataset well

---

## WHY STATISTICAL SUMMARIES ARE NOT ENOUGH ALONE

Statistical summaries:
* Hide distribution shape
* Hide subgroups
* Hide clusters
* Hide multimodal patterns

Therefore:
> **Summaries must always be followed by distribution analysis.**

---

## CORRECT ROLE OF STATISTICAL SUMMARIES IN EDA

### Used for
* Understanding what is typical
* Understanding spread
* Comparing mean vs median to infer skewness
* Deciding next EDA steps

---

### Not used for
* Removing rows
* Declaring errors
* Detecting exact outliers

---

## INTERVIEW-READY ANSWER

**Question:**  
What are statistical summaries and why are they used in EDA?

**Answer:**  
Statistical summaries such as mean, median, minimum, maximum, and standard deviation describe the central tendency and spread of numerical variables. They help summarize overall data behavior and signal potential skewness or variability, guiding deeper exploratory analysis rather than detecting individual outliers.

---

## FINAL LOCK-IN SUMMARY

* Statistical summaries describe populations, not individual rows
* Mean is sensitive to outliers
* Median is robust and represents typical values
* Min and max provide boundary checks
* Variance measures spread
* Statistics guide exploration, they do not make decisions
# EDA — SUBTOPIC 4: DISTRIBUTIONS

This section explains **what distributions are**, **why they are essential in EDA**, and **how they resolve the limitations of statistical summaries**.

Distributions are the point where:
- outliers become visible
- skewness becomes obvious
- mean vs median differences finally make sense

---

## WHAT IS A DISTRIBUTION?

### Plain definition
A **distribution** describes:
> **How the values of a variable are spread across their range.**

It does NOT focus on:
- one specific row
- one specific value

It focuses on:
- where most values lie
- how frequently values occur
- how values thin out toward extremes

---

## WHY DISTRIBUTIONS EXIST

Statistical summaries:
- compress data
- hide structure

Distributions:
- reveal structure
- provide context

> **Distributions exist to show the shape and behavior of data that statistics alone cannot explain.**

---

## WHY STATISTICS ALONE ARE NOT ENOUGH

Two datasets can have:
- same mean
- same median
- same variance

Yet behave completely differently.

### Example

Dataset A:
50, 50, 50, 50


Dataset B:


10, 30, 70, 90


Mean = 50  
Median = 50  

But:
- Dataset A → no variability
- Dataset B → extreme variability

Only distributions reveal this difference.

---

## KEY CLARIFICATION (IMPORTANT DOUBT)

### ❌ Wrong assumption
> Statistical summaries should detect outliers or row-level errors.

### ✅ Correct understanding
> Statistical summaries summarize overall behavior.  
> **Distributions reveal outliers visually.**

Outliers are a **distribution-level concept**, not a statistic-level one.

---

# SUBTOPIC 4.1 — HOW WE VIEW DISTRIBUTIONS

Distributions are understood using **visual tools** that group values and count how often they occur.

---

## CORE IDEA

A distribution becomes visible only when:
- values are grouped into ranges
- frequencies are counted

Every distribution plot answers:
> **How many values fall into each range?**

---

## HISTOGRAM

### What a histogram is
A **histogram**:
- divides the value range into intervals (bins)
- counts how many values fall into each bin
- displays those counts as bars

---

### Example (ages)

Data:


18, 19, 20, 20, 21, 22, 22, 23, 40


Possible bins:
- 18–20
- 21–23
- 24–30
- 31–40

Histogram reveals:
- heavy concentration around 18–23
- very few values near 40

That isolated bar visually indicates **outliers or extreme values**.

---

## WHAT HISTOGRAMS SHOW

Histograms reveal:
- where most values lie
- spread of data
- skewness
- long tails
- presence of outliers

These are **not visible** from mean or median alone.

---

## BIN SIZE (IMPORTANT DETAIL)

A **bin** is a value range.

- Bins too wide → hide structure
- Bins too narrow → noisy, misleading

Histogram interpretation requires **judgement**, not automation.

---

## BOX PLOT

### What a box plot shows
A **box plot** visually summarizes:
- median
- spread
- potential outliers

---

### Components
- Box → middle 50% of data
- Line inside → median
- Whiskers → typical range
- Points outside → potential outliers

---

## WHY BOX PLOTS ARE POWERFUL

Box plots:
- explicitly highlight extreme values
- show skewness visually
- allow easy comparison across groups

They are one of the fastest ways to **spot unusual behavior**.

---

## HISTOGRAM vs BOX PLOT

| Tool | Best for |
|-----|---------|
| Histogram | Overall shape |
| Box plot | Outliers & spread |

They complement each other and should be used together.

---

## DENSITY PLOTS (CONCEPTUAL)

Density plots:
- are smooth versions of histograms
- show probability density instead of counts

Used when:
- datasets are large
- smooth shape comparison is needed

---

## PERCENTILES

Percentiles answer:
> “What value lies below X% of the data?”

Examples:
- 50th percentile → median
- 25th percentile → lower quarter
- 75th percentile → upper quarter
- 95th percentile → extreme high values

Percentiles:
- help quantify tails
- help define thresholds
- complement box plots

---

## FINAL CLARITY ON OUTLIERS

- Statistics → summarize
- Distributions → reveal
- Histograms → show concentration
- Box plots → flag extremes
- Percentiles → quantify extremes

> **Outliers are seen, not computed.**

---

# SUBTOPIC 4.2 — SKEWNESS & SHAPE OF DISTRIBUTIONS

Skewness explains **why real-world data behaves asymmetrically** and why statistics often disagree.

---

## WHAT IS SHAPE?

The **shape of a distribution** describes:
- how values are arranged
- where data clusters
- where tails extend

Shape explains:
- skewness
- symmetry
- multiple peaks

---

## WHAT IS SKEWNESS?

**Skewness** describes whether:
- one side of the distribution stretches longer than the other

That stretched side is called the **tail**.

---

## RIGHT-SKEWED DISTRIBUTION (MOST COMMON)

### Characteristics
- Most values are small or moderate
- Few values are extremely large
- Tail stretches to the right

---

### Examples
- Income
- Salary
- House prices
- Transaction amounts
- Session durations

---

### Effect on statistics
- Mean > Median
- Mean pulled toward large values
- Median stays near majority

This explains earlier confusion about mean vs median.

---

## LEFT-SKEWED DISTRIBUTION

### Characteristics
- Most values are large
- Few values are very small
- Tail stretches to the left

---

### Examples
- Scores on easy exams
- Ratings where most are high

---

### Effect on statistics
- Mean < Median

---

## SYMMETRIC DISTRIBUTION

### Characteristics
- Left and right sides mirror each other
- Balanced spread around center

---

### Examples
- Adult height
- Measurement noise

---

### Effect on statistics
- Mean ≈ Median
- Many model assumptions hold

This shape is **rare in business data**.

---

## SKEWNESS AND OUTLIERS (IMPORTANT CLARIFICATION)

Outliers in skewed data:
- are often expected
- may be valid extreme values

Example:
- A billionaire salary is extreme but valid

EDA helps distinguish:
- data errors
- rare but real observations

---

## MULTIMODAL DISTRIBUTIONS

Sometimes distributions have **multiple peaks**.

This usually indicates:
- multiple sub-populations

Examples:
- Intern salaries + full-time salaries
- Children heights + adult heights

Statistics hide this.  
Distributions reveal it immediately.

---

## WHY SKEWNESS MATTERS IN ML

Skewness affects:
- choice of statistics
- transformations (e.g., log)
- model assumptions
- distance-based algorithms

Ignoring skewness leads to **silent model failure**.

---

## FULL CIRCLE (CONNECTING ALL DOUBTS)

- Statistics summarize behavior
- Distributions reveal structure
- Skewness explains asymmetry
- Outliers appear naturally
- Humans make decisions using all layers

EDA is **layered reasoning**, not a single calculation.

---

## INTERVIEW-READY SUMMARY

> Distributions show how data values are spread across their range, revealing shape, skewness, and outliers. Tools such as histograms, box plots, and percentiles provide essential context that statistical summaries alone cannot capture, enabling correct interpretation and modeling decisions.

---

## LOCK-IN STATEMENT

> **Statistical summaries describe data, but distributions explain it.**
