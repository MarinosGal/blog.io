# Big Data Storage/Retention Technologies

*In this repository I have gathered all (until early 2018) the big data storage and retention technologies, in order to 
give a brief, but yet informative, presentation of each technology.*

### HDFS: Distributed File System for Hadoop

A Java-based filesystem that provides scalable and reliable data storage. Designed to span large clusters of commodity servers.
Master-Slaves Architecture (NameNode-DataNodes). NameNode manages the directory tree and regulates access to files by clients. 
DataNodes store the data. Files are split into blocks of the same size and these blocks are stored and replicated in a set of 
DataNodes. [1] HDFS is highly fault-tolerant and is designed to be deployed on low-cost hardware. HDFS provides high throughput
access to application data and is suitable for applications that have large data sets. HDFS relaxes a few POSIX requirements 
to enable streaming access to file system data. [2]

### Apache Hive

Apache Hive is an open-source data warehouse system for querying and analyzing large datasets stored in Hadoop files using SQL.
Abstraction layer on top of MapReduce. SQL-like language called HiveQL. Metastore is the central repository of hive metadata. 
[3] Structure can be projected onto data already in storage. A command line tool and JDBC driver are provided to connect users 
to Hive. [4]

### Apache Kudu

Apache KUDU is an innovative new storage engine that is designed from the ground up to overcome the limitations of various 
storage systems available today in the Hadoop ecosystem. For the first time, Kudu enables the use of the same storage engine 
for large scale batch jobs and complex data processing jobs that require fast random access and updates. As a result, 
applications that require both batch as well as real-time data processing capabilities can use Kudu for both types of 
workloads. With Kudu’s ability to handle atomic updates, you no longer need to worry about boundary conditions relating to 
late-arriving or out-of-sequence data. In fact, data with inconsistencies can be fixed in place in almost real time, without 
wasting time deleting or refreshing large datasets. Having one system of record that is capable of handling fast data for 
both analytics and real-time workloads greatly simplifies application design and implementation. [5] Kudu provides a 
combination of fast inserts/updates and efficient columnar scans to enable multiple real-time analytic workloads across a 
single storage layer. Kudu is specifically designed for use cases that require fast analytics on fast (rapidly changing) data.
Engineered to take advantage of next-generation hardware and in-memory processing, Kudu lowers query latency significantly 
for Apache Impala (incubating) and Apache Spark (initially, with other execution engines to come). [6]

### Apache HBase

Apache HBase is an open-source, non-relational, distributed column-oriented database written in Java. Modeled after Google’s 
BigTable and developed as part of Apache Hadoop project, it runs on top of HDFS. Random, real-time read/write access to the 
data. Very light schema, Rows are stored in sorted order. [7] Use Apache HBase when you need random, realtime read/write 
access to your Big Data. [8]

### MapR DB

MapR DB is an enterprise-grade, high performance, in-Hadoop No-SQL database management system, MapR is used to add real-time 
operational analytics capabilities to Hadoop. [9] You can run MapR-DB in the same cluster as Apache™ Hadoop® and Apache Spark,
letting you immediately analyze or process live, interactive data. You can eliminate data silos to speed the data-to-action 
cycle, while also enabling a more efficient data architecture. [10]

### Pivotal HDB

Hadoop native SQL Database powered by Apache HAWQ [12] is the Apache Hadoop native SQL database for data science and machine 
learning workloads. With Pivotal HDB, you can ask more questions of your data in Hadoop more often to gain deeper, actionable 
insights. You no longer need to sample data or move it to another platform to perform advanced analytics. [13]

### Apache Hawq

Apache Hadoop native SQL. Advanced, MPP, elastic query engine and analytic database for enterprises. It combines exceptional 
MPP-based analytics performance, robust ANSI SQL compliance, Hadoop ecosystem integration and manageability, and flexible 
data-store format support. All natively in Hadoop. No connectors required. [14]

### Apasche Impala

Apache Impala is an open-source MPP analytic database built to work with data stored on open, shared data platforms like 
Apache Hadoop’s HDFS filesystem, Apache Kudu’s columnar storage and object stores like S3. By being able to query data from 
multiple sources stored in different, open formats like Apache Parquet, Apache Avro and text, Impala decouples data and 
compute and lets users query data without having to move/load data specifically into Impala clusters. In the cloud, this 
capability is especially useful as you can create transient clusters with Impala to run your reports/analytics and shut down 
the cluster when you are done or elastically scale compute power to support peak demands, letting you save on cluster-hosting 
costs. [15]

### Apache Parquet

