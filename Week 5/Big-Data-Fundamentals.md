<details><summary>Learning Objectives</summary>

- After completing this module, **learners will understand** the basics of Big Data.
- Learners will be able to **differentiate between structured, semi-structured, and unstructured data**.
- Learners will identify and explain the **5Vs of Big Data**.
- Learners will recognize **real-world applications** of Big Data across industries.
- Learners will gain a high-level understanding of **Big Data tools and implementation concepts**.

</details>

<details><summary>Description</summary>

## What is Data?

- Data is raw facts and figures.
- Data can be numbers, text, images, audio, video, or sensor readings.
- By itself, data has no meaning. When processed and analyzed, it becomes **information**.

Example:
- Marks scored by students → Data  
- Average class performance → Information  

---

## What is Big Data?

- Big Data is a group of data that is massive in volume, yet increasing exponentially with time.
- It is data with such a large size and complexity that no traditional data management tools can store or process it efficiently.
- Big Data includes data from:
  - Social media platforms
  - Online transactions
  - Sensors and IoT devices
  - Machine logs
  - Multimedia content

---

## Characteristics of Big Data

- Volume
- Variety
- Velocity
- Variability
- Value

---

### i) Volume

- The term **“Big Data”** emphasizes the **large volume** of data generated and stored.
- **Volume** is the **amount** of data generated and stored.
- Data is now measured in:
  - Terabytes (TB)
  - Petabytes (PB)
  - Exabytes (EB)
  - Zettabytes (ZB)

Example:
- Social media platforms generate millions of posts every minute.
- E-commerce websites store millions of transaction records.

---

### ii) Variety

- It refers to the nature of data—**structured, semi-structured, and unstructured**.
- It also refers to **heterogeneous sources** of data.

## Different varieties of data

- **Structured Data**
  - Organized in tables (rows and columns)
  - Stored in relational databases
  - Example: Excel sheets, SQL tables

- **Semi-Structured Data**
  - Does not follow a rigid table format
  - Contains tags or markers
  - Example: JSON, XML

- **Unstructured Data**
  - No predefined format
  - Example: Images, videos, emails, social media posts

![Variety](Images/variety.PNG)

---

### iii) Velocity

- **Velocity** is the speed at which data is **generated, collected, and processed**.
- Real-time data processing is often required.

Example:
- Stock market transactions
- Online payment systems
- Live traffic updates

---

### iv) Variability

- **Variability** is the **inconsistency** of data over time or across contexts.
- Data meaning may change depending on context.
- Data flow may fluctuate during peak and off-peak hours.

Example:
- Increased online traffic during festival sales.
- Sudden spikes in social media trends.

---

### v) Value

- **Value** is the **useful insight or business benefit** derived from data.
- Collecting data alone is not enough. Extracting meaningful insights is essential.

Example:
- Customer purchase patterns → Targeted marketing
- Health records → Early disease detection

---

## Advantages of Big Data

- Big Data analysis can drive innovation, **improve customer targeting**, and **optimize business processes**.
- It helps in improving science and research.
- It improves healthcare and public health through **electronic patient records** and large-scale analytics.
- It supports **financial trading, sports analytics, polling, and security/law enforcement**, etc.
- **Anyone can access large amounts of information via surveys and answer many queries.**
- **Data is generated every second.**
- **A single platform can store vast amounts of information.**
- Enables better decision-making using predictive analytics.
- Helps organizations reduce operational costs.

</details>

<details><summary>Real World Application</summary>

## Product Development

- Companies like Netflix and Procter & Gamble use Big Data to anticipate client demand.
- They build predictive models for new products and services by analyzing:
  - Customer preferences
  - Historical product performance
  - Market trends
- P&G uses information and analytics from focus groups, social media, test markets, and early store rollouts to plan, produce, and launch new products.

---

## Healthcare

- Hospitals use Big Data for:
  - Disease prediction
  - Patient monitoring
  - Personalized treatment plans

