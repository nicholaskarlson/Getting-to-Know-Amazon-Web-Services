# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 4 - AWS Storage Services


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


## AWS Storage Services

AWS provides a variety of storage services, each with unique features and benefits, to handle different types of data and workload requirements. Understanding these services is crucial to architecting effective solutions in the AWS cloud.

**Amazon S3 **(Simple Storage Service): S3 is an object storage service that offers industry-leading scalability, data availability, security, and performance. It allows you to store and retrieve any amount of data at any time, from anywhere on the web. It is often used for backup and restore, archiving, content distribution, and data lake for big data analytics.

**Amazon EBS** (Elastic Block Store): EBS provides block-level storage volumes for use with EC2 instances. EBS volumes are network-attached, and persist independently from the life of an instance. It is suited for both throughput and transaction-intensive workloads of any size, like a database, that require single-digit millisecond latency.

**Amazon Glacier and Glacier Deep Archive**: These services provide low-cost storage for data archiving and long-term backup. They're designed for data that is accessed infrequently, with Glacier being more for active archives and Deep Archive for storing data that is accessed once or twice in a year.

**Amazon EFS** (Elastic File System): EFS provides a simple, scalable, fully-managed elastic NFS (Network File System) that can be used with AWS Cloud services and on-premises resources. It is often used for a wide variety of use cases such as home directories, application hosting, and content management.

**AWS Storage Gateway**: This is a hybrid storage service that enables your on-premises applications to seamlessly use AWS cloud storage. It provides three types of services: File Gateway for flat files, Volume Gateway for block-based storage, and Tape Gateway for backup.

**AWS Snow Family (Snowball, Snowmobile)**: These are data transfer services that use devices designed to move terabytes or even petabytes of data into and out of AWS. They are used when you have a large amount of data that can't be easily transferred over the internet due to costs, transfer times, or security reasons.

**Amazon FSx**: This service provides fully managed third-party file systems, with two offerings: FSx for Windows File Server for enterprise workloads and FSx for Lustre for high-performance workloads.

The choice of storage service depends on factors such as the type of data, frequency of access, speed of access needed, and costs. For example, frequently accessed data that requires fast access times might be stored on Amazon EBS or EFS, while infrequently accessed data could be stored more cost-effectively in Amazon S3 or Glacier.


# AWS Storage Services - Detail


## Amazon Simple Storage Service

**Amazon Simple Storage Service**, also known as Amazon S3, is an object storage service that offers industry-leading scalability, data availability, security, and performance. This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

**Here are key aspects of Amazon S3**:

1. **Storage Types**: Amazon S3 offers a range of storage classes designed for different use cases, including S3 Standard for general-purpose storage of frequently accessed data; S3 Intelligent-Tiering for data with unknown or changing access patterns; S3 Standard-IA and S3 One Zone-IA for long-lived, infrequently accessed data; and Amazon S3 Glacier and S3 Glacier Deep Archive for long-term archive and digital preservation.

2. **Durability and Availability**: Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data over multiple systems and facilities to make it more resilient. It also provides 99.99% availability of objects over a given year.

3. **Security**: Amazon S3 supports three different forms of encryption. It offers sophisticated integration with AWS CloudTrail to log, monitor, and retain storage API call activities for auditing, and supports three different forms of encryption. Amazon S3 also has robust capabilities to manage access control (using both ACLs and Bucket Policies), allowing administrators to create finely tuned access controls to specific objects or buckets.

4. **Scalability**: With Amazon S3, you can store as much data as you want and access it when needed. It can support both small websites as well as massively popular websites.

5. **Data Transfer**: Amazon S3 supports transferring data in and out via the internet, or directly into or out of S3 using AWS Direct Connect, which provides a dedicated network connection into AWS data centers.

6. **Management Features**: Amazon S3 comes with a suite of features to organize data and configure finely-tuned access controls to meet specific business, organizational, and compliance requirements.

