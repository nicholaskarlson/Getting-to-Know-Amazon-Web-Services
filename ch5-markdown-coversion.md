# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 5 - AWS Database Services


## Intro 

**AWS Global Infrastructure**: Understand how AWS's infrastructure is geographically distributed across regions, availability zones, and edge locations.

**Compute Services**: Familiarize yourself with Amazon EC2 instances, AWS Lambda, and Elastic Beanstalk. Each service has its use case, such as running applications on virtual servers (EC2), running code without provisioning servers (Lambda), or deploying apps developed in Java, .NET, PHP, Node.js, etc. (Elastic Beanstalk).

**Storage Services**: Understand Amazon S3 for object storage, EBS for block-level storage, and Amazon Glacier for long-term cold storage.

**Database Services**: Be familiar with Amazon RDS, DynamoDB, ElastiCache, and Redshift, each providing different database functionalities, from relational, NoSQL, caching to data warehousing.

**Networking & Content Delivery**: Study Amazon VPC for virtual private cloud environments, ELB for load balancing, Route 53 for DNS services, and CloudFront for content delivery.

**Security, Identity & Compliance**: Comprehend AWS IAM for identity and access management, Amazon Cognito for mobile user identity, and KMS for key management.

**Management Tools**: Know the basic functionality of CloudWatch for monitoring, CloudFormation for infrastructure as code, CloudTrail for AWS API call recording, and Trusted Advisor for real-time guidance.

**Application Integration**: Understand SQS (queue service), SNS (notification service), and step functions (serverless workflow service).

**AWS Pricing and Cost Management**: Know how to calculate costs, use the AWS Pricing Calculator, and understand the fundamentals of the AWS Free Tier, On-Demand vs Reserved vs Spot instances.

**Well-Architected Framework**: AWS provides this framework as a guide to creating efficient and effective systems. It includes five pillars: operational excellence, security, reliability, performance efficiency, and cost optimization.

**Shared Responsibility Model**: An understanding of the shared responsibility model is important. AWS is responsible for "security of the cloud," while customers are responsible for "security in the cloud."

**AWS Architectural Principles**: These include designing for failure, implementing elasticity, and decoupling components of your application.


## AWS Database Services

AWS offers a broad range of database services to fit different types of applications and use cases. Here are the primary AWS Database Services:

**Amazon RDS** (Relational Database Service): This is a managed relational database service that provides access to capabilities of a familiar MySQL, MariaDB, PostgreSQL, Oracle, Microsoft SQL Server, or Amazon Aurora database engine. It manages time-consuming database administration tasks including patching, backup, recovery, failure detection, and repair.

**Amazon Aurora**: This is a relational database built for the cloud, compatible with MySQL and PostgreSQL, that combines the performance and availability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases.

**Amazon DynamoDB**: This is a key-value and document NoSQL database that delivers single-digit millisecond performance at any scale. It's a fully managed, multiregion, multimaster database with built-in security, backup and restore, and in-memory caching for internet-scale applications.

**Amazon DocumentDB** (with MongoDB compatibility): This is a fast, scalable, highly available, and fully managed document database service that supports MongoDB workloads. Developers can use the same MongoDB application code, drivers, and tools to run, manage, and scale workloads on Amazon DocumentDB.

**Amazon Redshift**: Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. It is designed for high-performance analysis of structured, semi-structured and complex data using familiar SQL-based clients and business intelligence (BI) tools.

**Amazon ElastiCache**: This service makes it easy to deploy, operate, and scale an in-memory cache in the cloud. It improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk-based databases. ElastiCache supports two open-source in-memory caching engines: Memcached and Redis.

**Amazon Neptune**: This is a fast, reliable, fully-managed graph database service that makes it easy to build and run applications that work with highly connected datasets. The core of Neptune is a purpose-built, high-performance graph database engine optimized for storing billions of relationships and querying the graph with milliseconds latency.

**AWS Database Migration Service** (DMS): This service helps you migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database.

Each of these database services is designed for different use cases and provides a different set of features and capabilities. It's important to choose a database service that is the best fit for your particular application and use case.


# AWS Database Services - Detail


## Amazon Relational Database Service

**Amazon Relational Database Service** (Amazon RDS) **is a fully managed relational database service provided by AWS**. It greatly simplifies the process of setting up, operating, and scaling a relational database in the cloud, making it a suitable choice for applications that need a relational database, a SQL interface, or both.

