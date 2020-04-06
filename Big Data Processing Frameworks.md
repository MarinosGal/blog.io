# Big Data Processing Frameworks

*In this post I will try to present in a compact and informative way all (since early 2018) the available big data 
processing frameworks. Based on popularity, some frameworks have more details than others and also there are 
comparisons between some of them.*

### Apache Hadoop

Hadoop is essentially a distributed data infrastructure: It distributes massive data collections across multiple nodes 
within a cluster of commodity servers, which means you don’t need to buy and maintain expensive custom hardware. It also 
indexes and keeps track of that data, enabling big-data processing and analytics far more effectively than was possible 
previously. Hadoop includes not just a storage component, known as the Hadoop Distributed File System, but also a processing 
component called MapReduce. The MapReduce workflow looks like this: read data from the cluster, perform an operation, write 
results to the cluster, read updated data from the cluster, perform next operation, write next results to the cluster, etc. 
MapReduce’s processing style can be just fine if your data operations and reporting requirements are mostly static and you 
can wait for batch-mode processing. Hadoop is naturally resilient to system faults or failures since data are written to 
disk after every operation [1] Key words: scalable, large amount of static data, distributed, parallel, fault tolerant, 
high latency.

### MapReduce

MapReduce was designed by Google as a programming model for processing large data sets with a parallel, distributed 
algorithm on a cluster. Key Terminology: 
  - **Job:** A full program – an execution of Mapper and Reducer across a data set. 
  - **Task:** An execution of a Mapper or a Reducer on a slice of data (Task In-Progress TIP). 
  - **Task Attempt:** A particular instance of an attempt to execute a task on a machine. Processing can occur on data stored 
                  either in a filesystem (unstructured) or in a database (structured). MapReduce can take advantage of the locality of the data, processing it near the place it is stored in order to reduce the distance over which it must be transmitted. 
  - **Map Step:** Each worker node applies the map() function to the local data, and writes the output to a temporary storage. 
              A master node ensures that only one copy of the redundant input data is processed. 
  - **Shuffle Step:** Worker nodes redistribute data based on the output keys (produced by the map() function), such all data 
                  belonging to one key is located on the same worker node. 
  - **Reduce Step:** Worker nodes now process each group of the output data, per key, in parallel. [27]
  
### Apache Spark
  
Spark, is a data-processing tool that operates on those distributed data collections; it doesn’t do distributed storage. 
You can also use Spark without Hadoop. Spark does not come with its own file management system, though, so it needs to be 
integrated with one - if not HDFS, then another cloud-based data platform. Spark was designed for Hadoop, however, so many 
agree they’re better together. Spark is generally a lot faster than MapReduce because of the way it processes data. While 
MapReduce operates in steps, Spark operates on the whole data set in one fell swoop. Spark completes the full data analytics 
operations in-memory and in near real-time: Read data from the cluster, perform all of the requisite analytic operations, 
write results to the cluster, done. If you need to do analytics on streaming data, like from sensors on a factory floor, or 
have applications that require multiple operations, you probably want to go with Spark. Most machine-learning algorithms, 
for example, require multiple operations. Common applications for Spark include real-time marketing campaigns, online 
product recommendations, cybersecurity analytics and machine log monitoring. Spark has similar built-in resiliency by 
virtue of the fact that its data objects are stored in something called resilient distributed datasets distributed across 
the data cluster. These data objects can be stored in memory or on disks, and RDD provides full recovery from faults or 
failures. 
**Spark use cases:** 
  - iterative Machine Learning algorithms 
  - Interactive analytics [1] In-memory data storage for every fast iterative processing. Replacement for the MapReduce 
    functions of Hadoop, running on top of an existing Haddop cluster, relying on YARN for resource scheduling. Spark can 
    layer on top of Mesos for scheduling or run as a stand-alone cluster using its built-in scheduler. Spark shines is in 
    its support for multiple processing paradigms and the supporting libraries. [10] 