7. **Query In-Place**: With Amazon S3 Select and S3 Glacier Select, you can use SQL to directly query your data in Amazon S3 or archive data in Amazon S3 Glacier, without having to retrieve all the data to perform filtering operations.

8. **Integration**: Amazon S3 integrates with a lot of AWS services like AWS CloudTrail, AWS CloudWatch, AWS Lambda, and Amazon Athena. You can configure these services to take action when certain events occur.

In summary, Amazon S3 is a highly flexible, secure, and durable storage service for the internet. It is designed to make web-scale computing easier and more cost-effective for developers. It provides a simple web services interface that can be used to store and retrieve any amount of data, at any time, from anywhere on the web.


## Amazon Elastic Block Store

**Amazon Elastic Block Store** (Amazon EBS) provides raw block-level storage that can be attached to Amazon EC2 instances. These block storage volumes can be used as primary storage for data that requires frequent updates, such as the system drive for an instance or storage for a database application. They can also be used for throughput-intensive and transaction-intensive workloads such as MongoDB, Cassandra, Microsoft SQL Server, MySQL, PostgreSQL, and Oracle databases.

**Here are the key aspects of Amazon EBS**:

1. **Durability and Availability**: Amazon EBS volumes are designed for high availability and durability. EBS volumes are automatically replicated within their Availability Zone to protect you from component failure, offering high durability and availability.

2. **Multiple Volume Types**: Amazon EBS provides a variety of volume types optimized for different performance characteristics:

**General Purpose SSD** (gp2 and gp3): This is a default volume type. GP SSD volume types deliver a cost-effective storage solution for a wide variety of workloads.

**Provisioned IOPS SSD** (io1 and io2): This volume type is best for I/O-intensive and latency-sensitive applications and databases.

**Throughput Optimized HDD** (st1): This volume type is designed for frequently accessed, throughput-intensive workloads and big data, data warehouses, and log processing.

**Cold HDD** (sc1): This volume type is ideal for less frequently accessed workloads.

**Magnetic **(Standard): This is a previous generation volume type and is recommended for infrequently accessed, sequential workloads.

3. **Scalability and Performance**: EBS volumes can be increased in size or performance (IOPS and throughput) without any downtime.

4. **Snapshots and Backup**: You can create point-in-time snapshots of EBS volumes, which are stored in Amazon S3, and can be used as the starting point for new EBS volumes or to protect data for long-term durability.

5. **Encryption**: Amazon EBS provides the ability to encrypt data at rest and in-transit. It uses AWS Key Management Service (KMS) keys when creating encrypted volumes and any snapshots created from your encrypted volumes are also encrypted.

6. **Access Control**: Access control policies can be defined using AWS Identity and Access Management (IAM) to control who can perform Amazon EBS actions.

In summary, Amazon EBS is a crucial component for many AWS-based applications. It offers durable and high-performing block-storage service designed for use with Amazon EC2 for both throughput and transaction-intensive workloads at any scale.


## Amazon Glacier and Glacier Deep Archive

**Amazon Glacier and Glacier Deep Archive** are **storage classes within Amazon Simple Storage Service** (S3) that are designed for long-term data archiving and backup. They are secure, durable, and extremely low-cost Amazon S3 storage classes for data archiving and long-term backup.

**Amazon S3 Glacier** provides three retrieval options to fit your use case. Expedited retrievals typically return data in 1-5 minutes, and are great for Active Archive use cases. Standard retrievals typically complete between 3-5 hours, and are suitable for less time-sensitive needs like backup data, media editing, or long-term analytics. Bulk retrievals are the lowest-cost retrieval option, returning large amounts of data within 5-12 hours.