Here are the key database engines that Amazon RDS supports as of September 2021:

1. MySQL: One of the most popular open-source relational database systems.

2. PostgreSQL: Another popular open-source relational database system known for its advanced features and extensibility.

3. MariaDB: A community-developed fork of MySQL, guaranteeing backward compatibility with MySQL.

4. Oracle Database: A widely used commercial relational database system.

5. Microsoft SQL Server: Another widely used commercial relational database system, commonly used in enterprise settings.

6. Amazon Aurora: Amazon's own cloud-optimized relational database that is compatible with MySQL and PostgreSQL. It's known for its performance, scalability, and reliability.

**Key aspects of Amazon RDS include**:

1. **Fully Managed**: Amazon RDS manages tedious tasks like database setup, patching, and backups. It provides cost-efficient and resizable capacity while managing time-consuming database administration tasks.

2. **Scalability**: Amazon RDS allows you to easily scale your database's compute resources or storage capacity.

3. **High Availability and Durability**: With Multi-AZ deployments, Amazon RDS automatically provisions and maintains a synchronous standby replica in a different Availability Zone. It also performs automated backups, database snapshots, and automatic host replacement.

4. **Security**: Amazon RDS makes it easy to control network access to your database. It also lets you run your database instances in Amazon Virtual Private Cloud (VPC), which allows you to isolate your database instances and to connect to your existing IT infrastructure through an industry-standard encrypted IPsec VPN.

5. **Compatibility**: Amazon RDS is SQL-compatible and can thus work seamlessly with existing applications that use SQL databases.

In summary, Amazon RDS is a service that simplifies many of the common tasks associated with setting up and managing relational databases, allowing you to focus on your applications and business logic rather than database administration. Whether you're running enterprise applications, a high-traffic website, or a new startup app, Amazon RDS can provide a reliable, scalable, and secure database solution.


## Amazon Aurora

**Amazon Aurora is a MySQL and PostgreSQL compatible relational database built for the cloud**, that combines the performance and availability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases. It is a part of Amazon RDS (Relational Database Service) and is designed to handle enterprise-level database workloads.

**Key features of Amazon Aurora include**:

1. **Performance**: Aurora offers up to five times the throughput of standard MySQL and up to three times the throughput of standard PostgreSQL. This increased performance is the result of various optimizations such as advanced query optimization, memory caching, and parallelized read/write operations.

2. **Compatibility**: Aurora is fully compatible with existing MySQL and PostgreSQL open-source databases, which means that applications, drivers and tools that you already use with your existing databases can be used with Amazon Aurora with little or no modification.

3. **Scalability**: Aurora automatically grows storage as needed, up to 64TB per database instance. It also allows for up to 15 low-latency read replicas, and it automatically divides your database volume into 10GB segments spread across many disks.

4. **High Availability and Durability**: Aurora is designed to offer greater than 99.99% availability. It has fault-tolerant and self-healing storage built for the cloud that replicates six copies of your data across three Availability Zones. Aurora continuously backs up your data to Amazon S3, and transparently recovers from physical storage failures.

5. **Security**: Aurora provides multiple levels of database security. These include network isolation using Amazon VPC, encryption at rest using keys you create and control through AWS Key Management Services (KMS), and encryption of data in transit using SSL.

6. **Fully Managed**: Amazon Aurora is fully managed by Amazon RDS, which automates time-consuming administration tasks like hardware provisioning, database setup, patching, and backups.

In terms of pricing, Amazon Aurora is charged based on the capacity you consume. This consumption is measured in "Aurora Capacity Units" and you pay on a per-second basis.

In summary, Amazon Aurora is a powerful, fully managed database solution that provides the speed, reliability, and scalability of a commercial database at a fraction of the cost, while maintaining compatibility with popular open-source databases.


## Amazon DynamoDB

**Amazon DynamoDB is a fully managed NoSQL database service provided by Amazon Web Services (AWS)**. It is designed to provide low-latency, high-throughput performance by automatically scaling and adjusting to your application's demands. DynamoDB supports both key-value and document data structures, making it a versatile option for mobile, web, gaming, ad tech, IoT, and other applications that need consistent, single-digit millisecond latency at any scale.

