# Azure-Data-Engineer

List of Question and Scenario Based

- [Azure-Data-Engineer](#azure-data-engineer)
  - [*Preparing for a Spark Interview? Here are **20 Key Differences You Should Know!***](#preparing-for-a-spark-interview-here-are-20-key-differences-you-should-know)
  - [**Scenario-based questions** that are typically asked in **Databricks interviews**](#scenario-based-questions-that-are-typically-asked-in-databricks-interviews)
  - [**Data Engineer Scenario based interview** !!](#data-engineer-scenario-based-interview-)
  - [Scenario-based Power BI interview question at Accenture](#scenario-based-power-bi-interview-question-at-accenture)
  - [**PySpark Data Engineer Interview** at Big 4 - KPMG India](#pyspark-data-engineer-interview-at-big-4---kpmg-india)
  - [**Important Interview Question On Spark**](#important-interview-question-on-spark)
  - [**Important SQL questions**](#important-sql-questions)
  - [**Important Python questions**](#important-python-questions)
  - [**Top 10 advanced SQL interview questions**](#top-10-advanced-sql-interview-questions)



---

## *Preparing for a Spark Interview? Here are **20 Key Differences You Should Know!***


1. **Repartition vs. Coalesce**: Repartition changes the number of partitions, while coalesce reduces partitions without full shuffle.

1. **Sort By vs. Order By**: Sort By sorts data within each partition and may result in partially ordered final results if multiple reducers are used.
Order By guarantees total order across all partitions in the final output.

1. **RDD vs. Datasets vs. DataFrames**: RDDs are the basic abstraction, Datasets add type safety, and DataFrames optimize for structured data.

1. **Broadcast Join vs. Shuffle Join vs. Sort Merge Join**: Broadcast Join is for small tables, Shuffle Join redistributes data, and Sort Merge Join sorts data before joining.

1. **Spark Session vs. Spark Context**: Spark Session is the entry point in Spark 2.0+, combining functionality of Spark Context and SQL Context.
  
1. **Executor vs. Executor Core**: Executor runs tasks and manages data storage, while Executor Core handles task execution.

1. **DAG VS. Lineage**: DAG (Directed Acyclic Graph) is the execution plan, while Lineage tracks the RDD lineage for fault tolerance.

1. **Transformation vs. Action**: Transformation creates RDD/Dataset/ DataFrame, while Action triggers execution and returns results to driver.

1. **Narrow Transformation vs. Wide Transformation**: Narrow operates on single partition, while Wide involves shuffling across partitions.

1. **Lazy Evaluation vs. Eager Evaluation**: Spark delays execution until action is called (Lazy), optimizing performance.

1. **Window Functions vs. Group By**: Window Functions compute over a range of rows, while Group By aggregates data into summary.

1. **Partitioning vs. Bucketing**: Partitioning divides data into logical units, while Bucketing organizes data into equal-sized buckets.

1. **Avro vs. Parquet vs. ORC**: Avro is row-based with schema, Parquet and ORC are columnar formats optimized for query speed.

1. **Client Mode vs. Cluster Mode**: Client runs driver in client process, while Cluster deploys driver to the cluster.

1. **Serialization vs. Deserialization**: Serialization converts data to byte stream, while Deserialization reconstructs data from byte stream.

1. **DAG Scheduler vs. Task Scheduler**: DAG Scheduler divides job into stages, while Task Scheduler assigns tasks to workers.

1. **TZ Accumulators vs. Broadcast Variables**: Accumulators aggregate values from workers to driver, Broadcast Variables efficiently broadcast read-only variables.

1. **Cache vs. Persist**: Cache stores RDD/Dataset/DataFrame in memory, Persist allows choosing storage level (memory, disk, etc.).

1. **Internal Table vs. External Table**: Internal managed by Spark, External managed externally (e.g., Hive).

1. **Executor vs. Driver**: Executor runs tasks on worker nodes, Driver manages job execution.

---

## **Scenario-based questions** that are typically asked in **Databricks interviews**


1. **Scenario**: You have a large dataset with skewed data. How would you optimize a join operation?
   
    **Answer**:
    - Utilize Adaptive Query Execution (AQE) for dynamic optimization
    - Consider broadcast joins for smaller tables
    - Use salting techniques to distribute skewed keys
    - Implement bucketing on join columns


1. **Scenario**: You need to process a stream of data in near real-time. How would you approach this using Databricks?
 
    **Answer**:
    - Use Structured Streaming in Databricks
    - Set up a streaming source (e.g., Kafka, Event Hubs)
    - Define the streaming query and output sink
    - Implement watermarking and windowing for late data handling


2. **Scenario**: You're dealing with sensitive data. How would you ensure data security in Databricks?
   
    **Answer**:
    - Implement table access control (ACLs)
    - Use Databricks secrets for managing credentials
    - Enable encryption at rest and in transit
    - Implement column-level encryption for highly sensitive data
    - Use Databricks' integration with Azure AD or AWS IAM for authentication
  
3. **Scenario**: Your Spark job is running slowly. How would you diagnose and optimize it?
   
    **Answer**:
    - Check the Spark Ul for stage details and bottlenecks
    - Look for data skew, shuffle operations, or spilling to disk
    - Optimize join operations (broadcast vs. shuffle hash join)
    - Adjust partitioning and caching strategies
    - Use Databricks' Query Optimization Advisor
  
4. **Scenario**: You need to implement a machine learning pipeline in Databricks. How would you approach this?
   
    **Answer**:
    - Use MLflow for experiment tracking and model management
    - Leverage Spark MLlib for distributed ML algorithms
    - Implement feature engineering using Spark SQL and DataFrame operations
    - Use Databricks AutoML for quick prototyping
    - Set up model serving using MLflow and Databricks Model Serving
  
5. **Scenario**: You're migrating an on-premises data warehouse to Databricks. What steps would you take?


    **Answer**:
    - Assess current data and workloads
    - Design a new data architecture using Delta Lake
    - Use Databricks' ETL tools for data migration
    - Implement slowly changing dimensions using Delta Lake merge operations
    - Set up proper access controls and governance
    - Optimize query performance using Databricks SQL warehouses

---

## **Data Engineer Scenario based interview** !!


**Scenario 1**:

- **Interviewer**: Can you design a data warehouse for an e-commerce company with 10 million customers and 1 million orders per day?

- **Candidate**: Yes, I would design a data warehouse using Azure Synapse Analytics or Amazon Redshift, with a star schema architecture and appropriate indexing and partitioning to handle the large volume of data.

**Scenario 2**:

- **Interviewer**: How would you optimize a slow-performing query that takes 10 minutes to execute?

- **Candidate**: I would analyze the query plan, identify performance bottlenecks, and apply optimization techniques like indexing, caching, and query rewriting to reduce execution time to less than 1 minute.

**Scenario 3**:

- **Interviewer**: Can you integrate data from 5 different sources, including AP/s, databases, and files, into a single data platform?

- **Candidate**: Yes, I would use Azure Data Factory or Apache NiFi to integrate the data sources, transform and cleanse the data as needed, and load it into a unified data platform like Azure Data Lake Storage or Amazon S3.

**Scenario 4**:

- **Interviewer**: How would you ensure data security and compliance with regulations like GDPR and HIPAA?

- **Candidate**: I would implement encryption, access controls, data masking, and auditing to ensure data security and compliance, and regularly monitor and update security measures to ensure ongoing compliance.

**Scenario 5**:

- **Interviewer**: Can you design a real-time data streaming platform to process 1 million events per second?
    
- **Candidate**: Yes, I would design a platform using Apache Kafka or Amazon Kinesis, with appropriate clustering, partitioning, and replication to handle the high volume of data, and ensure real-time processing and analytics.

**Some additional questions and figures:**

   - **Interviewer**: How do you handle data quality issues in a data warehouse?
     - **Candidate**: I would implement data validation, data cleansing, and data quality checks to ensure data accuracy and completeness, and regularly monitor and improve data quality.

   - **Interviewer**: Can you optimize data storage costs for a large data lake?
     - **Candidate**: Yes, I would use data compression, data deduplication, and tiered storage to reduce storage costs by up to 50%.

   - **Interviewer**: How do you ensure data governance and compliance across multiple teams and departments?
     - **Candidate**: I would establish clear data governance policies, procedures, and standards, and regularly monitor and enforce compliance across teams and departments.


---

## Scenario-based Power BI interview question at Accenture


**I have a shared folder with files for 6 months, let's say from January to June. Whenever the file for July arrives, my Power Bl report should take files from February to July. How can I achieve this?**

**Answer**:

- First, make sure each data file has a date column.
- Load your 6 months of data using the folder connector in Power BI.
- After cleaning up and aligning the data in the query editor, create a custom column using the formula below:

```
let
CurrentDate = Date.From(DateTime.LocalNow), //
Get today's date
FirstDateOfCurrentMonth =
Date.StartOfMonth(CurrentDate),
// Get the first day of the current month
FirstDateOfSixMonthsAgo =
Date.AddMonths(FirstDateOfCurrentMonth, -6) // Get the first day of six months ago in
if [Date] >= FirstDateOfSixMonthsAgo then "Include" else "Exclude"
```

- Here, replace '[Date] with your date column's name.
- Filter the data to keep only rows where the custom column equals Include.
- Click Close & Apply to load the filtered data into
Power BI.
- As soon as you add the July file to the folder, the custom column will automatically exclude the January data.
- The filter ensures only the last 6 months' data (February to July) is included.
- When you add the August file, the custom column will exclude February and include March to August.
- That's it! Your Power Bl report will always show the most recent 6 months of data dynamically.

---

## **PySpark Data Engineer Interview** at Big 4 - KPMG India


**Introduction**:

1. Can you provide an overview of your experience working with PySpark and big data processing?
2. What motivated you to specialize in PySpark, and how have you applied it in your previous roles?


**PySpark Basics**:

1. Explain the basic architecture of PySpark.

**Answer**: 
- PySpark is a Python API for Apache Spark, enabling Python developers to harness Spark's capabilities. 
- Its architecture comprises a driver program and worker nodes. The driver runs the main application, creating SparkContext, which connects to a cluster manager (YARN, Mesos, or standalone). 
- The cluster manager allocates resources to worker nodes, where executors run tasks. Each task processes data and performs computations in parallel. 
- PySpark employs RDDs (Resilient Distributed Datasets) for fault-tolerant, distributed data processing, with transformations and actions to manipulate data efficiently. 
- This architecture ensures scalability and performance for big data analytics.

![Spark-Architecture](/img/Spark-Architecture.png)
  
2. How does PySpark relate to Apache Spark, and what advantages does it offer in distributed data processing?

**Answer**: 
- PySpark is the Python API for Apache Spark, allowing Python developers to use Spark's capabilities. 
- It integrates seamlessly with Spark, enabling the use of Python's rich ecosystem alongside Spark's powerful distributed computing framework. 
- PySpark offers advantages like easy integration with Hadoop, support for data parallelism and fault tolerance through RDDs (Resilient Distributed Datasets), and optimized in-memory computations. 
- It simplifies big data processing by providing high-level APIs for data manipulation and machine learning, making it accessible for Python users to perform scalable, efficient, and fast data processing across large clusters.

**DataFrame Operations**:

1. Describe the difference between a DataFrame and an RDD in PySpark.

**Answer**:
- RDDs are low-level, schema-less collections for distributed data processing, offering fine-grained control. 
- DataFrames are high-level, schema-based tables optimized for SQL-like operations and performance.
```python
# RDD example
rdd = sc.parallelize([1, 2, 3, 4])
# DataFrame example
df = spark.createDataFrame([(1, 'Alice'), (2, 'Bob')], ['id', 'name'])

```

2. Can you explain transformations and actions in PySpark DataFrabmes?

**Answer**:
- In PySpark DataFrames, transformations (e.g., select, filter, groupBy) are operations that define a new DataFrame from an existing one, without immediately computing results. 
- Actions (e.g., show, collect, write) trigger the execution of these transformations, producing and returning the final output.

3. Provide examples of PySpark DataFrame operations you frequently use.

**Answer**:
```python
# Creating a DataFrame
data = [(1, 'Alice', 28), (2, 'Bob', 35), (3, 'Cathy', 23)]
df = spark.createDataFrame(data, ['id', 'name', 'age'])

# Showing Data
df.show()

# Selecting Columns
df.select('name', 'age').show()

# Filtering Rows
df.filter(df['age'] > 30).show()

# Grouping and Aggregation
df.groupBy('age').count().show()

# Adding a Column
from pyspark.sql.functions import lit

df.withColumn('country', lit('USA')).show()

# Removing a Column
df.drop('age').show()

# Sorting Data
df.sort(df['age'].desc()).show()

# Joining DataFrames
data2 = [(1, 'New York'), (2, 'Los Angeles'), (4, 'Chicago')]
df2 = spark.createDataFrame(data2, ['id', 'city'])

df.join(df2, on='id', how='inner').show()

# Writing to Disk
df.write.csv('/path/to/save')
```

**Optimizing PySpark Jobs**:

1. How do you optimize the performance of PySpark jobs?

**Answer**:
- To optimize PySpark jobs, 
  - use DataFrames over RDDs for their built-in optimizations
  - cache/persist intermediate results
  - leverage partitioning to balance workloads
  - avoid shuffling by minimizing wide transformations
  - use broadcast variables for small data
  - configure Spark settings for resource allocation and parallelism

2. Can you discuss techniques for handling skewed data in PySpark?

**Answer**:
- To handle skewed data in PySpark, use techniques like salting (adding random keys to distribute skewed keys), adjusting partitioning, using repartition() or coalesce() to balance partitions, leveraging broadcast joins for smaller datasets, and employing custom partitioning strategies to evenly distribute workload.

**Data Serialization and Compression**:

1.  Explain how data serialization works in PySpark.
2.  Discuss the significance of choosing the right compression codec for your PySpark applications.

**Handling Missing Data**:

1.  How do you deal with missing or null values in PySpark DataFrames?

**Answer**:
- dropna() to remove rows with nulls
- fillna() to fill nulls with specified values
- replace() to replace specific values. 

2.  Are there any specific strategies or functions you prefer for handling missing data?

**Answer**:
- fillna() with appropriate replacement values or statistical measures like mean or median for numerical data.
- dropna() selectively removes rows or columns with nulls based on analysis needs, ensuring data quality and integrity throughout processing pipelines.


**Working with PySpark SQL**:

1.  Describe your experience with PySpark SQL.
2.  How do you execute SQL queries on PySpark DataFrames?

**Broadcasting in PySpark**:

1.  What is broadcasting, and how is it useful in PySpark?
2.  Provide an example scenario where broadcasting can significantly improve performance.
   
**PySpark Machine Learning**:

1.  Discuss your experience with PySpark's MLlib.
2.  Can you give examples of machine learning algorithms you've implemented using PySpark?


**Job Monitoring and Logging**:

1.  How do you monitor and troubleshoot PySpark Jobs?
2.  Describe the importance of logging in PySpark applications.
   
**Integration with Other Technologies**:

1.  Have you integrated PySpark with other big data technologies or databases? If so, please provide examples.
2.  How do you handle data transfer between PySpark and external systems?

**Real-world Project Scenario**:
1.  Explain the project that you worked on in your previous organizations.
2.  Describe a challenging PySpark project you've worked on. What were the key challenges, and how did you overcome them?

**Cluster Management**:
1.  Explain your experience with cluster management in PySpark.
2.  How do you scale PySpark applications in a cluster environment?

**PySpark Ecosystem**:
1.  Can you name and briefly describe some popular libraries or tools in the PySpark ecosystem, apart from the core PySpark functionality?


---

## **Important Interview Question On Spark**


1. Difference between RDD & Dataframes

**Answer**: RDDs are lower-level, immutable collections of data, while DataFrames are higher-level APIs with schema support, optimized for SQL-like operations and Catalyst optimization.

2. What are the challenges you face in spark?

**Answer**: Challenges include handling skewed data, optimizing job performance, managing resource allocation, tuning for memory usage, and ensuring fault tolerance and scalability.

3. What is difference between reduceByKey & groupByKey?

**Answer**: reduceByKey combines values for each key using a function, aggregating data locally before shuffling, optimizing performance. groupByKey groups data without aggregation, potentially causing excessive data movement and memory consumption.

4. What is the difference between Persist and Cache?

**Answer**: Both persist RDDs/DataFrames in memory, but cache() is a shorthand for persist() with default storage level MEMORY_ONLY. persist() allows specifying storage levels like MEMORY_AND_DISK for durability or MEMORY_ONLY_SER for serialized storage.

5. What is the Advantage of a Parquet File?

**Answer**: Parquet offers efficient columnar storage, reducing storage space and improving read/write performance. It supports complex nested data structures, predicate pushdown for efficient query execution, and integration with various data processing frameworks.

6. What is a Broadcast Join ?

**Answer**: Broadcasts smaller DataFrame/RDD to each node, reducing data movement during join operations. Ideal for smaller datasets or when one dataset is significantly smaller than others, optimizing performance by minimizing network traffic.

7. What is Difference between Coalesce and Repartition?

**Answer**: Both adjust the number of partitions, but coalesce() minimizes shuffling and avoids full data movement, useful for reducing partitions. repartition() involves full shuffle and can increase or decrease partitions, ensuring data redistribution.

8. What are the roles and responsibility of driver in spark Architecture?

**Answer**: The driver coordinates the execution of Spark jobs, communicates with the cluster manager to acquire resources, splits tasks into stages, and manages the execution of tasks on worker nodes, handling task scheduling, fault recovery, and job monitoring.

9. What is meant by Data Skewness? How is it deal?

**Answer**: Data skewness refers to uneven distribution of data across partitions, slowing down processing. Techniques like data pre-processing (e.g., salting), custom partitioning strategies, or using repartition() can alleviate skew by balancing workload across nodes.

10. What are the optimisation techniques used in Spark?

**Answer**: Techniques include choosing appropriate transformations/actions, partitioning data effectively, caching/persisting intermediate results, using broadcast variables for small data, tuning memory and parallelism settings (spark-defaults.conf), and optimizing join strategies.

11. What is Difference Between Map and FlatMap?

**Answer**: map() transforms each element of an RDD/DataFrame independently and returns one output for each input. flatMap() maps each input element to zero or more output elements, useful for operations like tokenization or exploding arrays.

12. What are accumulator and BroadCast Variables?

**Answer**: Accumulators aggregate values across tasks, typically used for counters or sums in a distributed manner. Broadcast variables efficiently distribute read-only data to worker nodes, cached for reuse in operations like joins.

13. What is a OOM Issue, how to deal it?

**Answer**: OOM (Out of Memory) occurs when Spark runs out of memory due to large datasets or inefficient operations. Solutions include optimizing memory settings (spark.executor.memory), caching/persisting data, using efficient transformations, or scaling resources based on workload.

14. what are tranformation in spark? Type of Transformation?

**Answer**: Transformations modify RDDs/DataFrames to build a sequence of instructions for execution. Types include map, flatMap, filter (narrow transformations), groupBy, join (wide transformations), and sort, each defining how data is processed or combined.

15. Tell me some action in spark that you used ?

**Answer**: Common actions like show, collect, count, save, and reduce trigger execution and return results to the driver. These actions perform computations on RDDs/DataFrames and provide outcomes or write data to external storage.

16. What is the role of Catalyst Optimizer ?

**Answer**: Catalyst Optimizer optimizes Spark SQL queries by generating an optimized logical and physical execution plan. It leverages cost-based optimization, rule-based transformations, and code generation to improve query performance by minimizing data movement and computation.

17. what is the checkpointing?

**Answer**: Checkpointing saves RDD/DataFrame to disk to cut its lineage, reducing memory usage and recomputation in case of failures. It improves fault tolerance and performance for iterative algorithms or long lineage RDDs by creating a reliable storage checkpoint.

18. Cache and persist

**Answer**: Both store RDDs/DataFrames in memory/disk for fast access but differ in flexibility. cache() uses default MEMORY_ONLY storage level, while persist() allows setting storage levels like MEMORY_AND_DISK for durability or MEMORY_ONLY_SER for serialization, adapting to specific needs.

19. What do you understand by Lazy Evaluation?

**Answer**: Spark evaluates transformations only when an action requires a result. This deferred execution optimizes performance by optimizing job execution, minimizing data movement, and allowing Spark to optimize the entire workflow before actual computation starts.

20. How to convert Rdd to Dataframe?

**Answer**: Convert an RDD to DataFrame using toDF() method on the RDD, specifying column names. Example:
```python
rdd = sc.parallelize([(1, 'Alice'), (2, 'Bob')])
df = rdd.toDF(['id', 'name'])
```

20. How to Dataframe to Dataset.

**Answer**:

18. What makes Spark better than Hadoop?

**Answer**:

19. How can you read a CSV file without using an external schema?
20. What is the difference between Narrow Transformation and Wide Transformation?
21. What are the different parameters that can be passed while Spark-submit?
22. What are Global Temp View and Temp View?
23. How can you add two new columns to a Data frame with some calculated values?
24. Avro Vs ORC, which one do you prefer?
25. What are the different types of joins in Spark?
26. Can you explain Anti join and Semi join?
27. What is the difference between Order By, Sort By, and Cluster By?
28. Data Frame vs Dataset in spark?
29. What are the join strategies in Spark
30. What happens in Cluster deployment mode and Client deployment mode
31. What are the parameters you have used in spark-submit
32. How do you add a new column in Spark
33. How do you drop a column in Spark
34. What is difference between map and flatmap?
35. What is skew partitions?
36. What is DAG and Lineage in Spark?
37. What is the difference between RDD and Dataframe?
38. Where we can find the spark application logs.
39. What is the difference between reduceByKey and groupByKey?
40. what is spark optimization?
41. What are shared variables in spark
42. What is a broadcast variable
43. Why spark instead of Hive
44. what is cache
45. Tell me the steps to read a file in spark
46. How do you handle 10 GB file in spark, how do you optimize it?


---

## **Important SQL questions**


1. Find out nth Order/Salary from the tables.
2. Find the no of output records in each join from given Table 1 & Table 2
3. YOY,MOM Growth related questions.
4. Find out Employee ,Manager Hierarchy (Self join related question) or
Employees who are earning more than managers.
5. RANK,DENSERANK related questions
6. Some row level scanning medium to complex questions using CTE or recursive CTE, like (Missing no /Missing Item from the list etc.)
7. No of matches played by every team or Source to Destination flight combination using CROSS JOIN.
8. Use window functions to perform advanced analytical tasks, such as calculating moving averages or detecting outliers.
9. Implement logic to handle hierarchical data, such as finding all descendants of a given node in a tree structure.
10. Identify and remove duplicate records from a table.

---

## **Important Python questions**


1. Reversing a String using an Extended Slicing techniques.
2. Count Vowels from Given words.
3. Find the highest occurrences of each word from string and sort them in order.
4. Remove Duplicates from List.
5. Sort a List without using Sort keyword.
6. Find the pair of numbers in this list whose sum is n no.
7. Find the max and min no in the list without using inbuilt functions.
8. Calculate the Intersection of Two Lists without using Built-in Functions
9. Write Python code to make API requests to a public
API (e.g., weather API) and process the JSON response.
10. Implement a function to fetch data from a database table, perform data manipulation, and update the database.


---

## **Top 10 advanced SQL interview questions**

1. Write a query using a Common Table Expression
(CTE) to achieve a complex data transformation.
1. Explain the concept of window functions and provide an example using RANK or LAG.
1. Optimize a slow-running query by identifying appropriate indexes.
1. Write a stored procedure that takes parameters and performs specific data manipulation tasks.
1. Explain the concept of database normalization and its benefits for data integrity.
1. Write a query that finds duplicate rows in a table based on specific columns.
1. Utilize temporary tables to perform multi-step data transformations within a single query.
1. Write a query that joins multiple tables with complex relationships (e.g., self-joins).
1. Explain the differences between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN with examples.
1. Write a query that aggregates data based on hierarchical relationships between records.