**Spark Core:** general execution engine for Spark platform, in-memory computing capabilities deliver speed, general 
execution model supports wide variety of use cases. At the core of Apache Spark is the notion of data abstraction as 
distributed collection of objects called Resilient Distributed Dataset (RDD). RDD allows you to write programs that 
transform these distributed collection of objects (partitions) spread across a cluster of machines; data can be stored in 
memory or in disk (local). RDD enables parallel processing on data sets; data is partitioned across machines in a cluster 
that can be operated in parallel with a low-level API that offers transformations and actions. RDDs are fault tolerant as 
they track data lineage information to rebuild lost data automatically on failure; contains transformation history for whole 
dataset. 

**Operations:** Stateless Transformations (map, filter, groupBy), Actions (count, collect, save). MLlib is Spark’s 
general machine learning library: allows data scientists to focus on their data problems and models instead of solving the 
complexities surrounding distributed data. 

**ML Pipelines:** Running machine learning algorithms involves executing a sequence 
of tasks including pre-processing, feature extraction, model fitting and validation stages. A pipeline consists of a 
sequence of stages. There are two basic types of pipeline stages Transformer and Estimator. Transformer takes a dataset as 
input and produces an augmented dataset as output. Estimator must be first fit the input dataset to produce a model, which 
is a Transformer that transforms the input dataset.
 
### Apache Spark Streaming

Spark supports real-time distributed computation and stream-oriented processing, but it’s more of a general-purpose 
distributed computing platform. [10] Spark Streaming: run a streaming computation as a series of very small, deterministic 
batch jobs, batch size as low as ½ sec, latency of about 1 sec, exactly-once semantics, potential for combining batch and 
streaming processing in same system.

### Apache Flume

Apache Flume is a distributed and reliable service for efficiently collecting aggregating, and moving large amounts of 
streaming data into HDFS (especially “logs”). It has a simple and flexible architecture based on streaming data flows. 
It is robust and fault tolerant with tunable reliability mechanisms and many failover and recovery mechanisms. It uses 
a simple extensible data model that allows for online analytic application.[2]
Data is pushed to the destination (Push Mode) [A]. Flume does not replicate events – in case of flume-agent failure, 
you will lose events in the channel. [3]

### Apache kafka

Apache Kafka is a fast, horizontally scalable, durable, and fault-tolerant publish-subscribe messaging system*, a 
distributed streaming platform developed by LinkedIn, that persists messages to disk (Pull Mode) [A]. Designed for high 
throughput, is often used in place of traditional message brokers like JMS and AMQP, because of its higher throughput, 
reliability and replication. Use topics which many listeners can subscribe to, and thus processing of messages can happen 
in parallel on various channels. It is also used for building real-time data pipelines and streaming apps. [5][6]

In software architecture, publish–subscribe is a messaging pattern where senders of messages, called publishers, do not 
program the messages to be sent directly to specific receivers, called subscribers, but instead characterize published 
messages into classes without knowledge of which subscribers, if any, there may be. Similarly, subscribers express interest 
in one or more classes and only receive messages that are of interest, without knowledge of which publishers, if any, 
there are.[4]

**It gets used for two broad classes of application:**
  - Building real-time streaming data pipelines that reliably get data between systems or applications 
  - Building real-time streaming applications that transform or react to the streams of data.
  
**First a few concepts:**
  - Kafka is run as a cluster on one or more servers. 
  - The Kafka cluster stores streams of records in categories called topics. 
  - Each record consists of a key, a value, and a timestamp.
  
**Kafka has four core APIs:**
  - The Producer API allows an application to publish a stream of records to one or more Kafka topics. 
  - The Consumer API allows an application to subscribe to one or more topics and process the stream of records produced to 
    them. 
  - The Streams API allows an application to act as a stream processor, consuming an input stream from one or more topics 
    and producing an output stream to one or more output topics, effectively transforming the input streams to output 
    streams. 
  - The Connector API allows building and running reusable producers or consumers that connect Kafka topics to existing 
    applications or data systems. For example, a connector to a relational database might capture every change to a table. 
    
A topic is a category or feed name to which records are published. Topics in Kafka are always multi-subscriber; that is, a 
topic can have zero, one, or many consumers that subscribe to the data written to it.

### Apache Storm *(deprecated)*