**Key aspects of Amazon DynamoDB include**:

1. Fully Managed: Amazon DynamoDB automatically manages the administrative burdens of operating and scaling a distributed database such as hardware and software patching, setup and configuration, replication, software patching, cluster scaling, partitioning, and backups.

2. Performance at Scale: DynamoDB supports some of the world's largest scale applications by providing consistent, single-digit millisecond response times at any scale. You can build apps with virtually unlimited throughput and storage.

3. Flexibility: DynamoDB is a schemaless NoSQL database service, which gives you flexibility to adapt your data model to your application's evolving requirements. You can store any amount of data and serve any level of request traffic.

4. High Availability and Durability: DynamoDB automatically replicates your data across multiple AWS Regions to provide better availability, durability, and fault tolerance. It uses a multi-AZ data replication model, which means your data is stored across three geographically distinct Availability Zones for high availability.

5. Security: DynamoDB provides in-built security mechanisms such as encryption at rest (which secures your data from unauthorized access) and encryption in transit (which secures data during network transfers). It also integrates with AWS Identity and Access Management (IAM) for access control.

6. Serverless: DynamoDB fits in well with serverless architectures, including the ability to trigger AWS Lambda functions when specific conditions are met.

7. Event Driven Programming: DynamoDB Streams captures table activity, and its event-driven programming model makes it easy for applications to react to table updates.

8. Backup and Restore: DynamoDB provides on-demand and continuous backups to safeguard your tables, and point-in-time recovery (PITR) to restore your tables from backup at any point in time.

9. DynamoDB Accelerator (DAX): DAX is a fully managed, highly available, in-memory cache that can reduce DynamoDB response times from milliseconds to microseconds, even at millions of requests per second.

In summary, Amazon DynamoDB is a powerful NoSQL database service providing fast and predictable performance with seamless scalability. If you are a developer, you can use DynamoDB to create a database table that can store and retrieve any amount of data and serve any level of request traffic.


## Amazon DocumentDB with MongoDB compatibility

**Amazon DocumentDB** (with MongoDB compatibility) is a fully managed, scalable NoSQL database service offered by Amazon Web Services for storing, querying, and indexing JSON-like documents and data. It is designed to be compatible with MongoDB, which is a popular NoSQL database that uses a document-oriented data model and supports a rich query language.

**Here are the key features and aspects of Amazon DocumentDB**:

1. MongoDB Compatibility: Amazon DocumentDB is designed to be compatible with MongoDB, meaning it works with MongoDB drivers and tools. As of my knowledge cutoff in September 2021, it supports MongoDB 3.6 and 4.0 APIs. Applications designed for MongoDB can often be migrated to Amazon DocumentDB with minimal changes.

2. Fully Managed: Amazon DocumentDB offloads the time-consuming administrative tasks such as hardware provisioning, patch management, setup, configuration, and backups. This allows developers to focus on their applications rather than managing the database.

3. Scalability and Performance: Amazon DocumentDB is designed to scale and offers the capacity to handle millions of requests per second. It separates compute and storage resources, allowing each to be scaled independently.

4. Durability and Availability: Amazon DocumentDB replicates your data six times across three AWS Availability Zones (AZs). It continuously backs up your data to Amazon S3, enabling point-in-time recovery. This design provides high availability and durability for your data.

5. Security: Amazon DocumentDB provides multiple levels of security for your database. These include network isolation using Amazon VPC, encryption at rest using keys you create and control through AWS Key Management Services (KMS), encryption of data in transit using Transport Layer Security (TLS), and the ability to audit system events using AWS CloudTrail.

6. Integration with AWS Services: Amazon DocumentDB integrates with various AWS services like AWS CloudFormation, AWS CloudTrail, AWS Lambda, Amazon CloudWatch, and AWS Identity and Access Management (IAM).

In summary, Amazon DocumentDB with MongoDB compatibility is a robust and scalable NoSQL database service. It makes it easy for developers to store, query, and index JSON-like documents and data at scale while maintaining compatibility with existing MongoDB applications and tools. It is particularly well suited for mobile apps, web apps, content management, real-time analytics, and applications leveraging IoT data.


## Amazon Redshift

Amazon Redshift is a fully managed, petabyte-scale data warehousing service provided by Amazon Web Services (AWS). Redshift is designed for online analytical processing (OLAP) and business intelligence (BI) applications that require complex queries on large datasets.

