## <span class="mysql-color">Sec 1</span>

- Presentan las operaciones ya creadas al desarrollador.
- Paquete de datos grande (XML)
- Las llamadas van por POST
- Puede ser Sin-estado o Con-estado
- Se basa en una WSDL (Web Service Definition Languge)

---

## <span class="mysql-color">Sec 2</span>

1. Overview of Couchbase Server 4.5 Architecture and capabilities
2. Core use cases for Couchbase
3. Hardware sizing guidelines for different workloads
4. Installation and best practices guidelines for configuring Couchbase
5. How to perform a upgrade of Couchbase in a production environment
6. vBuckets
7. Storage Engine: Caching layer, Disk persistence and Network replication
8. Server warmup
9. Replicas and intra-cluster Replication: How Couchbase deals with consistency resolution
10. Configuring a client application to use a Couchbase cluster
11. How a client determines which Couchbase node to contact for I/O
12. Creating a new Bucket and adding data to it
13. How deletes are handled asynchronously: Tombstones and Compaction
14. Ejection, Eviction and Working Set Management
15. Rebalancing a cluster after adding or removing nodes
16. Views and Indexing
17. Managing Rack Awareness
18. Admin tasks: increase or reduce cluster size, handle a failover situation, etc.
19. Benchmarking and monitoring a live cluster
20. Cross Datacenter Replication and conflict resolution strategies
21. Backing up and Restoring a cluster
22. Tips and tricks for troubleshooting a Couchbase cluster
23. Using the Web Console to administer and monitor Couchbase
24. Using the Command-line toolkit to administer Couchbase

---

## <span class="mysql-color">Sec 3</span>

1. Welcome (4 hands-on labs)
 - Welcome to our course
 - Who's all here?
 - What are the logistics?
 - What will this course cover?
 - What do we assume you are familiar with?

2. Couchbase Server (1 hands-on lab)
 - How do customers use Couchbase?
 - What does Couchbase provide?
 - Where would Couchbase fit into an enterprise app?
 - How are analytical and operational uses different?
 - Where did we come from, and where are we going?
 - What is the project history?
 - What are the main architectural structures?
 - How is a node organized?
 - What is the high-level architecture?
 - What does the Cluster Manager provide?
 - What does the Data Manager provide?
 - How can services be scaled across a cluster?
 - What is multi-dimensional scalability (MDS)?
 - How does Couchbase provide these capabilities?
 - How is a cluster administered?
 - What do you configure in the setup wizard?
 - What administrative interfaces are available?
 - Once you're installed, where should you look?
 - Document browser in web console
 - How do you find/edit documents in the console?
 - Command-Line Interface (CLI) Tools
 - What administrative interfaces are available?
 - What command line tools are available?
 - How do you bulk load documents into a bucket?
 - What desktop tools work with N1QL?

3. Storing Data in Couchbase (4 hands-on labs)
 - How does Couchbase organize data?
 - What are the main architectural structures?
 - How does Couchbase organize data?
 - What is JSON?
 - Structured vs. unstructured data
 - What is JavaScript Object Notation?
 - Want to see a few examples?
 - Why does Couchbase focus on JSON?
 - Why store data as JSON?
 - How do NOSQL and relational approaches compare?
 - Static vs. flexible data models
 - Structured vs. unstructured data
 - How do data modeling approaches compare?
 - Normalization vs. de-normalization
 - How do data modeling approaches compare?
 - What's wrong with over-normalization?
 - What are key strengths of each approach?
 - Are Couchbase buckets like a table? A database?
 - How do we access the data?
 - How do you get documents from Couchbase?
 - Whole-document access
 - Subdocument API
 - How do we write applications?
 - For what languages are SDKs supported?
 - Show me some code...
 - What are the common APIs?
 - How is N1QL used by developers?
 - How about community support?
 - What is the scope of transactions?
 - How may atomicity affect modeling?
 - How does optimistic locking with CAS behave?
 - Can consistency be maintained?