**Amazon S3 Glacier Deep Archive** is Amazon S3's lowest-cost storage class and supports long-term retention and digital preservation for data that may be accessed once or twice in a year. It is designed for customers — particularly those in highly-regulated industries, such as the Financial Services, Healthcare, and Public Sectors — that retain data sets for 7-10 years or longer to meet regulatory compliance requirements. All objects stored in the S3 Glacier Deep Archive storage class have a minimum of 180 days of storage, and objects deleted before 180 days incur a prorated charge equal to the storage charge for the remaining days.

**Key aspects of Amazon Glacier and Glacier Deep Archive include**:

1. **Low-cost Storage**: Both Amazon S3 Glacier and Glacier Deep Archive offer the lowest cost storage in AWS, and are designed for rarely accessed data where a retrieval time of several hours is acceptable.

2. **Durability and Security**: Both storage classes offer the same 99.999999999% durability as other Amazon S3 storage classes. Data is also protected using 256-bit server-side encryption and offers flexible key management options.

3. **Data Retrieval**: With S3 Glacier, you can choose from three retrieval options — expedited, standard, or bulk retrievals — that range from a few minutes to hours. S3 Glacier Deep Archive provides two retrieval options that can restore data within 12 or 48 hours.

4. **Integration with Other AWS Services**: Both S3 Glacier and Glacier Deep Archive integrate with other AWS services like AWS CloudTrail, Amazon Macie, and S3 Event Notifications. This allows you to track and audit access requests, automatically discover and protect sensitive data, and automatically respond to certain changes to your data.

5. **Lifecycle Management**: You can define lifecycle rules to automatically transition objects between different Amazon S3 storage classes. For instance, you could define a rule that moves objects to S3 Glacier 30 days after creation, and then moves them again to S3 Glacier Deep Archive after 180 days.

In summary, both Amazon S3 Glacier and Glacier Deep Archive are essential services for organizations requiring long-term, secure data storage that meets regulatory or compliance needs. By leveraging these services, organizations can significantly reduce the cost of storing and maintaining large volumes of data over extended periods of time.


## Amazon Elastic File System

**Amazon Elastic File System** (Amazon EFS) is a cloud storage service provided by AWS for applications that require shared access to file-based storage. Amazon EFS provides a simple, scalable, fully managed elastic NFS (Network File System) that you can use with your AWS Cloud services and on-premises resources.

**Here are the key aspects of Amazon EFS**:

1. **Elastic and Scalable**: EFS is automatically scalable, and the storage capacity increases and decreases as you add and remove files. It can scale up to petabytes in size, and it can support thousands of concurrent NFS connections.

2. **Fully Managed**: Amazon EFS is a fully managed service, which means AWS handles the work of setting up and configuring the file system. It removes the complexity of deploying and managing complex file system infrastructures.

3. **Shared Access**: Amazon EFS supports the Network File System version 4 (NFSv4) protocol, so the applications and users can access a common data source. It allows multiple EC2 instances to access data at the same time, making it suitable for workloads that require concurrent read and write access by multiple EC2 instances.

4. **Durability and Availability**: Amazon EFS is designed to be highly durable and highly available. It automatically and transparently replicates your data across multiple Availability Zones in a region for high durability and availability.

5. **Integration**: Amazon EFS is integrated with other AWS services, such as Amazon EC2, Amazon ECS, AWS Lambda, and AWS DataSync. It can be accessed from on-premises systems via AWS Direct Connect or AWS VPN.

6. **Security**: EFS provides multiple levels of security for your sensitive data. It supports IAM for controlling access, VPC for network isolation, and it integrates with AWS Key Management Service (KMS). You can also use EFS access points to enforce a user identity, including the user’s POSIX (Portable Operating System Interface) group permissions.

7. **Performance Modes**: Amazon EFS offers two performance modes: general purpose and max I/O. General purpose mode is suitable for most applications, while max I/O can scale to higher levels of aggregate throughput and operations per second with a tradeoff of slightly higher latencies.

8. **Storage Tiers**: EFS offers two storage tiers: **EFS Standard** and **EFS Infrequent Access** (IA). EFS IA offers cost savings for files not accessed every day, and lifecycle policies can automatically move files between the two tiers based on access patterns.