Apache Parquet is a columnar storage format available to any project in the Hadoop ecosystem, regardless of the choice of 
data processing framework, data model or programming language. [16]

### Apache Avro

Apache Avro is a data serialization system that provides rich data structures, compact fast binary data format and a 
container file to store persistent data. [17]

### MemSQL

MemSQL unveiled its Spark Streamliner initiative, in which it incorporated Apache Spark Streaming as a middleware component 
to buffer the parallel flow of data coming from Kafka before it’s loaded into MemSQL’s consistent storage. This enables 
customers to eliminate batch processing and move to continuous processing of data. “Create Pipeline” command will 
automatically extract data from the Kafka source, perform some type of transformation, and then load it into the MemSQL 
database’s lead nodes (as opposed to loading them in MemSQL’s aggregator nodes first, as it did with Streamliner). [18] 
MemSQL is a real-time data warehouse for cloud and on-premises that delivers immediate insights across live and historical 
data. [19]

### Apache ORC

The smallest, fastest columnar storage for Hadoop workloads. ACID support, built-in indexes and complex types. [20]

### Apache RCFile

RCFile (Record Columnar File) is a data placement structure designed for MapReduce-based data warehouse systems. Hive added 
the RCFile format in version 0.6.0. RCFile stores table data in a flat file consisting of binary key/value pairs. It first 
partitions rows horizontally into row splits, and then it vertically partitions each row split in a columnar way. RCFile 
stores the metadata of a row split as the key part of a record, and all the data of a row split as the value part. RCFile 
combines the advantages of both row-store and column-store to satisfy the need for fast data loading and query processing, 
efficient use of storage space, and adaptability to highly dynamic workload patterns. As row-store, RCFile guarantees that 
data in the same row are located in the same node. As column-store, RCFile can exploit column-wise data compression and skip 
unnecessary column reads. [21]

### Apache Cassandra

The Apache Cassandra database is the right choice when you need scalability and high availability without compromising 
performance. Linear scalability and proven fault-tolerance on commodity hardware or cloud infrastructure make it the perfect 
platform for mission-critical data. Cassandra's support for replicating across multiple datacenters is best-in-class, 
providing lower latency for your users and the peace of mind of knowing that you can survive regional outages. [22]

### Mongo DB

MongoDB is a document database with the scalability and flexibility that you want with the querying and indexing that you 
need. MongoDB is a distributed database at its core, so high availability, horizontal scaling, and geographic distribution 
are built in and easy to use. [23]

### Neo4j

The World’s Leading Graph Database. Neo4j is a highly scalable, native graph database purpose-built to leverage not only 
data but also its relationships. Neo4j's native graph storage and processing engine deliver constant, real-time performance, 
helping enterprises build intelligent applications to meet today’s evolving data challenges. [24] Neo4j provides sustainable 
competitive advantage when: 1. Building new applications by leveraging value in data relationships 2.  Reimagining existing 
applications by harnessing the ever-increasing relatedness of data 3. Accelerating innovation by decreasing the time to 
create complex applications 4. Lowering total cost of ownership compared to traditional database management systems. [25]

### Apache CouchDB

Apache CouchDB™ lets you access your data where you need it by defining the Couch Replication Protocol that is implemented 
by a variety of projects and products that span every imaginable computing environment from globally distributed 
server-clusters, over mobile phones to web browsers. Software that is compatible with the Couch Replication Protocol 
include: PouchDB, Cloudant, and Couchbase Lite. Store your data safely, on your own servers, or with any leading cloud 
provider. Your web- and native applications love CouchDB, because it speaks JSON natively and supports binary for all your 
data storage needs. The Couch Replication Protocol lets your data flow seamlessly between server clusters to mobile phones 
and web browsers, enabling a compelling, offline-first user-experience while maintaining high performance and strong 
reliability. CouchDB comes with a developer-friendly query language, and optionally MapReduce for simple, efficient, and 
comprehensive data retrieval. [26]

### OrientDB

Imagine the power of a Distributed Graph Database engine with the flexibility of a Document Database all in one product. 
This is OrientDB. The first and best scalable, high-performance, operational NoSQL database. But there’s much more under the
hood. OrientDB incorporates a search engine, Key-Value and Object-Oriented concepts along with a reactive model (with Live
Queries) and geospatial awareness, making it the first and only true Multi-Model Database. [27]

### Terrastore

Terrastore is a modern document store which provides advanced scalability and elasticity features without sacrificing 
consistency. Terrastore is a distributed document store supporting single-cluster and multi-cluster deployments. Terrastore 
is elastic: you can add and remove nodes dynamically to/from your running cluster(s) with no downtime and no changes at all 
to your configuration. [28]