Apache Storm developed by BackType (bought by Twitter) is a reliable real-time system for processing streaming data in real 
time (and generating new streams). Designed to support wiring “spouts” (think input streams) and “bolts” (processing and 
output modules) together as a directed acyclic graph (DAG) called a topology. One strength is the catalogue of available 
spouts specialized for receiving data from all types of sources. Storm topologies run on clusters and the Storm scheduler 
distributes work to nodes around the cluster, based on the topology configuration. [7] Storm makes it easy to reliably 
process unbounded streams of data, doing for realtime processing what Hadoop did for batch processing. Storm is simple, 
can be used with any programming language, and is a lot of fun to use. Storm has many use cases: realtime analytics, online 
machine learning, continuous computation, distributed RPC, ETL, and more. Storm is fast: a benchmark clocked it at over a 
million tuples processed per second per node. It is scalable, fault-tolerant, guarantees your data will be processed, and 
is easy to set up and operate. Storm integrates with the queueing and database technologies you already use. A Storm 
topology consumes streams of data and processes those streams in arbitrarily complex ways, repartitioning the streams 
between each stage of the computation however needed. [8]

### Twitter Heron

Twitter dropped Apache Storm in production in 2015 and replaced it with a homegrown data processing system, named Heron. 
Apache Storm was the original solution to Twitter’s problems. Storm it was reputedly hard to work with and hard to get good 
results from, and despite 1.0 renovation, it’s been challenged by other projects, including Apache Spark and its own revised 
streaming framework. Heron was built from scratch with a container – and cluster – based design. The user creates Heron jobs,
of “topologies”, and submits them to scheduling system, which launches the topology in a series of containers. The scheduler 
can be any of the number of popular schedulers, like Apache Mesos or Apache Aurora. Storm, by contrast, has to be manually 
provisioned on clusters to add scale. Heron is backward compatible with Storm’s API. Storm spouts and bolts could then be 
reused in Heron. Gives existing Storm users some incentive to check out Heron. Code is to be written in Java or Scala. The 
web-based UI components are written in Python. The critical parts of the framework, the code that manages the topologies and 
network communications is written in C++. Twitter claims it’s been able to gain anywhere from two to five times an 
improvements in “efficiency” (basically, lower opex and capex) [B] with Heron.[9]

### Google Cloud Dataflow

Fully-managed cloud service and programming model for batch and streaming big data processing. Used for developing and 
executing a wide range of data processing patterns including ETL, batch computation and continuous computation. 
Cloud Dataflow “frees” from operational tasks like resource management and performance optimization. The open source 
Java-based Cloud Dataflow SDK enables developers to implement custom extensions and to extend Dataflow to alternate service 
environments. [11][12]

### Google Dataflow vs Apache Spark

Dataflow is clearly faster than Spark. But Spark has an ace up its sleeve in form of REPL, or its “read evaluate print loop”
functionality, which enables users to iterate on their problems quickly and easily. While Spark maintains an edge among 
data scientists looking to iterate quickly, Google Cloud Dataflow seems to hold the advantage in the operations department, 
thanks to all the work that Google has done over the years to optimize queries at scale.

### Apache Beam

Apache Beam is an open source, unified programming model used to create a data processing pipeline. Start by building a 
program that defines the pipeline using one of the open source Beam SDKs. The pipeline is then executed by one of the Beam’s
supported distributed processing back-ends, which include Apache Flink, Apache Spark, and Google Cloud Dataflow. Beam is 
particularly useful for embarrassingly parallel data processing tasks, in which the problem can be decomposed into many 
smaller bundles of data that can be processed independently and in parallel. Beam can also be used for ETL tasks and pure 
data integration. [13] 
  - Unified: Use a single programming model for both batch and streaming use cases.
  - Portable: Execute pipelines on multiple execution environments. 
  - Extensible: Write and share new SDKs, IO connectors, and transformation libraries. (Java and Python) [14]

### Concord

Concord is a distributed stream processing framework built in C++ on top of Apache Mesos, designed for high performance data 
processing jobs that require flexibility & control. Concord is an inclusive stream processing solution that takes care of 
systems' configuration and management for you. That way, you can spend your time working on business logic rather than 
managing your infrastructure. Dynamic Topology: You can deploy, scale, or kill running jobs without having to hard restart 
anything. Each job can publish or subscribe to any other jobs at runtime. 
You can write your jobs in C++, Python, Ruby, Go, Java, or Scala. Concord runs 10x more throughput than Apache Storm or 
Apache Spark at milliseconds latency. You can see it yourself with built-in monitoring for latency, throughput, CPU load, 
Memory utilization and more. [15]