4. N1QL (2 hands-on labs)
 - N1QL is like SQL
 - How do you query the data?
 - What information comes back with results?
 - How do you select documents by key, in N1QL?
 - How do you query for a document key?
 - How do you alias a bucket?
 - How do you filter for a specific value?
 - How could you efficiently select a range?
 - How do you filter text with wildcards?
 - Aggregating and ORDERing
 - How do you count documents or attributes?
 - How do you sequence results?
 - How do you select unique values?
 - How do you aggregate values?
 - Operators and Functions
 - What operators are available?
 - What functions are available in N1QL?
 - Primary Index
 - Indexes: Primary Indexes
 - Secondary Indexes
 - How do you create a full secondary index?
 - How do you utilize a full secondary index?
 - How do you partially index the documents?
 - How do you utilize a filtered index?
 - EXPLAINing the data access plan
 - How do you determine if an index is in use?
 - Executions Plans & Explain
 - Main Operations
 - Index Hinting
 - Minimize Items Scanned
 - System Namespace
 - How do you determine indexes via N1QL?
 - How do you determine buckets via N1QL?
 - Indexes: Secondary Indexes
 - Query Workbench
 - What desktop tools work with N1QL?
 - Query Workbench
 - Features of the Query Workbench
 - N1QL Editor
 - Bucket Analysis
 - Results
 - JSON Result Format
 - Table Result Format
 - Tree/List Result Format

5. Index Engines (7 hands-on labs)
 - Overview
 - Indexing Architecture and Indexers
 - MapReduce View Indexer
 - Spatial View Indexer
 - GSI Indexer
 - Distributed Secondary Indexes (DSI = View)
 - Indexing - DSI - Scatter/Gather
 - Global Secondary Indexes (GSI)
 - Query and Index with GSI
 - What are Global Secondary Indexes?
 - Power of GSI
 - Distribution in GSI (Range Partitioning)
 - Latency in GSI
 - GSI and Scalability
 - Load-balancing in GSI
 - GSI and Replication
 - Which to choose - GSI vs Views
 - Index Service - Capacity Management
 - Memory-Optimized Global Indexes
 - Enabling Memory-Optimized Global Indexes on the Cluster

6. N1QL is NOSQL (7 hands-on labs)
 - JSON extensions to SQL, or "SQL for Documents"
 - What is JavaScript Object Notation?
 - How do you select nested attributes?
 - How do you respond to missing data?
 - What is a "collection" in a JSON document?
 - How do you select for a value in an array?
 - How do you select for a value in an object array?
 - Array Indexing
 - Data Manipulation Language (DML)
 - DML Statements
 - DELETE
 - INSERT
 - UPDATE
 - INSERT vs. UPSERT
 - JOIN
 - How do you join a single document?
 - How do you join document sets from a key array?
 - NEST
 - NEST vs. JOIN
 - UNNEST Clause
 - How do you UNNEST an embedded collection?
 - Flexible Commutative JOIN in N1QL

7. Introduction to Modeling (6 hands-on labs)
 - What is Data Modeling?
 - Logical Data Modeling
 - Example: Logical Data Modeling
 - Physical Data Modeling
 - Data models used in this course
 - What data models are used in the course?
 -  - How is Couchmusic1 shaped?
 - How is Couchmusic2 shaped?
 - How is Couchmusic3 shaped?

8. Query Engine (2 hands-on labs)
 - N1QL empowers, beyond other NOSQL engines
 - Query Architecture
 - How do you get documents from Couchbase?
 - Couchbase Server Cluster Architecture
 - How does Couchbase provide these capabilities
 - Architecture Highlights
 - Query Execution
 - How is a N1QL query processed?
 - Query Execution
 - How does the query execute?
 - Client to Query Service: REST API
 - The Parse Phase
 - Query Execution: Plan
 - Query Execution: Scan Phase
 - Query Execution: Fetch
 - Query Execution: Join
 - Query Execution: Filter
 - Query Execution: Aggregate, Sort, Offset, Limit
 - Query Execution: Project
 - Intersect Scan
 - IntersectScan (Multi-Index Scan)
 - IntersectScan
 - Index Covering
 - Phases of Query Execution - (Without Index Covering)
 - N1QL Query Execution Flow: Index Covering
 - Phases of Query Execution - (With Index Covering)
 - Index Covering
 - Querying data with N1QL
 - More Index Covering
 - Scaling
 - Query Execution
 - Query Service - Capacity Management