**Here are the key aspects of Amazon Redshift**:

1. Fully Managed: Amazon Redshift manages all the work needed to set up, operate, and scale a data warehouse, from provisioning capacity to monitoring and backing up the cluster, to applying patches and upgrades.

2. Performance: Amazon Redshift uses columnar storage technology and parallel query execution to deliver high-speed performance for read-heavy analytic queries. It also utilizes machine learning to deliver high throughput, regardless of the size of the data set or complexity of the query.

3. Scalability: With Redshift, you can start with a small dataset and scale upwards to a petabyte or more, while maintaining high query performance. Scaling is easy and does not require any downtime.

4. Cost-Effective: Amazon Redshift is more cost-effective than traditional data warehousing solutions. It provides the option of on-demand pricing with no upfront costs, or reserved instance pricing for long-term commitments. Redshift Spectrum, an Amazon Redshift feature, also allows you to directly run SQL queries against exabytes of unstructured data in Amazon S3, saving costs on storage.

5. Integration: Amazon Redshift integrates with a number of AWS services such as Amazon S3, Amazon DynamoDB, Amazon EMR, AWS Glue, AWS Data Pipeline and Amazon Kinesis for data loading, transformation, and processing. It also integrates with popular third-party BI and data integration tools.

6. Security: Amazon Redshift provides a number of security features to secure your data. These include VPC for network isolation, SSL/TLS for securing data in transit, AWS Key Management Service (KMS) for encryption at rest, and IAM for access control.

7. Availability and Durability: Amazon Redshift automatically replicates all your data within your data warehouse cluster when it is loaded and continuously backs it up to Amazon S3. Redshift can also automatically recover from node and component failures.

8. Concurrent Scaling: Amazon Redshift allows you to support virtually unlimited concurrent users and concurrent queries with Redshift Concurrency Scaling. Additional capacity can be added on-demand to handle bursts of query load.

In summary, Amazon Redshift provides a robust and highly scalable data warehouse solution for complex OLAP and BI queries on large datasets. Its cost-effectiveness, performance, and integration capabilities make it a powerful option for businesses of all sizes that rely on data-driven decision making.


## Amazon ElastiCache

**Amazon ElastiCache** is a fully managed, in-memory caching service provided by Amazon Web Services (AWS). It seamlessly integrates with other AWS services and provides a high-performance, scalable, and cost-effective caching layer for web applications, while removing the complexity associated with deploying and managing a distributed cache environment.

**ElastiCache supports two open-source in-memory caching engines**:

**Redis**: Redis is an open-source, in-memory data store that can function as a database, cache, and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, and more. Additionally, Redis provides features like transactions, pub/sub, Lua scripting, Keys with a limited time-to-live, and configuration settings to make certain commands atomic.

**Memcached**: Memcached is a high-performance, distributed memory caching system originally developed by Danga Interactive for LiveJournal, but now used by many other sites. It's simple yet powerful - its simple design promotes quick deployment, ease of development, and solves many problems facing large data caches.

**Key features of Amazon ElastiCache include**:

1. Ease of Setup: Amazon ElastiCache is easy to set up, manage, and scale in the AWS Management Console.

2. Performance: ElastiCache works as an in-memory cache, providing high-speed access to your data, minimizing latency compared to disk-based databases.

3. Scalability: You can start with a small cache and easily scale up to a larger one as your needs grow.

4. Compatibility: Since ElastiCache supports Redis and Memcached, applications that use these caching engines can switch to ElastiCache with little or no modifications.

5. High Availability and Durability: ElastiCache supports multi-AZ deployments, automatic failover, and backup capabilities to enhance the availability and durability of your data.

6. Security: ElastiCache provides several security features, including VPC support, encryption in-transit and at-rest, and integration with AWS Identity and Access Management (IAM).

7. Cost-effective: By leveraging ElastiCache, you can reduce the load on your databases and save on compute resources and I/O operations, leading to significant cost savings.

In summary, Amazon ElastiCache is a powerful solution for applications that require a high-performance, scalable, and cost-effective in-memory caching layer. Its support for popular caching engines like Redis and Memcached, combined with the ease of management, scalability, and security offered by AWS, makes it a popular choice for caching use cases.


## Amazon Neptune