In summary, Amazon EFS is an easy-to-use, scalable, and highly available solution for many applications and workloads that need shared access to file data. It's well-suited for use cases like content management, web serving, data analytics, and many others.


## AWS Storage Gateway

**AWS Storage Gateway** is a hybrid cloud storage service that gives you on-premises access to virtually unlimited cloud storage. The service provides a standard set of storage protocols (iSCSI, SMB, and NFS) and is optimized for securely transferring data to and from the AWS Cloud, maximizing transfer speeds and minimizing internet bandwidth usage.

**AWS Storage Gateway supports three configurations**, each serving different use cases:

1. **File Gateway**: This offers a seamless way to connect to the cloud in order to store application data files and backup images as durable objects on Amazon S3 cloud storage. It provides a file interface into S3, which means that your applications can store files and directories as objects in S3, and access data directly using file protocols (NFS and SMB).

2. **Volume Gateway**: It provides block storage to your applications using the iSCSI protocol. Data written to these volumes can be asynchronously backed up as point-in-time snapshots of your volumes and stored in the cloud as Amazon EBS snapshots. Volume Gateway comes in two modes:

**Stored Volumes**: In this mode, your entire dataset is stored on premises and is asynchronously backed up to AWS Cloud. This is ideal for applications needing low-latency access to their entire dataset.

**Cached Volumes**: In this mode, the frequently accessed data is cached on-premises while the full data is stored in AWS Cloud. This is best for substantial datasets where only a subset of data is needed on-premises for low-latency access.

3. **Tape Gateway**: It offers a durable, cost-effective solution to archive your data in the AWS Cloud. The Tape Gateway configuration of Storage Gateway is a cloud-based virtual tape library (VTL). It enables you to replace using physical tapes on-premises with virtual tapes in AWS.

**Here are key aspects of AWS Storage Gateway**:

1. **Easy Integration**: AWS Storage Gateway's seamless integration with existing applications via standard storage protocols means that applications don't need to be rewritten to benefit from AWS storage infrastructure.

2. **Secure**: Data transferred between the storage gateway and AWS storage is encrypted using SSL. For data at rest, the service integrates with AWS Key Management Service (KMS) for encryption.

3. **Cost-Effective**: The service can minimize data transfer by sending only changed data (compressing it where possible) to AWS, and caching frequently accessed data on your on-premises gateway.

4. **Durable and Available**: Data stored through AWS Storage Gateway benefits from the durability and availability provided by AWS services like S3, Glacier, and EBS.

5. **Easy Management**: AWS Storage Gateway is easy to manage. You can monitor and manage your gateways using the AWS Management Console, AWS CLI, or SDK.

In summary, AWS Storage Gateway is a critical service for implementing hybrid storage environments, which can help in the transition to the cloud, reducing on-premises storage needs, or satisfying regulatory requirements that need data to be available both on-site and off-site.


## AWS Snow Family (Snowball, Snowmobile)

**The AWS Snow Family** is a collection of physical devices and services offered by AWS to help customers with large-scale data transfers, edge computing, or situations where network connectivity is an issue. The Snow Family includes the AWS Snowcone, Snowball, and Snowmobile devices, which are physical storage devices designed to securely transport terabytes to exabytes of data into and out of the AWS cloud.

1. **AWS Snowball**: Snowball is a portable, ruggedized storage appliance designed to transfer large amounts of data into and out of AWS. With Snowball, you don't need to rely on a high-speed internet connection to move data; instead, you can simply transfer the data to a Snowball device, then ship that device back to AWS, where the data is imported into your S3 buckets.

**Snowball comes in two options**:

**Snowball**: Designed for large-scale data migrations and content distribution, each device can hold up to 80 TB of data.

