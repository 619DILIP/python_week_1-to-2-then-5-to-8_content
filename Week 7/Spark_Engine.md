<details><summary>Learning Objectives</summary>

After completing this module, learners should be able to:

- Define the Spark Engine
- Explain how the Spark execution engine works
- Understand DAG, stages, and tasks
- Describe how Spark schedules jobs
- Identify key components involved in execution
- Monitor Spark Engine performance

</details>

<details><summary>Description</summary>

## What is the Spark Engine?

The Spark Engine is the core execution engine of Apache Spark. It is
responsible for:

- Task scheduling
- Memory management
- Fault recovery
- Interaction with storage systems
- Distributed computation

The Spark Engine executes transformations and actions across distributed
executors.

---

## How Spark Engine Works

When a Spark application runs:

1.  User code is submitted to the Driver.
2.  The Driver builds a Logical Plan.
3.  The plan is optimized into a Physical Plan.
4.  A DAG (Directed Acyclic Graph) is created.
5.  The DAG is divided into stages.
6.  Each stage is divided into tasks.
7.  Tasks are distributed to Executors.
8.  Results are returned to the Driver.

---

## DAG (Directed Acyclic Graph)

- Represents the computation workflow.
- Created based on transformations.
- Optimizes execution before running.

---

## Stages and Tasks

Stage: - A group of tasks that can be executed without shuffle.

Task: - Smallest unit of work. - Executes on a single partition.

---

## Task Scheduling

Spark Engine uses:

- Task Scheduler
- DAG Scheduler

DAG Scheduler: - Divides jobs into stages.

Task Scheduler: - Assigns tasks to executors.

---

## Fault Tolerance

Spark Engine ensures fault tolerance by:

- Recomputing lost partitions
- Using lineage information
- Retrying failed tasks

---

## Memory Management

Spark Engine manages:

- Execution Memory (for shuffle, joins, aggregation)
- Storage Memory (for caching)

Proper memory configuration improves performance.

</details>

<details><summary>Real World Application</summary>

## 1. Large-Scale Data Processing

Companies process terabytes of data using Spark Engine's distributed
task scheduling.

---

## 2. Machine Learning Workloads

Spark Engine efficiently handles iterative algorithms using in-memory
processing.

---

## 3. Streaming Pipelines

Structured Streaming relies on the Spark Engine to process
micro-batches.

---

## 4. Data Warehousing

Spark SQL queries are executed by the Spark Engine across clusters.

---

## 5. ETL Systems

The engine executes complex transformations in parallel to reduce
processing time.

</details>

<details><summary>Implementation</summary>

## Example: Understanding DAG Creation

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("SparkEngineExample").getOrCreate()

rdd = spark.sparkContext.parallelize([1,2,3,4,5])

result = (
    rdd
    .map(lambda x: x * 2)
    .filter(lambda x: x > 5)
)

result.collect()
```

This creates: - Logical Plan - Physical Plan - DAG - Stage(s) - Task(s)

---

## Viewing DAG in Spark UI

1.  Run Spark job.
2.  Open Spark UI (http://localhost:4040).
3.  Navigate to:
    - Jobs tab
    - Stages tab
    - DAG Visualization

---

## Checking Task Distribution

```python
rdd = spark.sparkContext.parallelize(range(100), 4)
rdd.getNumPartitions()
```

More partitions → More parallel tasks.

---

## Example: Shuffle Stage

```python
pairs = rdd.map(lambda x: (x % 2, x))
pairs.reduceByKey(lambda a, b: a + b).collect()
```

reduceByKey creates a shuffle stage in the DAG.

</details>

<details><summary>Summary</summary>

In this module, we learned:

- Spark Engine is the core execution component of Spark.
- It builds logical and physical plans.
- It creates a DAG for execution.
- Jobs are divided into stages and tasks.
- DAG Scheduler and Task Scheduler coordinate execution.
- Fault tolerance is achieved using lineage.
- Spark UI helps monitor engine execution.

The Spark Engine is responsible for scalable, distributed, and
fault-tolerant execution of Spark applications.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>