### Apache Flink

Apache Flink is an open-source stream processing framework for distributed, high-performing, always-available, and accurate 
data streaming applications. [17] Apache Flink’s core is a streaming dataflow engine that provides data distribution, 
communication and fault tolerance for distributed computations over data streams. Flink’s includes several APIs for creating 
applications that use the Flink engine: DataStream API for unbounded streams embedded in Java and Scala, DataSet API for 
static data embedded in Java, Scala and Python , Table API with SQL-like expression language embedded in java and Scala. 
Flink also bundles libraries for domain-specific use cases: CEP, a complex event processing library, Machine Learning 
Library, Gelly a graph processing API and library. [16]

### Apache Spark vs Flink

**Flink is:** optimized for cyclic or iterative processes by using iterative transformations on collections. 
This is achieved by optimization of join algorithms, operator chaining and reusing of partitioning and sorting. 
However, Flink is also a string tool for batch processing.

**Spark is:** based on RDDs. This in-memory data structure gives the power to Spark’s functional programming paradigm. 
It is capable of big batch calculations by pinning memory. [18]

### Apache Apex

Apache Apex is a YARN-native integrated platform that unifies stream and batch processing. It process big data in-motion in 
a way that is highly scalable, highly performant, fault-tolerant, statefull, secure and distributed. [19] Write your 
business logic and leave all operability to the platform. It provides a simple API that enables developers to write or 
re-use generic Java code, thereby lowering the expertise needed to write big data applications. Application logic broken 
into components (operators) that execute distributed in a cluster. Machine Learning on Apache Apex with Apache SAMOA. 
Use cases: GE’s Predix IoT cloud platform uses Apex for industrial data and analytics. Capital One for rea-time decisions 
and fraud detection.[20, 21, 22]

### Apache Apex vs Spark and Storm

Spark and Storm are considered difficult to use, they are built to batch engines, rather than true streaming architecture, 
and don’t natively support statefull computation. They can’t do low latency processing that Apex can, and will suffer a 
latency overhead for having to schedule batched repeatedly, no matter how quickly that occurs.[20]

### Apache Samza

Samza is a distributed stream-processing framework that is based on Apache Kafka and YARN. It provides a simple 
callback-based API that’s similar to MapReduce, and it includes snapshot management and fault tolerance in a durable and 
scalable way. [23]

### Amazon Kinesis

Kinesis is Amazon’s service for real-time processing streaming data on the cloud. Deeply integrated with other Amazon 
services via connectors, such as S3, Redshift, and DynamoDB, for complete Big Data architecture. [23]

### NFS Gateway

The NFS Gateway supports NFSv3 and allows HDFS to be mounted as part of the client’s local file system. 
Currently NFS Gateway supports and enables the following usage patterns:
  - Users can browse the HDFS file system through their local file system on NFSv3 client compatible operating systems.
  - Users can download files from the HDFS file system on to their local file system.
  - Users can upload files from their local file system directly to the HDFS file system.
  - Users can stream data directly to HDFS through the mount point. File append is supported but random write is not 
    supported. [24, 25]
    
### Apache Sqoop

Apache Sqoop is a tool designed for efficiently transferring bulk data between Hadoop and structured data stores 
(and vice-versa). 
  - Import data from external structured data stores into a HDFS. 
  - Extract data from Hadoop and export it to external structured data stores like relational database and enterprise data 
    warehouses. [26]

### Cascading

Cascading is the proven application development platform for building data applications on Hadoop. Simplifies development 
of Cascading applications through an advanced auto-suggesting fluent API. Simplifies systems integration through ANSI SQL 
compatibility and a JDBC driver. Enables development with Scala, a powerful language for solving functional problems. 
Enables development with Clojure, a Lisp dialect. [29]

### Apache Tez

