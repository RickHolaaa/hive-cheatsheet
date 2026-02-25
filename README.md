# 📘 Hive & HQL Cheatsheet

<div style="display: flex; align-items: center; gap: 20px; padding: 20px; justify-content: center;">
<img src="https://tse1.mm.bing.net/th/id/OIP.zlwD91Wpiuyn5sY4iUzeYwHaFj?rs=1&pid=ImgDetMain&o=7&rm=3" style="width: 50px">
<img src="https://logodix.com/logo/981909.png" style="width: 50px">
<img src="https://creazilla-store.fra1.digitaloceanspaces.com/vectors/7917955/apache-sqoop-logo-vector-md.jpeg" style="width: 130px">
<img src="https://tse2.mm.bing.net/th/id/OIP.GNzSNJ5OzXDAhTgEg58mHAAAAA?rs=1&pid=ImgDetMain&o=7&rm=3" style="width: 130px">
<img src="https://www.svgrepo.com/show/184143/java.svg" style="width: 45px">
<img src="https://tse4.mm.bing.net/th/id/OIP.TLvPDXYJYSicUFYhoeAY1QHaHa?rs=1&pid=ImgDetMain&o=7&rm=3" style="width: 45px">

</div>

This repository contains all the information you need to know to master Hive and HQL.

## 🧭 Introduction & Context

### Hadoop Overview

<div style="display: flex; align-items: center; gap: 20px;">
<div>

| Component | Description |
|----------|-------------|
| **Hadoop** | Open‑source framework for distributed Big Data processing/storage. |
| **MapReduce** | Parallel programming model for structured, semi-/unstructured data. |
| **HDFS** | Fault‑tolerant distributed file system on commodity hardware. |

</div>

<img src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/hadoop-ecosystem-projects-architecture.png" style="width: 500px">

</div>

### MapReduce Approaches

<div style="display: flex; align-items: center; gap: 20px;">
<div>

| Approach | Description |
|---------|-------------|
| **Java MapReduce** | Traditional low‑level processing for all data types. |
| **Pig** | Procedural scripting for structured/semi‑structured data. |
| **Hive/HQL** | SQL‑like queries for structured data. |

</div>

<img src="https://i.ytimg.com/vi/cHGaQz0E7AU/maxresdefault.jpg" style="width: 500px">

</div>

### Hadoop Ecosystem
| Tool | Purpose |
|------|---------|
| **Sqoop** | Import/export data between HDFS and RDBMS. |
| **Pig** | Script-based transformations (MapReduce abstraction). |
| **Hive** | SQL-style analytics on Hadoop (HQL). |

## 🐝 Hive Overview
| Category | Details |
|----------|---------|
| Purpose | Data warehouse infrastructure for structured data. |
| Designed for | Analytics, ETL, batch processing, Big Data queries. |
| Not for | OLTP, real-time queries, row-level operations. |
| Features | Schema in metastore, HDFS storage, SQL-like HQL, scalable & extensible. |

## 🏗️ Commands
### Database Commands
| Action | Syntax |
|--------|--------|
| Create DB | `CREATE DATABASE [IF NOT EXISTS] db;` |
| Drop DB | `DROP DATABASE [IF EXISTS] db [CASCADE];` |
| Describe DB | `DESCRIBE DATABASE [EXTENDED] db;` |
| Show DBs | `SHOW DATABASES;` |
| Use DB | `USE db;` |

---

### Table Commands
| Action | Syntax |
|--------|--------|
| Create basic table | `CREATE TABLE t (id INT, name STRING);` |
| Create external table | `CREATE EXTERNAL TABLE t (...) LOCATION '/path';` |
| SerDe table | `ROW FORMAT DELIMITED ... STORED AS TEXTFILE;` |
| ORC/Parquet | `STORED AS ORC;` |
| Copy structure | `CREATE TABLE t2 LIKE t1;` |
| Describe table | `DESCRIBE [FORMATTED] t;` |
| Drop | `DROP TABLE t;` |
| Truncate | `TRUNCATE TABLE t;` |
| Rename | `ALTER TABLE t1 RENAME TO t2;` |
| Add columns | `ALTER TABLE t ADD COLUMNS (...);` |
| Replace columns | `ALTER TABLE t REPLACE COLUMNS (...);` |
| Change location | `ALTER TABLE t SET LOCATION 'hdfs://path';` |

---

### Loading & Inserting Data
| Action | Syntax |
|--------|--------|
| Load from HDFS | `LOAD DATA INPATH '/path' INTO TABLE t;` |
| Load from local | `LOAD DATA LOCAL INPATH '/file' INTO TABLE t;` |
| Insert row | `INSERT INTO t VALUES (...);` |
| Insert‑select | `INSERT INTO t SELECT * FROM t2;` |
| Insert overwrite | `INSERT OVERWRITE TABLE t SELECT ...;` |

---