**Amazon Neptune** is a fully managed graph database service provided by Amazon Web Services (AWS). It is optimized for processing complex graph queries, enabling users to easily build and run applications that work with highly connected datasets.

**Graph databases** are designed to store data that is best represented as a network, also known as a graph, where data points (nodes) are interconnected through relationships (edges). Common use cases include social networking, recommendation engines, fraud detection, knowledge graphs, life sciences, and network and IT operations.

**Here are the key features and aspects of Amazon Neptune**:

1. Fully Managed: Amazon Neptune is fully managed, which means AWS automatically handles the tasks associated with database management, including hardware provisioning, software patching, setup, configuration, and backups.

2. High Performance: Neptune is designed to deliver high performance querying, with the ability to execute millions of queries per second and automatically scale as your requests increase.

3. Graph Models: Amazon Neptune supports popular graph models Property Graph and W3C's RDF, and their respective query languages Apache TinkerPop Gremlin and SPARQL, allowing you to easily build queries that efficiently navigate highly connected datasets.

4. Scalability and Availability: Neptune is designed to offer high availability, automatically replicating six copies of your data across three Availability Zones and continuously backing up your data to Amazon S3. It also provides the ability to scale read capacity to millions of requests per second by adding up to 15 low latency read replicas.

5. Security: Amazon Neptune includes a number of security features such as network isolation using Amazon VPC, encryption at rest using AWS Key Management Service (KMS), and encryption in transit using TLS. On an encrypted Neptune instance, data in the underlying storage is encrypted, as are the automated backups, snapshots, and replicas in the same cluster.

6. Fully ACID Compliant: Amazon Neptune is fully ACID (Atomicity, Consistency, Isolation, Durability) compliant, ensuring reliable processing and a strong level of data integrity.

7. Fast and Reliable Backups: Neptune supports continuous backup to Amazon S3 and point-in-time recovery (PITR). This allows you to restore your database from a backup to any point in time within a configurable range, usually up to the last 35 days.

8. Integration with AWS Services: Amazon Neptune can be integrated with other AWS services, for instance, you can stream changes from Neptune to other AWS services with Neptune Streams.

In summary, Amazon Neptune is a powerful and flexible option for applications that need to work with highly connected data and complex queries. It provides a robust, scalable, and highly available infrastructure for graph-based data workloads.


## AWS Database Migration Service

**AWS Database Migration Service** (DMS) is a tool that allows you to migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database.

**Here are the key features and aspects of AWS Database Migration Service**:

1. Broad Support for Databases: AWS DMS supports both homogenous migrations (such as Oracle to Oracle) and heterogeneous migrations (such as Oracle to Amazon Aurora). It supports a wide range of source and target databases, including Oracle, Microsoft SQL Server, MySQL, MariaDB, PostgreSQL, SAP ASE, and MongoDB for sources, and these plus Amazon Aurora, Redshift, DynamoDB, and S3 for targets.

2. Minimal Downtime: AWS DMS uses a replication technology that allows it to copy data from the source to the target database without impacting the performance or up-time of the source system. This allows applications to remain operational during the migration process, greatly reducing the downtime associated with a database migration.

3. Continuous Data Replication: AWS DMS not only supports one-time migrations but can also continuously replicate data from the source to the target, which can be useful for applications that need to maintain synchronized data across different databases.

4. Schema Conversion Tool: In conjunction with AWS DMS, AWS also provides the AWS Schema Conversion Tool (SCT), which helps to convert the source database schema and a majority of the custom code, including views, stored procedures, and functions, to a format compatible with the target database.

5. Support for Large Databases: AWS DMS can handle terabytes of data, making it suitable for large database migrations.

6. Monitoring and Alerts: AWS DMS is integrated with Amazon CloudWatch, which allows you to monitor the progress of data replication tasks and provides alerts on the status of the migration. It also logs all the activities associated with the migration tasks.

7. Security: All network connections used by AWS DMS, including replication and administrative connections, are SSL-enabled, and all data transferred between the replication instance and the source and target endpoints is encrypted.

In summary, AWS Database Migration Service provides a convenient and effective way to migrate databases to AWS with minimal downtime, whether you're conducting a one-time migration or continuously replicating data. Its ability to support a wide range of databases and provide secure, real-time data replication makes it a popular choice for database migration projects.