The Apache Tez project is aimed at building an application framework which allows for a complex directed-acyclic-graph of 
tasks for processing data. It is currently built atop Apache Hadoop YARN. The 2 main design themes for Tez are:
  - **Empowering end users by:**
      - Expressive dataflow definition APIs
      - Flexible Input-Processor-Output runtime model
      - Data type agnostic
      - Simplifying deployment
  - **Execution Performance**
      - Performance gains over Map Reduce
      - Optimal resource management
      - Plan reconfiguration at runtime

### Apache Pig

Apache Pig is a platform for analyzing large data sets that consists of a high-level language for expressing data analysis 
programs, coupled with infrastructure for evaluating these programs. The salient property of Pig programs is that their 
structure is amenable to substantial parallelization, which in turns enables them to handle very large data sets. At the 
present time, Pig's infrastructure layer consists of a compiler that produces sequences of Map-Reduce programs, for which 
large-scale parallel implementations already exist (e.g., the Hadoop subproject). Pig's language layer currently consists of 
a textual language called Pig Latin, which has the following key properties: 
  - Ease of programming. It is trivial to achieve parallel execution of simple, "embarrassingly parallel" data analysis 
    tasks. Complex tasks comprised of multiple interrelated data transformations are explicitly encoded as data flow 
    sequences, making them easy to write, understand, and maintain.
  - Optimization opportunities. The way in which tasks are encoded permits the system to optimize their execution 
    automatically, allowing the user to focus on semantics rather than efficiency.
  - Extensibility. Users can create their own functions to do special-purpose processing.
  
 [31] Supports machine learning algorithms [32]
 
### Hortonworks Dataflow
 
Hortonworks DataFlow (HDF) provides the only end-to-end platform that collects, curates, analyzes and acts on data in 
real-time, on-premises or in the cloud, with a drag-and-drop visual interface. HDF is an integrated solution with 
Apache Nifi/MiNifi, Apache Kafka, Apache Storm and Druid. [35]

### Amazon EC2 F1

Amazon EC2 F1 is a compute instance with field programmable gate arrays (FPGAs) that you can program to create custom 
hardware accelerations for your application. F1 instances are easy to program and come with everything you need to develop, 
simulate, debug, and compile your hardware acceleration code, including an FPGA Developer AMI and Hardware Developer Kit 
(HDK). Once your FPGA design is complete, you can register it as an Amazon FPGA Image (AFI), and deploy it to your F1 
instance in just a few clicks. You can reuse your AFIs as many times, and across as many F1 instances as you like. [36]

### Apache Hyracks

Hyracks is a new Partitioned-parallel software platform. It is designed to run data-intensive computations on large 
shared-nothing clusters of computers. Hyracks allows users to express a computation as a DAG of data operators and 
connectors. Operators operate on partitions of input data and produce partitions of output data, while connectors 
repartition operators' outputs to make the newly produced partitions available at the consuming operators. The ASTERIX 
project is developing new technologies for ingesting, storing, managing, indexing, querying, analyzing, and subscribing to 
vast quantities of semi-structured information. Hyracks was used as a substrate for implementing Scaling Datalog for 
Machine Learning on Big Data. [37] Pregelix is an open-source implementation of the bulk-synchronous vertex-oriented 
programming model for large-scale graph analytics, which scales to very large clusters and very large graphs. [38]

### Tupleware

A new system specifically aimed at the challenges faced by the typical user. Tupleware’s architecture brings together ideas 
from the database and compiler communities to create a powerful end-to-end solution for data analysis. It considers the data,
computations, and hardware together to achieve maximum performance on a case-by-case basis. Machine learning and advanced 
statistics are important tools for drawing insights from large datasets. However, these techniques often require human 
intervention to steer computation towards meaningful results. To that end, we are building Vizdom, a new system for 
interactive analytics through pen and touch. Vizdom’s frontend allows users to visually compose complex workflows of 
machine learning and statistics operators on an interactive whiteboard, and the backend leverages recent advances in 
workflow compilation techniques to run these computations at interactive speeds. [39]

### Microsoft Dryad

The Dryad Project is investigating programming models for writing parallel and distributed programs to scale from a small 
cluster to a large data-center. Dryad is an infrastructure which allows a programmer to use the resources of a computer 
cluster or a data center for running data-parallel programs. A Dryad programmer can use thousands of machines, each of them 
with multiple processors or cores, without knowing anything about concurrent programming. [40]