### FlockDB

FlockDB is a distributed graph database for storing adjancency lists, with goals of supporting: a high rate of 
add/update/remove operations, a potientially complex set arithmetic queries, paging through query result sets containing 
millions of entries, ability to "archive" and later restore archived edges, horizontal scaling including replication, 
online data migration. [29]

### Hibari

Hibari is a distributed, ordered key-value store with strong consistency guarantee. Hibari is written in Erlang and designed
for being: Fast, Read Optimized: Hibari serves read and write requests in short and predictable latency. Hibari has 
excellent performance especially for read and large value operations. High Bandwidth: Batch and lock-less operations help 
to achieve high throughput while ensuring data consistency and durability. Big Data: Can store Peta Bytes of data by 
automatically distributing data across servers. The largest production Hibari cluster spans across 100 of servers. Reliable: 
High fault tolerance by replicating data between servers. Data is repaired automatically after a server failure. [30]

### Riak

Riak is a distributed, decentralized data storage system. [31]

### Hypertable

Hypertable delivers scalable database capacity at maximum performance to speed up your big data application and reduce your 
hardware footprint. Hypertable seamlessly overlays on top of Hadoop to provide supercharged scalable database infastructure 
for your big data application. Hypertable delivers maximum efficiency and superior performance over the competition which 
translates into major cost savings. Google's Bigtable Design A proven scalable design that powers hundreds of Google 
services. 100% Open Source All the benefits of open source with a strong and thriving community. High Performance C++ 
implementation for optimum performance. Comprehensive Language Support Java, Node.js, PHP, Python, Perl, Ruby, C++ and more.
[32]

### Amazon S3

Amazon Simple Storage Service (Amazon S3) is object storage with a simple web service interface to store and retrieve any 
amount of data from anywhere on the web. It is designed to deliver 99.999999999% durability, and scale past trillions of 
objects worldwide. Customers use S3 as primary storage for cloud-native applications; as a bulk repository, or "data lake," 
for analytics; as a target for backup & recovery and disaster recovery; and with serverless computing. It's simple to move 
large volumes of data into or out of Amazon S3 with Amazon's cloud data migration options. Once data is stored in S3, it can
be automatically tiered into lower cost, longer-term cloud storage classes like S3 Standard - Infrequent Access and Amazon
Glacier for archiving. [33]

### Apache Drill

Schema-free SQL Query Engine for Hadoop, NoSQL and Cloud Storage. Get faster insights without the overhead (data loading, 
schema creation and maintenance, transformations, etc.). Analyze the multi-structured and nested data in non-relational 
datastores directly without transforming or restricting the data. Leverage your existing SQL skillsets and BI tools 
including Tableau, Qlikview, MicroStrategy, Spotfire, Excel and more. Drill supports a variety of NoSQL databases and file 
systems, including HBase, MongoDB, MapR-DB, HDFS, MapR-FS, Amazon S3, Azure Blob Storage, Google Cloud Storage, Swift, NAS 
and local files. A single query can join data from multiple datastores. For example, you can join a user profile collection 
in MongoDB with a directory of event logs in Hadoop.
Drill's datastore-aware optimizer automatically restructures a query plan to leverage the datastore's internal processing 
capabilities. In addition, Drill supports data locality, so it's a good idea to co-locate Drill and the datastore on the 
same nodes. [34]

### Apache Omid

Apache Omid (Optimistically transaction Management In Datastores) is a flexible, reliable, high performant and scalable 
transactional framework that allows Big Data applications to execute ACID transactions on top of MVCC key/value NoSQL 
datastores. The current implementation provides multi-row transactions on top of Apache HBase, but Omid’s design is flexible
enough to support other datastore implementations as long as they provide MVCC features in their API. [35]


### Yahoo! Pnuts

A massively parallel and geographically distributed database system for Yahoo!’s web applications. PNUTS provides data 
storage organized as hashed or ordered tables, low latency for large numbers of concurrent requests including updates and 
queries, and novel per-record consistency guarantees. It is a hosted, centrally managed, and geographically distributed 
service, and utilizes automated load-balancing and failover to reduce operational complexity. [36]

### Google Cloud Spanner

