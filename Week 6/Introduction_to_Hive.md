<details><summary> Learning Objectives </summary>

By the end of this lesson, learners should be able to:

-   Understand why Apache Hive is used in big data ecosystems.
-   Explain the modern Hive architecture and execution engines (Tez,
    Spark).
-   Identify how Hive stores data in HDFS and cloud storage systems.
-   Modify Hive warehouse storage locations.
-   Understand the Hive Metastore and its deployment modes.
-   Connect to Hive using Python.
-   Compare Hive with modern alternatives such as Spark SQL and Presto.
</details>

<details><summary> Description </summary>

Apache Hive is an open-source distributed data warehouse system built on
top of Hadoop. It enables users to query and analyze massive datasets
stored in distributed storage systems using SQL-like queries called Hive
Query Language (HQL).

Originally developed by Facebook and later contributed to the Apache
Software Foundation, Hive was designed to make big data querying
accessible to users familiar with SQL.

### Why Hive?

Traditional relational databases struggle when:

-   Data grows into terabytes or petabytes.
-   Horizontal scalability is required.
-   Fault tolerance is necessary.
-   Schema flexibility is important.

Hive addresses these challenges by:

-   Allowing SQL-based querying on distributed storage.
-   Scaling horizontally across clusters.
-   Providing fault tolerance through HDFS replication.
-   Supporting schema-on-read design.

### Modern Hive Execution Engines

Earlier versions of Hive relied heavily on MapReduce. Modern Hive
deployments primarily use:

-   Apache Tez (default in many clusters)
-   Apache Spark (optional execution engine)
-   MapReduce (legacy support)

### Hive Architecture Overview

1.  Clients (CLI, Beeline, JDBC, ODBC, Python via PyHive)
2.  HiveServer2 (handles sessions and client communication)
3.  Driver (parses and manages queries)
4.  Compiler & Optimizer (creates optimized execution plan)
5.  Execution Engine (Tez/Spark/MapReduce)
6.  Storage Layer (HDFS or Cloud Object Storage)

### Hive Storage Location

By default, Hive stores tables in:

/user/hive/warehouse

Each database is stored as a subdirectory inside the warehouse
directory.

### Hive Metastore

The Hive Metastore stores metadata including:

-   Table schema
-   Column data types
-   Partition information
-   Storage format
-   File locations

Production deployments typically use MySQL or PostgreSQL instead of the
default embedded Derby database.

### Metastore Deployment Modes

1.  Embedded Mode (Development only, single session)
2.  Local Mode (Metastore in same JVM, external database)
3.  Remote Mode (Production standard, separate metastore service)

### Limitations of Hive

Modern Hive supports ACID transactions, subqueries, and basic
UPDATE/DELETE operations. However:

-   It is not suitable for high-frequency OLTP workloads.
-   Query latency is higher than interactive engines.
-   It is optimized primarily for batch analytics.

</details>

<details><summary> Real World Application </summary>

Hive is widely used in industries that manage massive structured
datasets.

### Banking and Finance

-   Risk analysis
-   Fraud detection
-   Loan portfolio management
-   Regulatory reporting

### Retail and E-commerce

-   Customer behavior analytics
-   Purchase pattern analysis
-   Promotion effectiveness tracking
-   Inventory analysis

### Healthcare

-   Disease trend analysis
-   Medical research data aggregation
-   Reporting and compliance analytics

### Log and Event Processing

-   Application log analytics
-   Clickstream analysis
-   Batch ETL pipelines

Hive is particularly useful when large-scale historical data analysis is
required rather than real-time processing.

</details>

<details><summary> Implementation </summary>

### Example Hive Query

```sql
SELECT fname, id, AVG(marks) FROM students WHERE class IN
('10th','11th') GROUP BY id HAVING AVG(marks) \> 50 ORDER BY AVG(marks);
```

### Viewing Execution Plan

```sql
EXPLAIN SELECT * FROM students;
```
### Checking Table Location

```sql
DESCRIBE FORMATTED table_name;
```

### Creating Table with Custom Location

```sql
CREATE TABLE test ( name STRING, id INT ) ROW FORMAT DELIMITED FIELDS
TERMINATED BY ',' STORED AS TEXTFILE LOCATION '/user/demo/test';
```

### Altering Table Location

```sql
ALTER TABLE test SET LOCATION '/user/new_location';
```

### Changing Default Warehouse Location

In hive-site.xml:

```xml
<property>
<name>hive.metastore.warehouse.dir</name>
<value>/data/hive/warehouse</value>
</property>
```

## Python Integration with Hive

Hive can be accessed using Python through the PyHive library.

### Installing PyHive

pip install pyhive

### Connecting to Hive

``` python
from pyhive import hive

conn = hive.Connection(
    host="localhost",
    port=10000,
    username="hive"
)

cursor = conn.cursor()
cursor.execute("SHOW DATABASES")

for db in cursor.fetchall():
    print(db)
```

### Running a Query

``` python
cursor.execute("""
SELECT class, AVG(marks)
FROM students
GROUP BY class
HAVING AVG(marks) > 50
""")

results = cursor.fetchall()
print(results)
```
</details>

<details><summary> Summary </summary>

Apache Hive is a distributed SQL-based data warehouse system built for
large-scale batch analytics. It enables organizations to store and
process massive datasets using familiar SQL syntax.

Modern Hive integrates with execution engines such as Tez and Spark,
supports ACID transactions, and works seamlessly with distributed
storage systems like HDFS and cloud object storage.

Hive remains highly relevant for:

-   Large-scale ETL workflows
-   Historical data analytics
-   Enterprise data warehousing

For real-time and interactive analytics, engines like Spark SQL or
Presto are often preferred. However, Hive continues to be a foundational
technology in many big data ecosystems, especially in batch-oriented
data processing pipelines.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>