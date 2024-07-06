# Azure-Data-Engineer

#








Preparing for a Spark Interview? Here are 20 Key Differences You Should Know!

Repartition vs. Coalesce: Repartition changes the number of partitions, while coalesce reduces partitions without full shuffle.
Sort By vs. Order By: Sort By sorts data within each partition and may result in partially ordered final results if multiple reducers are used.
Order By guarantees total order across all partitions in the final output.
RDD vs. Datasets vs. DataFrames: RDDs are the basic abstraction, Datasets add type safety, and DataFrames optimize for structured data.
Broadcast Join vs. Shuffle Join vs. Sort Merge Join: Broadcast Join is for small tables, Shuffle Join redistributes data, and Sort Merge Join sorts data before joining.
Spark Session vs. Spark Context: Spark Session is the entry point in Spark 2.0+, combining functionality of Spark Context and SQL Context.
Executor vs. Executor Core: Executor runs tasks and manages data storage, while Executor Core handles task execution.
DAG VS. Lineage: DAG (Directed Acyclic Graph) is the execution plan, while Lineage tracks the RDD lineage for fault tolerance.
8 Transformation vs. Action: Transformation creates RDD/Dataset/ DataFrame, while Action triggers execution and returns results to driver.
9 Narrow Transformation vs. Wide Transformation: Narrow operates on single partition, while Wide involves shuffling across partitions.
10 Lazy Evaluation vs. Eager Evaluation: Spark delays execution until action is called (Lazy), optimizing performance.
11 Window Functions vs. Group By: Window Functions compute over a range of rows, while Group By aggregates data into summary.
12 Partitioning vs. Bucketing: Partitioning divides data into logical units, while Bucketing organizes data into equal-sized buckets.
1) (3) Avro vs. Parquet vs. ORC: Avro is row-based with schema, Parquet and ORC are columnar formats optimized for query speed.
Client Mode vs. Cluster Mode: Client runs driver in client process, while Cluster deploys driver to the cluster.
1 5 Serialization vs. Deserialization: Serialization converts data to byte stream, while Deserialization reconstructs data from byte stream.
1) 6) DAG Scheduler vs. Task Scheduler: DAG Scheduler divides job into stages, while Task Scheduler assigns tasks to workers.
TZ Accumulators vs. Broadcast Variables: Accumulators aggregate values from workers to driver, Broadcast Variables efficiently broadcast read-only variables.
1 8 Cache vs. Persist: Cache stores RDD/Dataset/DataFrame in memory, Persist allows choosing storage level (memory, disk, etc.).
1 9 Internal Table vs. External Table: Internal managed by Spark, External managed externally (e.g., Hive).
20 Executor vs. Driver: Executor runs tasks on worker nodes, Driver manages job execution.

