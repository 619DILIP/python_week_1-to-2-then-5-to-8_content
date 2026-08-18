<details><summary> Learning Objectives </summary>

After completing this lesson, learners should be able to:

-   Understand CRUD (Create, Read, Update, Delete) operations in Hive.
-   Configure Hive for ACID transactional support.
-   Create transactional tables using ORC format.
-   Insert, load, update, and delete records in Hive tables.
-   Execute Hive queries using Python.
-   Understand when to use INSERT vs LOAD DATA.
-   Apply filtering and conditional logic in SELECT, UPDATE, and DELETE
    statements.

</details>

<details><summary> Description </summary>

Hive supports SQL-like operations for managing large datasets stored in
distributed storage systems such as HDFS or cloud object storage.

In modern Hive versions (Hive 3.x and above), ACID transactions are
fully supported, allowing:

-   INSERT
-   UPDATE
-   DELETE
-   MERGE

However, transactional operations require proper configuration.

### ACID Requirements for Hive Tables

To perform UPDATE and DELETE operations:

-   Table must be stored as ORC.
-   Table must be transactional.
-   Bucketing is handled automatically in Hive 3+, but older versions
    require CLUSTERED BY.
-   Hive must be configured with a transactional manager.

### Basic CRUD Operations in Hive

CRUD stands for:

-   Create → Databases and Tables
-   Read → SELECT queries
-   Update → UPDATE statements (Transactional tables only)
-   Delete → DELETE statements (Transactional tables only)

</details>

<details><summary> Real World Application </summary>

Organizations manage structured datasets such as:

-   Customer records
-   Sales transactions
-   Student performance data
-   Banking transactions

Example scenarios:

### Banking Systems

Updating customer risk score periodically.

### Retail Platforms

Deleting duplicate product entries.

### Education Systems

Updating student marks after re-evaluation.

### Data Warehousing

Bulk inserting historical sales data into reporting tables.

Hive CRUD operations allow structured modification of analytical
datasets, especially in batch-driven environments.

</details>

<details><summary> Implementation </summary>

### Step 1: Check Hive Version

``` bash
hive --version
```

Ensure Hive 3.x or above for full ACID support.

------------------------------------------------------------------------

### Step 2: Configure Hive for Transactions

In hive-site.xml:

    hive.support.concurrency = true
    hive.txn.manager = org.apache.hadoop.hive.ql.lockmgr.DbTxnManager
    hive.compactor.initiator.on = true
    hive.compactor.worker.threads = 1
    hive.exec.dynamic.partition.mode = nonstrict

Restart Hive services after configuration changes.

------------------------------------------------------------------------

### Step 3: Create Database

``` sql
CREATE DATABASE IF NOT EXISTS School;
```

------------------------------------------------------------------------

### Step 4: Create Transactional Table

``` sql
CREATE TABLE IF NOT EXISTS School.student (
    Student_Name STRING,
    Student_Rollno INT,
    Student_Marks FLOAT
)
STORED AS ORC
TBLPROPERTIES ('transactional'='true');
```

Verify table structure:

``` sql
DESCRIBE FORMATTED School.student;
```

------------------------------------------------------------------------

### Step 5: Insert Data

#### Method 1: INSERT INTO

``` sql
INSERT INTO School.student VALUES
('Daniel', 1, 95.0),
('Akshat', 2, 96.0),
('Andrew', 3, 90.0);
```

#### Method 2: LOAD DATA

``` sql
LOAD DATA LOCAL INPATH '/home/user/data.csv'
INTO TABLE School.student;
```

Use LOAD DATA for bulk ingestion from files.

------------------------------------------------------------------------

### Step 6: SELECT Query

``` sql
SELECT * FROM School.student;
```

Example with condition:

``` sql
SELECT Student_Name, Student_Marks
FROM School.student
WHERE Student_Marks > 90;
```

------------------------------------------------------------------------

### Step 7: UPDATE Query

``` sql
UPDATE School.student
SET Student_Marks = 92
WHERE Student_Name = 'Andrew';
```

------------------------------------------------------------------------

### Step 8: DELETE Query

``` sql
DELETE FROM School.student
WHERE Student_Rollno = 3;
```

------------------------------------------------------------------------

## Python Integration Example

Install PyHive:

``` bash
pip install pyhive
```

### Connect to Hive Using Python

``` python
from pyhive import hive

conn = hive.Connection(
    host="localhost",
    port=10000,
    username="hive"
)

cursor = conn.cursor()

# Insert example
cursor.execute("""
INSERT INTO School.student VALUES ('Ravi', 4, 88.0)
""")

# Select example
cursor.execute("SELECT * FROM School.student")
results = cursor.fetchall()

for row in results:
    print(row)
```

Python allows Hive queries to be integrated into:

-   ETL pipelines
-   Reporting systems
-   Data validation scripts
-   Automation workflows

</details>

<details><summary> Summary </summary>

Hive supports structured data manipulation through SQL-like CRUD
operations.

For transactional behavior:

-   Tables must be stored in ORC format.
-   Transactional properties must be enabled.
-   Proper Hive configuration is required.

CRUD operations in Hive include:

-   CREATE DATABASE and CREATE TABLE
-   INSERT and LOAD DATA
-   SELECT queries
-   UPDATE statements (Transactional tables)
-   DELETE statements (Transactional tables)

Modern Hive supports ACID compliance, making it suitable for controlled
updates and deletes in large-scale analytical environments.

Hive integrates seamlessly with Python using libraries such as PyHive,
enabling data engineers to automate queries and embed Hive workflows
into modern data pipelines.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>