### Apache Mahout

The Apache Mahout project’s goal is to build an environment for quickly creating scalable performant machine learning 
applications. Apache Mahout software provides three major features:
  - A simple and extensible programming environment and framework for building scalable algorithms
  - A wide variety of premade algorithms for Scala + Apache Spark, H2O, Apache Flink
  - Samsara, a vector math experimentation environment with R-like syntax which works at scale

Apache Mahout Samsara Environment includes
  - Distributed Algebraic optimizer
  - R-Like DSL Scala API
  - Linear algebra operations
  - Ops are extensions to Scala
  - IScala REPL based interactive shell
  - Integrates with compatible libraries like MLLib
  - Runs on distributed Spark, H2O, and Flink
  - Fastutil to speed up sparse matrix and vector computations
  - Matrix to tsv conversions for integration with Apache Zeppelin Apache Mahout Samsara Algorithms included
  - Stochastic Singular Value Decomposition (ssvd, dssvd)
  - Stochastic Principal Component Analysis (spca, dspca)
  - Distributed Cholesky QR (thinQR) 
  - Distributed regularized Alternating Least Squares (dals)
  - Collaborative Filtering: Item and Row Similarity
  - Naive Bayes Classification
  - Distributed and in-core [41]

### Apache Datafu

Apache DataFu (incubating) is a collection of libraries for working with large-scale data in Hadoop. The project was 
inspired by the need for stable, well-tested libraries for data mining and statistics. It consists of two libraries:
  - Apache DataFu Pig: a collection of user-defined functions for Apache Pig
  - Apache DataFu Hourglass: an incremental processing framework for Apache Hadoop in MapReduce [42]
  
### Apache Ignite

Apache Ignite is a high-performance, integrated and distributed in-memory platform for computing and transacting on 
large-scale data sets in real-time, orders of magnitude faster than possible with traditional disk-based or flash 
technologies. [44]

### Apache Gearpump

Gearpump is a lightweight real-time big data streaming engine. It is inspired by recent advances in the Akka framework and 
a desire to improve on existing streaming frameworks. [45]

### Apache Akka

Build powerful reactive, concurrent & distributed applications more easily. Akka is a toolkit and runtime for building 
highly concurrent, distributed, and resilient message-driven applications for Java and Scala. [46]

### Apache Mesos

Apache Mesos abstracts CPU, memory, storage, and other compute resources away from machines (physical or virtual), 
enabling fault-tolerant and elastic distributed systems to easily be built and run effectively. Mesos is built using the 
same principles as the Linux kernel, only at a different level of abstraction. The Mesos kernel runs on every machine and 
provides applications (e.g., Hadoop, Spark, Kafka, Elasticsearch) with API’s for resource management and scheduling across 
entire datacenter and cloud environments. [47]

### Apache Hadoop Yarn

The fundamental idea of YARN is to split up the functionalities of resource management and job scheduling/monitoring into 
separate daemons. The idea is to have a global ResourceManager (RM) and per-application ApplicationMaster (AM). 
An application is either a single job or a DAG of jobs.  The ResourceManager and the NodeManager form the data-computation 
framework. 
  - The ResourceManager is the ultimate authority that arbitrates resources among all the applications in the system. 
  - The NodeManager is the per-machine framework agent who is responsible for containers, monitoring their resource usage 
    (cpu, memory, disk, network) and reporting the same to the ResourceManager/Scheduler. [48]
    
### Apache Aurora

Aurora is a Mesos framework for long-running services and cron jobs. Aurora runs applications and services across a shared 
pool of machines, and is responsible for keeping them running, forever. When machines experience failure, Aurora 
intelligently reschedules those jobs onto healthy machines. [49]

### Scribe

Scribe is a server for aggregating log data that's streamed in real time from clients. It is designed to be scalable and 
reliable. [28]

### Apache S4

S4 (Simple Scalable Streaming System) is a general-purpose, distributed, scalable, partially fault-tolerant, pluggable 
platform that allows programmers to easily develop applications for processing continuous, unbounded streams of data. [34]

## References

[1] https://iamsoftwareengineer.wordpress.com/2015/12/15/hadoop-vs-spark/?iframe=true&theme_preview=true

