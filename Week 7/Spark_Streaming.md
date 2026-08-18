<details><summary>Learning Objectives</summary>

After completing this module, learners should be able to:

- Define Spark Streaming
- Understand the difference between batch and stream processing
- Explain micro-batch processing in Spark
- Identify components of Spark Streaming architecture
- Implement basic streaming pipelines
- Handle real-time data sources

</details>

<details><summary>Description</summary>

## What is Spark Streaming?

Spark Streaming is a scalable, fault-tolerant stream processing system
built on top of Apache Spark. It enables processing of real-time data
streams.

Unlike traditional batch processing, Spark Streaming processes data
continuously in small chunks called micro-batches.

---

## Batch vs Streaming

### Batch Processing

- Processes large volumes of data at once
- Higher latency
- Suitable for historical analytics

### Stream Processing

- Processes data continuously
- Low latency
- Suitable for real-time analytics

---

## How Spark Streaming Works

Spark Streaming follows the micro-batch architecture:

1.  Data is ingested from streaming sources.
2.  Data is divided into small batches.
3.  Each batch is processed using Spark engine.
4.  Results are stored or pushed to output systems.

Internally: Input Stream → Micro-batches → Spark Jobs → Output Sink

---

## Structured Streaming

Modern Spark uses Structured Streaming, built on Spark SQL engine.

Features: - Declarative API - Fault tolerance - Exactly-once
guarantees - Automatic state management

---

## Supported Sources

Spark Streaming supports:

- Kafka
- File systems
- Sockets
- AWS Kinesis
- Rate source (for testing)

---

## Output Modes

- append → Only new rows are written
- complete → Entire result table is written
- update → Only updated rows are written

---

## Fault Tolerance

Spark Streaming ensures:

- Checkpointing
- Write-ahead logs
- Exactly-once processing (when configured properly)

</details>

<details><summary>Real World Application</summary>

## 1. Fraud Detection

Banks process transaction streams in real-time to detect suspicious
activity.

---

## 2. Log Monitoring

Streaming logs from applications: - Detect errors instantly - Trigger
alerts

---

## 3. IoT Data Processing

Sensor data from devices: - Real-time analytics - Equipment failure
prediction

---

## 4. Real-Time Recommendation Systems

E-commerce platforms: - Process user clicks - Update recommendations
instantly

---

## 5. Social Media Analytics

Monitor trending topics and sentiment analysis in real-time.

</details>

<details><summary>Implementation</summary>

## Creating Spark Session

```python
from pyspark.sql import SparkSession

spark = (
    SparkSession.builder
    .appName("SparkStreamingExample")
    .getOrCreate()
)
```

---

## Example 1: Streaming from Socket

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

## Example 2: Word Count Streaming

```python
from pyspark.sql.functions import explode, split

words = stream_df.select(
    explode(
        split(stream_df.value, " ")
    ).alias("word")
)

word_counts = words.groupBy("word").count()
```

---

## Writing Stream to Console

```python
query = (
    word_counts.writeStream
    .outputMode("complete")
    .format("console")
    .start()
)

query.awaitTermination()
```

---

## Example 3: Streaming from Kafka

```python
kafka_df = (
    spark.readStream
    .format("kafka")
    .option("kafka.bootstrap.servers", "localhost:9092")
    .option("subscribe", "topic_name")
    .load()
)
```

---

## Using Checkpointing

```python
query = (
    word_counts.writeStream
    .outputMode("complete")
    .option("checkpointLocation", "/tmp/checkpoints")
    .format("console")
    .start()
)
```

Checkpointing ensures fault tolerance.

</details>

<details><summary>Summary</summary>

In this module, we learned:

- Spark Streaming processes real-time data using micro-batches
- Structured Streaming is the modern streaming API
- It supports multiple real-time data sources
- Output modes control how results are written
- Checkpointing ensures fault tolerance
- Streaming is widely used in fraud detection, monitoring, IoT, and
  recommendation systems

Spark Streaming enables scalable, fault-tolerant real-time data
processing in distributed environments.

</details>

<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)

</details>