**Snowball Edge**: This is an advanced version of the Snowball that, in addition to providing data transfer capabilities, also includes on-board storage and compute functionality. The device comes in two versions, Storage Optimized and Compute Optimized, providing 80 TB and 100 TB of capacity, respectively. It can run custom applications and AWS IoT Greengrass, allowing it to be used for local processing and edge-computing workloads.

2. **AWS Snowmobile**: For truly enormous amounts of data (up to 100 PB), AWS offers Snowmobile. Snowmobile is a secure, ruggedized 45-foot long shipping container, pulled by a semi-trailer truck, that can be used to move exabytes of data to AWS in a matter of weeks. Snowmobile makes it possible to transfer large amounts of data to the cloud, even in situations where network conditions would make it impractical to do so over the internet.

**Here are some key aspects of AWS Snow Family**:

1. **Security**: All data transferred using the Snow Family is automatically encrypted using 256-bit encryption. The devices are also tamper-resistant to ensure physical security during transit.

2. **Scalable**: The Snow Family offers a range of devices that can handle anything from a few terabytes to multiple petabytes of data, making it a scalable solution for offline data transfer.

3. **Edge Computing**: Snowball Edge devices come with onboard computing capabilities, allowing them to perform local processing on data. This is beneficial for use cases like data preprocessing, machine learning, and data analytics at the edge location.

4. **Integration with AWS Services**: Data transferred via Snow Family can be imported directly into various AWS Services like S3, EBS, or Glacier. It is also compatible with AWS IoT Greengrass and AWS Lambda.

In summary, the AWS Snow Family provides solutions to overcome challenges related to large-scale data transfer and edge computing, ensuring secure and efficient data migration to the AWS Cloud.


## Amazon FSx

**Amazon FSx** is a fully managed native file system service provided by AWS that makes it easy for you to launch and run feature-rich and highly-performant file systems with just a few clicks. As of my knowledge cutoff in September 2021, Amazon FSx provides two types of file systems: Amazon FSx for Windows File Server and Amazon FSx for Lustre.

1. **Amazon FSx for Windows File Server**: This is a fully managed native Microsoft Windows file system built on Windows Server. It provides a fully compatible, shared file storage that comes with the compatibility, features, and performance that your Windows-based applications rely on.

It is ideal for enterprise applications, home directories, and any other use cases that require Windows shared file storage. FSx for Windows supports the SMB protocol, NTFS, and Active Directory (AD) integration.

2. **Amazon FSx for Lustre**: Lustre is a popular open-source parallel file system for processing large-scale, high-performance computing (HPC) workloads. FSx for Lustre is fully managed, making it easy to set up, scale, and manage Lustre file systems.

FSx for Lustre is integrated with S3, which means you can link your S3 buckets to your Lustre file system, import data from S3 to process, and then export back to S3. It's suitable for machine learning, high-performance computing, video processing, financial modeling, and electronic design automation.

**Key aspects of Amazon FSx include**:

1. **Fully Managed**: Amazon FSx automatically handles the time-consuming administrative tasks such as hardware provisioning, software configuration, patching, and backups.

2. **Compatibility**: Amazon FSx provides a fully native environment, meaning that the applications and tools that you already use with your existing file systems will work seamlessly.

3. **Performance**: Amazon FSx provides fast, predictable performance (with SSD storage) to meet the needs of the most demanding workloads.

4. **Security**: Amazon FSx offers multiple layers of security and compliance capabilities. Data is encrypted at rest and in transit. It supports Windows and AWS security best practices and compliance certifications.

5. **Integration**: Amazon FSx integrates with other AWS services, making it easier to run your applications in the AWS Cloud. For example, Amazon FSx for Lustre works natively with Amazon S3, allowing you to process cloud data sets with the high-performance file system.

In summary, Amazon FSx offers fully managed file storage solutions that support a wide array of workloads. These are optimized for different use-cases, from Windows-based applications to compute-intensive workloads that require high-performance file systems like Lustre.
