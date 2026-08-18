<details><summary>Learning Objectives</summary>

After completing this module, learners should be able to:

- Understand why Spark optimization is important
- Identify common performance bottlenecks
- Apply optimization techniques in Spark
- Optimize shuffle operations
- Tune partitioning strategies
- Use caching and persistence effectively
- Monitor performance using Spark UI

</details>

<details><summary>Description</summary>

## What is Spark Optimization?

Spark Optimization refers to techniques used to improve the performance,
scalability, and resource utilization of Spark applications.

Optimization helps to:

- Reduce execution time
- Improve parallelism
- Minimize shuffle overhead
- Avoid memory errors
- Efficiently utilize cluster resources

---

## Common Performance Bottlenecks

### 1. Too Few or Too Many Partitions

- Too few → underutilized cluster
- Too many → scheduling overhead

### 2. Data Skew

- Uneven distribution of data across partitions
- Causes some tasks to run much longer

### 3. Excessive Shuffle

- groupByKey(), join(), distinct() cause shuffle
- Shuffle increases disk and network I/O

### 4. Driver Bottleneck

- Using collect() on large datasets
- Large broadcast variables

### 5. Improper Resource Configuration

- Insufficient executor memory
- Too many cores per executor

---

## Optimization Techniques

### 1. Use reduceByKey Instead of groupByKey

reduceByKey performs map-side combine and reduces shuffle size.

---

### 2. Optimize Partitions

Use:

- repartition() to increase partitions
- coalesce() to reduce partitions

---

### 3. Cache Reused Data

Use cache() or persist() when dataset is reused multiple times.

---

### 4. Avoid Large collect()

Instead of:

large_df.collect()

Use:

large_df.limit(100).show()

---

### 5. Broadcast Small Tables

For joins:

from pyspark.sql.functions import broadcast

df1.join(broadcast(df2), "key")

---

### 6. Use Proper File Formats

Prefer:

- Parquet\
- ORC

They are columnar and optimized.

---

### 7. Tune Shuffle Partitions

spark.sql.shuffle.partitions controls shuffle parallelism.

Default: 200

---

### 8. Use Predicate Pushdown

Filter early before joins or aggregations.

---

## Monitoring Optimization

Use Spark UI:

- Jobs Tab
- Stages Tab
- Storage Tab
- Executors Tab

Check:

- Shuffle read/write size
- Task time variance
- Skewed tasks

</details>

<details><summary>Real World Application</summary>

## 1. Large ETL Pipelines

Optimizing partitions and shuffle reduces job time from hours to
minutes.

---

## 2. Machine Learning Workloads

Caching intermediate results reduces iterative training time.

---

## 3. Real-Time Analytics

Reducing shuffle improves streaming latency.

---

## 4. Cloud Cost Optimization

Efficient Spark jobs reduce infrastructure cost in cloud environments.

---

## 5. Handling Big Data Warehouses

Using columnar formats and partition pruning improves query performance.

</details>

<details><summary>Implementation</summary>

## Example 1: Optimizing groupByKey()

Bad Practice:

```python
pairs.groupByKey().mapValues(lambda vals: sum(vals)).collect()
```

Optimized:

```python
pairs.reduceByKey(lambda a, b: a + b).collect()
```

---

## Example 2: Repartitioning

```python
df = spark.read.csv("data.csv")
df = df.repartition(8)
```

---

## Example 3: Caching

```python
df.cache()
df.count()
```

---

## Example 4: Broadcast Join

```python
from pyspark.sql.functions import broadcast

result = df1.join(broadcast(df2), "id")
```

---

## Example 5: Adjust Shuffle Partitions

```python
spark.conf.set("spark.sql.shuffle.partitions", "100")
```

---

## Example 6: Viewing Execution Plan

```python
df.explain(True)
```

This shows logical and physical plans.

</details>

<details><summary>Summary</summary>

In this module, we learned:

- Spark optimization improves performance and scalability
- Common bottlenecks include shuffle, skew, and memory issues
- reduceByKey is better than groupByKey for aggregation
- Proper partitioning improves parallelism
- Caching helps when data is reused
- Broadcast joins reduce shuffle
- Spark UI helps diagnose performance problems

Optimization is critical for building efficient and scalable Spark applications.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>
