# Big Data Technologies

*A categorization of big data tecnologies based on injestion, storage, processing and access*

## Ingestion
  - **Architecture:**
    - Scalable, Extensible to capture streaming and batch data
    - Provide capability to business logic, filters, validation, data quality, routing, etc. business requirements
    
  - **Technology stack:**
    - Apache Flume
    - Apache Kafka
    - Apache Storm
    - Apache Sqoop
    - NFS Gateway

## Storage/Retention
  - **Data Storage:**
    - Depending on the requirements data is paced into Hadoop HDFS, Hive, Hbase, Elastic Search or In-memory
    - Metadata management
    - Policy-based data Retention is provided
    
  - **Technology stack:**
    - HDFS
    - Hive Tables
    - Hbase/MapR DB
    - Elastic Search

## Processing
  - **Data Processing:**
    - Processing is provided for both batch and near-realtime use cases
    - Provision workflows for repeatable data processing
    - Provide late data arrival handling
    
  - **Technology stack:**
    - Map Reduce
    - Hive
    - Spark
    - Storm
    - Drill
    
 ## Access
  - **Visualization and APIs:**
    - Dashboard and applications that provides valuable business insights
    - Data will be made available to consumers using API, MQ Feed and DB Access
    
  - **Technology stack:**
    - Qlik/Tableau/Spotfire
    - REST APIs
    - Apache Kafka
    - JDBC
    
 ## Management, Monitoring, Governance
  - Ambari
  - Cloudera Manager
  - Cloudera Navigator
  - MapR MCS
  
*Information by William El Kaim 2016*