[2] https://flume.apache.org/

[3] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 8)

[4] https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

[5] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 9)

[6] https://kafka.apache.org/

[7] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 10)

[8] http://storm.apache.org/

[9] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 13)

[10] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 10)

[11] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 21)

[12] https://cloud.google.com/dataflow/

[13] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 23)

[14] https://beam.apache.org/

[15] http://concord.io/

[16] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 25)

[17] https://flink.apache.org/

[18] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 28)

[19] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 29)

[20] https://apex.apache.org/

[21] http://events.linuxfoundation.org/sites/events/files/slides/ApacheBigDataEU2016IntroApacheApex_0.pdf

[22] http://events.linuxfoundation.org/sites/events/files/slides/Apache%20BigData%20-%20Machine%20Learning%20On%20Apache%20Apex%20using%20Apache%20SAMOA%20v2.0.pdf

[23] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 30)

[24] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 31)

[25] https://hadoop.apache.org/docs/r2.8.0/hadoop-project-dist/hadoop-hdfs/HdfsNfsGateway.html

[26] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 31)

[27] https://www.slideshare.net/welkaim/big-data-architecture-part-2 (slide 56)

[28] https://github.com/facebookarchive/scribe

[29] http://www.cascading.org/

[30] https://tez.apache.org/

[31] https://pig.apache.org/

[32] https://www.slideshare.net/Hadoop_Summit/t-1205p230-cstella

[33] http://camel.apache.org/kestrel.html

[34] http://incubator.apache.org/projects/s4.html

[35] https://hortonworks.com/products/data-center/hdf/

[36] https://aws.amazon.com/ec2/instance-types/f1/

[37] https://arxiv.org/pdf/1203.0160.pdf

[38] http://hyracks.weebly.com/

[39] http://tupleware.cs.brown.edu/

[40] https://www.microsoft.com/en-us/research/project/dryad/#

[41] http://mahout.apache.org/

[42] https://datafu.incubator.apache.org/

[43] https://nifi.apache.org/

[44] https://ignite.apache.org/

[45] https://github.com/gearpump/gearpump

[46] http://akka.io/

[47] http://mesos.apache.org/

[48] https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html

[49] http://aurora.apache.org/

## More

[A] Push vs Pull mode
  - Push mode: The client establishes a constant HTTP connection to the server. Whenever a change occurs with the server 
               status, it notifies the client immediately.
        
  - Pull mode: The client connects to the server periodically, depending on the 
    frequency of the heartbeat setting. The client checks the status of the server when it connects.
    Source: https://www.symantec.com/connect/forums/pull-mode-vs-push-mode
    
[B] An operating expense, operating expenditure, operational expense, operational expenditure or Opex is an ongoing cost 
    for running a product, business, or system. Its counterpart, a capital expenditure (Capex), is the cost of developing 
    or providing non-consumable parts for the product or system
    
[C] APACHE OPENNLP: The Apache OpenNLP library is a machine learning based toolkit for the processing of natural language 
    text. OpenNLP supports the most common NLP tasks, such as tokenization, sentence segmentation, part-of-speech tagging, 
    named entity extraction, chunking, parsing, and coreference resolution. https://opennlp.apache.org/
    
[D] STANFORD CORENLP: Stanford CoreNLP provides a set of human language technology analysis tools. It can give the base 
    forms of words, their parts of speech, whether they are names of companies, people, etc., normalize dates, times, and 
    numeric quantities, mark up the structure of sentences in terms of phrases and syntactic dependencies, indicate which 
    noun phrases refer to the same entities, indicate sentiment, extract particular or open-class relations between entity 
    mentions, get quotes people said, etc. https://stanfordnlp.github.io/CoreNLP/
    
[E] MALLET: MALLET is a Java-based package for statistical natural language processing, document classification, clustering, 
    topic modeling, information extraction, and other machine learning applications to text. 
    MALLET includes sophisticated tools for document classification: efficient routines for converting text to "features", 
    a wide variety of algorithms (including Naïve Bayes, Maximum Entropy, and Decision Trees), and code for evaluating 
    classifier performance using several commonly used metrics. http://mallet.cs.umass.edu/
  