---

## E-commerce

- Online platforms analyze browsing history and purchase patterns to:
  - Recommend products
  - Optimize pricing
  - Improve customer experience

---

##  Smart Cities

- Traffic management systems use real-time data to reduce congestion.
- Energy consumption data helps optimize power distribution.

</details>

<details><summary>Implementation</summary> 

## Big Data Implementation using Hadoop and PySpark

A typical Big Data system using Hadoop and PySpark follows this pipeline:

1. Data Collection  
2. Data Storage (HDFS)  
3. Data Processing (MapReduce / Spark)  
4. Data Analysis  

---

## 1. Data Collection

Data can be collected from:

- Application logs  
- Social media platforms  
- E-commerce transactions  
- IoT devices  
- CSV/JSON files  

Example:
An e-commerce website collects customer purchase data and browsing history.

---

## 2. Data Storage using Hadoop (HDFS)

### What is Hadoop?

Hadoop is a distributed framework designed to store and process massive datasets across multiple machines.

### Hadoop Distributed File System (HDFS)

- Stores large files by splitting them into blocks.
- Distributes those blocks across multiple nodes.
- Provides fault tolerance using replication.
- Allows horizontal scalability by adding more machines.

### Key Hadoop Components

- NameNode → Manages metadata.
- DataNode → Stores actual data blocks.

Why HDFS?

- Can store terabytes or petabytes of data.
- Works on commodity hardware.
- Ensures data reliability even if a node fails.

---

## 3. Data Processing

### A) Hadoop MapReduce

MapReduce is Hadoop’s batch processing model.

It works in two phases:

1. Map Phase  
   - Processes input data.
   - Converts raw data into key-value pairs.

2. Reduce Phase  
   - Aggregates results from the map phase.
   - Produces final output.

Example:
Counting product sales from millions of transaction records.

---

### B) PySpark (Apache Spark with Python)

PySpark is the Python API for Apache Spark.

Spark improves performance compared to traditional MapReduce by:

- Performing in-memory processing.
- Supporting real-time and batch processing.
- Providing faster computation.

Why PySpark?

- Easy to write code using Python.
- Supports DataFrames and SQL-like operations.
- Suitable for machine learning and analytics.

---

## 4. Example Workflow using Hadoop + PySpark

Scenario: Analyze e-commerce sales data.

Step 1:
Transaction data is stored in HDFS.

Step 2:
PySpark reads data from HDFS.

Step 3:
Data is processed to calculate:
- Total sales
- Most purchased products
- Customer purchase trends

Step 4:
Results are stored back into HDFS or exported for reporting.

---

## Sample PySpark Code Example

```python
from pyspark.sql import SparkSession

spark = (
    SparkSession.builder
        .appName("SalesAnalysis")
        .getOrCreate()
)

# Load data from HDFS
df = spark.read.csv("hdfs://path/to/sales.csv", header=True, inferSchema=True)

# Calculate total sales per product
result = df.groupBy("product_name").sum("amount")

result.show()
```

## Key Concepts in Hadoop + PySpark Implementation

- Distributed Storage (HDFS)

- Distributed Processing (Spark)

- Parallel Execution

- Fault Tolerance

- Scalability by adding nodes

Together, Hadoop handles large-scale storage, while PySpark performs fast and efficient data processing and analysis.

</details>


<details><summary>Summary</summary> 

- Big Data is a group of data that is massive in volume and increasing exponentially.
- It is complex and cannot be handled efficiently by traditional data management systems.
- Big Data could be:
  - Structured  
  - Semi-structured  
  - Quasi-structured  
  - Unstructured  

![variety](Images/variety.PNG)

- **Volume, Variety, Velocity, Variability, and Value are key Big Data characteristics.**
- Big Data enables better decision-making, predictive analytics, and innovation across industries.
- Technologies such as Hadoop and Spark help manage and process Big Data effectively.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>