### Querying Data
| Feature | Syntax |
|---------|--------|
| Select | `SELECT col FROM t;` |
| Filter | `WHERE col > 10` |
| Group By | `GROUP BY dept` |
| Having | `HAVING SUM(col) > ...` |
| Order By | `ORDER BY col` |
| Sort By | `SORT BY col` |
| Distribute By | `DISTRIBUTE BY col` |
| Cluster By | `CLUSTER BY col` |

---

### Joins

<div style="display: flex; align-items: center; gap: 20px;">
<div>

| Join Type | Syntax |
|-----------|--------|
| Inner | `JOIN` |
| Left | `LEFT JOIN` |
| Right | `RIGHT JOIN` |
| Full | `FULL OUTER JOIN` |
| Cross | `CROSS JOIN` |

</div>

<img src="https://www.kevsrobots.com/learn/sqlite3/assets/join_types.jpg" style="width: 400px;">

</div>

---

### Functions
#### String
`LOWER(), UPPER(), LENGTH(), CONCAT(), SUBSTR(), TRIM(), SPLIT(), REGEXP_REPLACE()`

#### Math
`ABS(), POWER(), CEIL(), FLOOR(), ROUND(), RAND(), SQRT()`

#### Date
`CURRENT_DATE(), CURRENT_TIMESTAMP(), YEAR(), MONTH(), DAY(), HOUR(), DATEDIFF(), ADD_MONTHS()`

#### Conditional
`IF(EXP1, EXP2, EXP3), CASE WHEN ... THEN ... END`

#### Aggregate
`COUNT(), SUM(), AVG(), MAX(), MIN()`

---

### Partitioning & Bucketing
| Feature | Syntax |
|---------|--------|
| Static partition | `INSERT INTO t PARTITION (year=2025) SELECT ...;` |
| Enable dynamic | `SET hive.exec.dynamic.partition=true;` |
| Dynamic partition | `INSERT INTO t PARTITION(year) SELECT ...;` |
| Bucketing | `CLUSTERED BY(id) INTO 8 BUCKETS;` |

---

### ACID Transactions
| Action | Syntax |
|--------|--------|
| Enable ACID | `SET hive.txn.manager=...DbTxnManager;` |
| Insert | `INSERT INTO t VALUES (...);` |
| Update | `UPDATE t SET ... WHERE ...;` |
| Delete | `DELETE FROM t WHERE ...;` |
| Merge | `MERGE INTO t USING s ON ... WHEN MATCHED ...;` |

---

### Administrative Commands
| Action | Syntax |
|--------|--------|
| Show tables | `SHOW TABLES;` |
| Show functions | `SHOW FUNCTIONS;` |
| Explain plan | `EXPLAIN SELECT ...;` |
| Set config | `SET hive.execution.engine=tez;` |

---

### Views & Materialized Views
| Type | Syntax |
|------|--------|
| View | `CREATE VIEW v AS SELECT ...;` |
| Materialized View | `CREATE MATERIALIZED VIEW mv AS SELECT ...;` |

## 📝 Definitions
| Term | Definition | Concrete Explanation | Example |
|------|------------|----------------------|---------|
| **External Table** | Table where Hive stores only metadata; data remains in external storage. | Dropping the table deletes only the schema, not the files. Useful when data is shared with other systems (Spark, Presto, etc.). | `CREATE EXTERNAL TABLE logs(...) LOCATION '/data/logs/';` |
| **SerDe** | Serializer/Deserializer for custom input/output formats. | Allows Hive to read/write data that isn’t plain text (e.g., JSON, CSV, Avro). Hive uses the SerDe to interpret each line. | `ROW FORMAT SERDE 'org.apache.hive.hcatalog.data.JsonSerDe'` |
| **ORC** | Columnar storage format optimized for Hive. | Provides fast reads, compression, indexing, predicate pushdown, and ACID support. Best for Hive performance. | `STORED AS ORC` |
| **Parquet** | Columnar file format used across multiple engines. | Highly efficient for analytics; supports nested structures and is interoperable with Spark, Hive, Presto, etc. | `STORED AS PARQUET` |
| **Truncate** | Deletes all rows without removing the schema. | Faster than DELETE because it drops data files directly. Cannot be used on transactional tables without special flags. | `TRUNCATE TABLE employees;` |
| **DISTRIBUTE BY** | Sends rows to reducers using hash partitioning. | Ensures rows with the same key go to the same reducer but doesn’t sort them. Useful for parallelized grouping. | `SELECT * FROM sales DISTRIBUTE BY region;` |
| **CLUSTER BY** | Combines DISTRIBUTE BY and SORT BY. | Rows are both partitioned by key and sorted within each reducer. Optimized for sorting pipelines. | `SELECT * FROM sales CLUSTER BY region;` |
| **Static Partition** | Partition values specified manually. | Good when you already know partition values (e.g., daily batch loads). | `INSERT INTO t PARTITION(year=2025) SELECT ...;` |
| **Dynamic Partition** | Hive derives partition values at runtime. | Allows automatic creation of many partitions in one insert statement; must enable dynamic mode first. | `INSERT INTO t PARTITION(year) SELECT ..., year FROM src;` |
| **Bucketing** | Divides data into fixed buckets based on a hash function. | Improves join performance and enables efficient sampling. Buckets required for ACID tables. | `CLUSTERED BY(id) INTO 8 BUCKETS` |
| **ACID** | Hive’s transaction framework (INSERT, UPDATE, DELETE, MERGE). | Requires ORC + bucketing + transactional properties. Enables row-level operations similar to RDBMS systems. | `TBLPROPERTIES ('transactional'='true')` |
| **MERGE** | Performs insert/update/delete in one operation. | Ideal for Slowly Changing Dimensions (SCD). Automatically updates matches and inserts non-matches. | `MERGE INTO t USING s ON t.id=s.id ...` |
| **Explain Plan** | Shows the execution plan for a query. | Useful for debugging, performance tuning, and understanding MapReduce/Tez/Spark tasks. | `EXPLAIN SELECT * FROM t;` |
| **Set Config** | Changes session properties or execution settings. | Used to switch execution engine, set partitioning/bucketing modes, enable ACID, etc. | `SET hive.execution.engine=tez;` |
| **View** | Virtual table created from a query. | Doesn’t store data; acts as a saved SQL query for reusability and abstraction. | `CREATE VIEW v AS SELECT ...;` |
| **Materialized View** | View whose results are physically stored. | Speeds up repetitive analytical queries; Hive can rewrite queries to use the MV transparently. | `CREATE MATERIALIZED VIEW mv AS SELECT ...;` |

