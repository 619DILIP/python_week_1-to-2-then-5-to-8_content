<details><summary>Learning Objectives</summary>

After completing this module, learners should be able to:

- Understand how Spark processes streaming data
- Read streaming data from different sources
- Apply transformations on streaming data
- Write streaming output to different sinks
- Understand streaming query lifecycle
- Implement real-time streaming pipelines

</details>

<details><summary>Description</summary>

## What is Stream Processing in Spark?

Stream processing is the continuous processing of incoming data in
real-time or near real-time.

Spark uses Structured Streaming to process streaming data as an
unbounded table.

Unlike batch processing, streaming processes data continuously.

---

## How Spark Processes Streaming Data

Spark Structured Streaming follows these steps:

1.  Read streaming data from a source.
2.  Treat incoming data as a streaming DataFrame.
3.  Apply transformations.
4.  Write processed data to an output sink.
5.  Repeat continuously.

---

## Streaming Components

### Source

Input systems such as:

- Kafka
- Socket
- Files
- Rate source

---

### Transformation

Operations such as:

- filter()
- select()
- groupBy()
- aggregation

---

### Sink

Output systems such as:

- Console
- Files
- Kafka
- Databases

---

### Streaming Query

A streaming query continuously processes data until stopped.

---

## Streaming Execution Model

Spark divides incoming data into micro-batches.

Each micro-batch is processed as a Spark job.

---

## Fault Tolerance

Spark Streaming provides:

- Checkpointing
- Exactly-once processing guarantees
- Automatic recovery

</details>

<details><summary>Real World Application</summary>

## 1. Real-Time Log Processing

Applications stream logs continuously.

Spark processes logs to detect errors instantly.

---

## 2. Fraud Detection

Banks analyze transactions in real-time.

Spark identifies suspicious activities.

---

## 3. IoT Monitoring

Sensors send real-time data.

Spark processes sensor readings to detect anomalies.

---

## 4. Real-Time Analytics

E-commerce platforms track user activity.

Spark updates dashboards in real-time.

---

## 5. Monitoring Systems

Spark processes system metrics continuously.

Alerts are generated based on thresholds.

</details>

<details><summary>Implementation</summary>

## Step 1: Create Spark Session

```python
from pyspark.sql import SparkSession

spark = (
    SparkSession.builder
    .appName("StreamProcessingExample")
    .getOrCreate()
)
```

---

## Step 2: Read Streaming Data from Socket

```python
stream_df = (
    spark.readStream
    .format("socket")
    .option("host", "localhost")
    .option("port", 9999)
    .load()
)
```

---

## Step 3: Apply Transformation

```python
from pyspark.sql.functions import split, explode

words = (
    stream_df
    .select(explode(split(stream_df.value, " ")).alias("word"))
)

word_count = words.groupBy("word").count()
```

---

## Step 4: Write Streaming Output

```python
query = (
    word_count.writeStream
    .outputMode("complete")
    .format("console")
    .start()
)
```

---

## Step 5: Start Streaming Query

```python
query.awaitTermination()
```

---

## Step 6: Using Checkpointing

```python
query = (
    word_count.writeStream
    .outputMode("complete")
    .option("checkpointLocation", "/tmp/checkpoint")
    .format("console")
    .start()
)
```

Checkpointing ensures recovery after failure.

---

## Step 7: Stop Streaming

```python
query.stop()
```

</details>

<details><summary>Summary</summary>

In this module, we learned:

- Spark processes streaming data using Structured Streaming
- Streaming data is processed as micro-batches
- Streaming pipelines consist of source, transformation, and sink
- Streaming queries run continuously
- Checkpointing ensures fault tolerance
- Spark Streaming is used in fraud detection, monitoring, and analytics

Spark Structured Streaming enables scalable and fault-tolerant real-time
data processing.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>