9. More Modeling (1 hands-on lab)
 - Data Modeling in a JSON and NOSQL context
 - What choices impact JSON document design?
 - What factors may influence structural choices?
 - Modeling entities in JSON
 - What is an "entity"?
 - How can entities be described in JSON?
 - Is a UserProfile one entity? Or, more than one?
 - Is a Country an entity?
 - Is an Address an entity?
 - Is a Phone an entity?
 - Modeling relationships in JSON
 - How can relationships be expressed in JSON?
 - When might you nest a related entity?
 - When might you nest an array of related entities?
 - When might you embed a foreign document key?
 - Making choices in JSON document design
 - How may the root attribute be used?
 - Are attributes best expressed as objects or arrays?
 - Should array values be simple or complex?
 - What options do you have for timestamps?
 - What choices can be made about attribute names?
 - How does N1QL distinguish empty, null, missing?
 - Making choices in JSON key design
 - What is a natural key?
 - What is a surrogate key?
 - Common Patterns
 - How may key patterns be useful?
 - What is the Lookup Key document pattern?
 - Is this traditional, widely-used pattern still needed?
 - Can consistency be maintained?

10. Tuning (2 hands-on labs)
 - Fundamentals
 - Minimize Items Scanned
 - Monitoring
 - How do you determine indexes in the console?
 - Monitoring GSI Indexes

11. Migrating from SQL to N1QL (no labs)
 - Motivation for Migration
 - Motivation for Migration to Couchbase
 - How to Migrate to Couchbase?
 - Motivation for Migration to Couchbase
 - Data Model
 - Data Model: Map RDBMS to Couchbase
 - Map Tables to Buckets: Normalized Data
 - Map Database(s) to Buckets: Normalized Data
 - Map Database(s) to Buckets: Normalized Data
 - Map Database(s) to Buckets: Denormalized Data
 - Datatypes
 - Data Types Mapping
 - MISSING in JSON
 - Queries
 - Operators: Searching in JSON (Non-Existing Fields)
 - JOINs
 - JOINs: Output of JOIN - NESTed Data
 - NEST: Create NESTed JSON
 - UNNEST: Remove NESTing From JSON
 - USE KEYS: Improving Efficiency
 - Functions: Comparing DateTime Fields and Values
 - DML
 - CRUD Operations: INSERT/UPSERT
 - CRUD Operations: UPDATE/DELETE
 - What have you learned?

 ---

## <span class="mysql-color">Sec 4</span>

## Optional Appendices (reviewed based on available time and interest)

A. More Features (no labs)
 - How is Couchbase optimized for mobile development?
 - Why is mobile data synchronization critical?
 - How does Couchbase solve this problem?
 - Full-Text Search
 - Full text search
 - Full text search - Couchbase CBFT
 - Full-Text Search
 - How does Couchbase Enterprise Edition secure your data?
 - How is administrative data secured in motion?
 - How is client data secured in motion?
 - How is client data secured at rest?
 - How is administrative activity audited?
 - What external systems integrate with Couchbase?
 - Apache Hadoop
 - Apache Spark
 - ODBC/JDBC drivers
 - Full text search
 - Spring developer framework
 - Talend platform
 - Unity mobile
 - Many, many more open source integrations

B. Aggregations With Views (no labs)
 - Query Data in Couchbase
 - Retrieving Data with Document Key
 - Querying Data using View Queries
 - Query Consistency with Views
    - stale=ok
    - stale=update_after
    - stale=false
 - Querying geographic data with spatial views
 - Querying data with N1QL
 - Components of N1QL Query Engine
 - GSI vs. Views
 - Global Secondary Indexes vs. Views
 - GSI and Views Differences: Partitioning Model
 - GSI and Views Differences: Scaling Model
 - GSI and Views Differences: Performance
 - GSI and Views Differences: Managed Cache and Storage
 - GSI and Views Differences: High Availability
 - Indexing And Querying via Views
 - Components of N1QL Query Engine
 - Indexing and Querying via Views
 - Best Practices - Selection, Projection, Aggregation
 - Database Design Considerations for Views
 - Number of Design Documents per Bucket
 - Separated Buckets for Indexing/Querying
 - XDCR - Separate Cluster for Indexing
 - Configuration Settings and their Effects on Views
 - Indexing Settings
 - Rebalance Settings
 - Compaction Settings