## 📖 Glossary
| Term | Meaning |
|------|---------|
| **ACID** | Hive’s transaction framework supporting INSERT, UPDATE, DELETE, and MERGE on transactional tables. |
| **Bucketing** | Dividing data into fixed “buckets” using a hash function to optimize joins and sampling. |
| **CLUSTER BY** | Combines `DISTRIBUTE BY` and `SORT BY`; partitions and sorts data within reducers. |
| **Dynamic Partition** | Hive automatically determines partition values from incoming data during insertion. |
| **DISTRIBUTE BY** | Hash-based distribution of rows across reducers without guaranteeing order. |
| **EXPLAIN** | Displays the detailed execution plan of a Hive query. |
| **External Table** | A Hive table where only metadata is managed by Hive; data remains external (HDFS/S3). Dropping the table does not delete underlying data. |
| **HDFS** | Hadoop Distributed File System; the distributed, fault-tolerant storage layer used by Hadoop and Hive. |
| **HQL** | Hive Query Language — SQL-like language used to query and manage Hive data. |
| **Internal Table** | Hive-managed table; dropping it deletes both metadata and data from HDFS. |
| **MapReduce** | Parallel processing framework used for distributed computation over large datasets. |
| **Materialized View** | A view with physically stored content to speed up analytical queries. |
| **MERGE** | SQL statement combining insert, update, and delete operations in one command (SCD support). |
| **Metastore** | Hive’s metadata storage component (schemas, partitions, statistics). |
| **OLAP** | Online Analytical Processing — analytical queries, reporting, batch workloads (Hive is OLAP‑oriented). |
| **OLTP** | Online Transaction Processing — real-time transactional workloads (Hive is NOT designed for OLTP). |
| **ORC** | Optimized Row Columnar — high-performance columnar storage format for Hive with compression & ACID support. |
| **Parquet** | Columnar storage format used across Hadoop ecosystem (Spark, Hive, Presto). |
| **Partition** | Directory-level segmentation of table data based on column values (e.g., `year=2025/month=01`). |
| **Predicate Pushdown** | Optimization where filters are applied directly at file format level (ORC, Parquet) to reduce data read. |
| **RDBMS** | Relational Database Management System — traditional SQL databases like MySQL, PostgreSQL, Oracle, SQL Server; typically used as **sources** or **targets** for Hive via Sqoop. |
| **Schema-on-Read** | Data is parsed and structured at query time, not during ingestion. |
| **SerDe** | Serializer/Deserializer allowing Hive to read/write various data formats (CSV, JSON, Avro). |
| **SET** | Used to configure Hive session-level or engine-level settings. |
| **Spark** | In-memory distributed processing engine; can serve as a Hive execution engine. |
| **Static Partition** | Partition value manually provided during insertion. |
| **Tez** | DAG-based execution engine faster than MapReduce; often used as Hive’s execution backend. |
| **Textfile** | Default Hive storage format (plain text, no columnar optimizations). |
| **UDF** | User-Defined Function — custom functions extending Hive SQL capabilities. |
| **UDAF** | User-Defined Aggregate Function — custom aggregate operations (e.g., custom SUM or MEDIAN). |
| **UDTF** | User-Defined Table Function — returns multiple rows/columns (e.g., similar to explode). |
| **View** | Virtual table storing only the SQL query; does not physically store data. |
| **Warehouse Directory** | Default HDFS directory where Hive stores managed table data. |

## 📚 References
https://yourdevkit.com/cheat-sheet/apache-hive

https://hive.apache.org/docs/latest/