No-Compromise Relational Database Service. Cloud Spanner is the world’s first fully managed relational database service to 
offer both strong consistency and horizontal scalability for mission-critical online transaction processing (OLTP) 
applications. With Cloud Spanner you enjoy all the traditional benefits of a relational database; but unlike any other 
relational database service, Cloud Spanner scales horizontally to hundreds or thousands of servers to handle the biggest 
transactional workloads. Customers across industries use Cloud Spanner for mission-critical use cases including: 
  - Powering customer authentication and provisioning for multi-national businesses
  - Building consistent systems for transactions and inventory management in the financial services and retail industries
  - Supporting high-volume systems that require low latency and high throughput in the advertising and media industries [37]
  
### Google BigTable

Massively Scalable NoSQL. Cloud Bigtable is Google's NoSQL Big Data database service. It's the same database that powers 
many core Google services, including Search, Analytics, Maps, and Gmail. Bigtable is designed to handle massive workloads 
at consistent low latency and high throughput, so it's a great choice for both operational and analytical applications, 
including IoT, user analytics, and financial data analysis. Bigtable offers low latency and high throughput at any scale or 
application type. You can use Bigtable as the storage engine for large-scale, low-latency applications as well as 
throughput-intensive data processing and analytics. Bigtable provisions and scales to hundreds of petabytes automatically, 
and can smoothly handle millions of operations per second. Changes to the deployment configuration are immediate, so there 
is no downtime during reconfiguration. Bigtable integrates easily with popular Big Data tools like Hadoop, as well as Google
Cloud Platform products like Cloud Dataflow and Dataproc. Plus, Bigtable supports the open-source, industry-standard HBase 
API, which makes it easy for development teams to get started. [38]

### ElasticSearch

Elasticsearch is a distributed, RESTful search and analytics engine capable of solving a growing number of use cases. As 
the heart of the Elastic Stack, it centrally stores your data so you can discover the expected and uncover the unexpected. 
[39, 40]

### Druid

Druid is a high-performance, column-oriented, distributed data store. Issue sub-second ad-hoc queries to group, filter, and
aggregate data. Druid is ideal for powering multi-tenant user-facing applications. Druid runs on commodity hardware. 
Deploy it in the cloud or on-premise. Integrate with existing big data systems such as Hadoop, Spark, Kafka, Storm, Flink, 
and Samza. [41]

### Amazon Redshift

Amazon Redshift is a fast, fully managed data warehouse that makes it simple and cost-effective to analyze all your data 
using standard SQL and your existing Business Intelligence (BI) tools. It allows you to run complex analytic queries against
petabytes of structured data, using sophisticated query optimization, columnar storage on high-performance local disks, and
massively parallel query execution. [42]

### Amazon DynamoDB

Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit 
millisecond latency at any scale. It is a fully managed cloud database and supports both document and key-value store models.
Its flexible data model, reliable performance, and automatic scaling of throughput capacity, makes it a great fit for mobile,
web, gaming, ad tech, IoT, and many other applications. [43]

## References

[1] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 38)

[2] https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html#Introduction

[3] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 38)

[4] https://hive.apache.org/

[5] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 39)

[6] https://kudu.apache.org/

[7] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 40)

[8] https://hbase.apache.org/

[9] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 40)

[10] https://mapr.com/products/mapr-db-in-hadoop-nosql/

[11] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 40)

[12] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 40)

[13] https://pivotal.io/pivotal-hdb

[14] http://hawq.incubator.apache.org/

[15] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 41)

[16] https://parquet.apache.org/

[17] https://avro.apache.org/docs/current/s

[18] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 42)

[19] http://www.memsql.com/product/

[20] https://orc.apache.org/

[21] https://cwiki.apache.org/confluence/display/Hive/RCFile

[22] http://cassandra.apache.org/

[23] https://www.mongodb.com/what-is-mongodb

[24] https://neo4j.com/product/

[25] http://info.neo4j.com/rs/neotechnology/images/Product%20At-A-Glance.pdf?_ga=2.181388455.1484978126.1498419348-841463139.1498419348

[26] http://couchdb.apache.org/

[27] http://orientdb.com/orientdb/

[28] https://code.google.com/archive/p/terrastore/

[29] https://github.com/twitter-archive/flockdb

[30] https://github.com/hibari/hibari

[31] https://github.com/basho/riak

[32] http://www.hypertable.org/

[33] https://aws.amazon.com/s3/

[34] https://drill.apache.org/

[35] https://omid.incubator.apache.org/

[36] http://www.vldb.org/pvldb/1/1454167.pdf

[37] https://cloud.google.com/spanner/

[38] https://cloud.google.com/bigtable/

[39] https://www.elastic.co/products/elasticsearch

[40] https://github.com/elastic/elasticsearch

[41] http://druid.io/

[42] https://aws.amazon.com/redshift/

[43] https://aws.amazon.com/dynamodb/


























