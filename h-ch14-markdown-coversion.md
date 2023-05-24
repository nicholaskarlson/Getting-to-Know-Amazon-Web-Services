# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 14 - Summary

Some knowledge regarding AWS cloud architecture, core services, security, and pricing. 

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


## AWS Global Infrastructure

AWS Global Infrastructure is a critical concept to understand for anyone involved with cloud computing and interested in AWS.

At the highest level, the AWS Global Infrastructure is composed of Regions and Availability Zones. As of September 2021, AWS spans 77 Availability Zones within 24 geographic regions around the world, with announced plans for more Availability Zones and Regions.

Let's discuss each component in more detail:

**Regions**: A region is a physical location in the world where AWS clusters data centers. Each AWS Region is a separate geographic area, such as North Virginia, London, Sydney, etc. Regions are designed to be completely isolated from each other, to achieve the greatest possible fault tolerance and stability. They provide a way for you to deploy your applications and data across the globe, thereby enabling you to serve your users with lower latency and a better experience.

**Availability Zones** (AZs): Each Region has multiple AZs. An Availability Zone is essentially one or more data centers, each with redundant power, networking, and cooling. They are located in different areas within a region and are designed to be insulated from failures in other AZs, to ensure high availability and provide reliable services.

**Edge Locations**: In addition to Regions and AZs, AWS also has many more Edge Locations. These are sites that AWS uses to cache data for distribution via the AWS Content Delivery Network (CDN), known as Amazon CloudFront, to deliver content to users more quickly. They are located in most of the major cities around the world and are separate from Regions and AZs.

**Local Zones**: These are a type of infrastructure deployment that places AWS compute, storage, database, and other select services closer to large population, industry, and IT centers where no AWS Region exists. They offer ultra-low latency to end-users in geographic areas that are far from existing AWS Regions.

**Wavelength Zones**: These are AWS infrastructure deployments that embed AWS compute and storage services within communications service providers' datacenters at the edge of the 5G network, so application traffic can reach application servers running in Wavelength Zones without leaving the telecommunications network.

Understanding AWS's global infrastructure is essential as it allows businesses to design resilient, high-performing, secure, and cost-effective applications. It also helps customers to comply with data sovereignty requirements by keeping their data within a specific geographic region.


## AWS Compute Services

AWS Compute Services are the backbone of many applications running on Amazon Web Services. They offer a range of services suitable for different workloads and requirements. Here are the key services:

**Amazon EC2** (Elastic Compute Cloud): EC2 is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale computing easier by providing a simple web service interface that allows you to obtain and configure capacity with minimal friction. EC2 offers a variety of instance types optimized to fit different use cases, such as memory-optimized, compute-optimized, and storage-optimized instances.

**AWS Lambda**: This service lets you run your code without provisioning or managing servers. You just upload your code, and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app. This is an example of "Function as a Service" or FaaS, and is used for serverless computing.

**AWS Elastic Beanstalk**: is a fully managed service offered by Amazon Web Services that makes it easy for developers to deploy and run applications in multiple languages. These include applications written in Java, .NET, PHP, Node.js, Python, Ruby, and Go, or in custom runtime environments using Docker. Elastic Beanstalk supports applications developed in a range of familiar servers, including Apache, Nginx, Passenger, and IIS.

The central idea behind Elastic Beanstalk is that you can focus on your application while AWS handles the infrastructure setup, scaling, and administration.

**Amazon ECS** (Elastic Container Service): Amazon ECS is a highly scalable, high-performance container orchestration service that supports Docker containers and allows you to run applications on a managed cluster of Amazon EC2 instances. ECS eliminates the need for you to install, operate, and scale your own cluster management infrastructure.

**Amazon EKS** (Elastic Kubernetes Service): Amazon EKS is a managed service that makes it easy for you to run Kubernetes on AWS without needing to install and operate your own Kubernetes control plane or nodes. Kubernetes is a popular open-source system for automating the deployment, scaling, and management of containerized applications.

**AWS Fargate**: Fargate is a compute engine for Amazon ECS and EKS that allows you to run containers without having to manage the underlying EC2 instances. With Fargate, you can focus on designing and building your applications instead of managing the infrastructure that runs them.

**AWS Batch**: This is a set of batch computing services. It efficiently plans, schedules, and executes your batch computing workloads across the full range of AWS compute services and features, such as EC2 and Spot Instances.

**Amazon Lightsail**: Lightsail provides virtual private servers (instances). It's designed to be the easiest way to launch and manage a virtual private server with AWS. It includes everything you need for a project, such as a virtual machine, SSD-based storage, data transfer, DNS management, and a static IP, for a low, predictable price.

Each of these services is designed for different workloads and use cases. For example, you might use EC2 for an application requiring a great deal of custom configuration, while Lambda might be a better fit for a microservices architecture. Understanding these services is crucial for using AWS effectively.


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


## AWS Networking & Content Delivery

AWS offers several services focused on networking and content delivery to ensure secure and efficient communication within your applications and with end-users. Here are the main ones:

**Amazon VPC** (Virtual Private Cloud): Amazon VPC lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways.

**Amazon Route 53**: This is a highly available and scalable cloud Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost-effective way to route end users to Internet applications by translating names into the numeric IP addresses that computers use to connect to each other.

**Amazon CloudFront**: CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment. It integrates with other AWS services to give developers and businesses an easy way to accelerate content to end users.

**AWS Direct Connect**: This makes it easy to establish a dedicated network connection from your premises to AWS. Using AWS Direct Connect, you can establish private connectivity between AWS and your datacenter, office, or colocation environment, which can reduce network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections.

**Elastic Load Balancing** (ELB): ELB automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions. It can handle the varying load of your application traffic in a single Availability Zone or across multiple Availability Zones.

**Amazon API Gateway**: This is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. It handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including traffic management, authorization and access control, monitoring, and API version management.

**AWS Transit Gateway**: This is a service that enables customers to connect their Amazon Virtual Private Clouds (VPCs) and their on-premises networks to a single gateway. It simplifies network architecture, reduces operational overhead, and offers the potential for significant cost savings.

**AWS Global Accelerator**: This improves the availability and performance of your applications for local and global users. It uses the AWS global network to optimize the path from your users to your applications, improving the performance of your TCP and UDP traffic.

**AWS App Mesh**: This is a service mesh that provides application-level networking to make it easy for your services to communicate with each other across multiple types of compute infrastructure.

These services collectively enable a secure and efficient network architecture in the AWS environment. They provide control and customization, enabling your application to deliver content and services quickly and securely.


## AWS Security, Identity & Compliance

Security is a top priority for AWS, and the platform provides a wide range of services and features designed to help you protect your data, accounts, and workloads. Below are the primary AWS services related to security, identity, and compliance:

**AWS Identity and Access Management** (IAM): IAM allows you to manage access to AWS services and resources securely. You can create and manage AWS users and groups and use permissions to allow and deny their access to AWS resources. It also allows for role-based access control, letting you dictate who can access what resources.

**Amazon Cognito**: Cognito provides authentication, authorization, and user management for your web and mobile apps. Users can sign in directly with a username and password, or through a third party such as Facebook, Amazon, or Google.

**AWS Key Management Service** (KMS): This is a managed service that makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications.

**Amazon Macie**: Macie is a security service that uses machine learning to automatically discover, classify, and protect sensitive data like Personally Identifiable Information (PII). It provides you with dashboards and alerts that give visibility into how this data is being accessed or moved.

**Amazon GuardDuty**: GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts, workloads, and data stored in Amazon S3.

**AWS Security Hub**: Security Hub gives you a comprehensive view of your security posture across your AWS accounts. It aggregates, organizes, and prioritizes your security alerts, or findings, from multiple AWS services and partner solutions.

**AWS Secrets Manager**: This service helps you protect access to your applications, services, and IT resources. It enables you to easily rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle.

**AWS Inspector**: Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS. It assesses applications for vulnerabilities or deviations from best practices, including impacted networks, OS, and attached storage.

**Amazon Detective**: This service makes it easy to analyze, investigate, and quickly identify the root cause of security findings or suspicious activities.

**AWS Single Sign-On** (SSO): This makes it easy to centrally manage SSO access to multiple AWS accounts and business applications. It provides users with a single user portal for all their applications and AWS accounts.

**AWS Certificate Manager**: This service handles the complexity of creating, storing, and renewing public and private SSL/TLS X.509 certificates and keys that protect your AWS websites and applications.

These services work in conjunction to help you establish a secure and compliant AWS environment. They support you in managing access, protecting data, monitoring activity, and maintaining regulatory compliance. AWS also complies with a wide array of global security standards, making it easier for you to meet your own compliance requirements.


## AWS Management Tools

AWS provides several services and tools that help users to manage and automate their resources in the AWS environment. These management tools assist with resource organization, task automation, system monitoring, configuration management, and operational insight.

Here are the primary AWS Management Tools:

**AWS Management Console**: This is a web application for managing Amazon Web Services. The console provides an intuitive user interface for performing many AWS tasks like working with Amazon S3 buckets, launching and connecting to Amazon EC2 instances, setting Amazon CloudWatch alarms, and more.

**AWS CloudFormation**: CloudFormation provides a common language for you to model and provision AWS and third-party application resources in your cloud environment. It allows you to use programming languages or a simple text file to model and provision, in an automated and secure manner, all the resources needed for your applications across all regions and accounts.

**AWS CloudTrail**: CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account. It allows you to log, continuously monitor, and retain account activity related to actions across your AWS infrastructure.

**AWS Config**: This is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. It continuously monitors and records your AWS resource configurations and allows you to automate the evaluation of recorded configurations against desired configurations.

**Amazon CloudWatch**: CloudWatch is a monitoring and observability service built for DevOps engineers, developers, site reliability engineers (SREs), and IT managers. It provides data and actionable insights to monitor your applications, understand and respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health.

**AWS Systems Manager**: Systems Manager gives you visibility and control of your infrastructure on AWS. It provides a unified user interface so you can view operational data from multiple AWS services and automate operational tasks across your AWS resources.

**AWS Auto Scaling**: This monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. It can be used to scale multiple resources across multiple services, and improve your applications’ availability and cost effectiveness.

**AWS OpsWorks**: OpsWorks is a configuration management service that provides managed instances of Chef and Puppet, which are automation platforms that allow you to use code to automate the configurations of your servers.

**AWS Service Catalog**: This allows organizations to create and manage catalogs of IT services that are approved for use on AWS. It helps you achieve consistent governance and meet your compliance requirements, while enabling users to quickly deploy only the approved IT services they need.

**AWS Control Tower**: Control Tower sets up and governs a new, secure multi-account AWS environment based on best practices established through AWS’ experience working with thousands of enterprises as they move to the cloud.

**AWS Trusted Advisor**: This provides real-time guidance to help you provision your resources following AWS best practices. It provides insights into cost optimization, security, fault tolerance, service limits, and performance improvement.

These tools are designed to help you with resource provisioning, configuration management, operational monitoring, event-driven automation, and much more, thereby simplifying overall management and governance across your AWS environment.


## AWS Application Integration

Application integration in AWS involves the use of various services that enable different software applications, often running in different environments, to work together seamlessly. These AWS services facilitate the exchange of data and processes among different applications and systems, both on-premises and in the cloud. Here are the key AWS Application Integration services:

**AWS Step Functions**: AWS Step Functions is a serverless workflow service that lets you coordinate distributed applications using visual workflows. It allows you to design and run workflows that stitch together services like AWS Lambda, AWS Fargate, and Amazon SageMaker into feature-rich applications.

**Amazon Simple Notification Service** (SNS): SNS is a fully managed pub/sub messaging service that allows you to decouple microservices, distributed systems, and serverless applications. SNS provides topics for high-throughput, push-based, many-to-many messaging.

**Amazon Simple Queue Service** (SQS): SQS is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. SQS eliminates the complexity and overhead associated with managing and operating message oriented middleware, and empowers developers to focus on differentiating work.

**Amazon AppFlow**: Amazon AppFlow is a fully managed integration service that enables you to securely transfer data between Software-as-a-Service (SaaS) applications like Salesforce, Marketo, Slack, and ServiceNow, and AWS services like Amazon S3 and Amazon Redshift, in just a few clicks.

**Amazon EventBridge**: EventBridge is a serverless event bus service that makes it easy to connect your applications with data from a variety of sources. You can build powerful event-driven applications with a variety of AWS resources and SaaS applications, and respond to operational changes in your environment.

**AWS Lambda**: Though not strictly an integration service, Lambda often plays a key role in application integration in AWS. It lets you run your code without provisioning or managing servers. You can use AWS Lambda to execute your back-end application code in response to events, such as changes to data in an Amazon S3 bucket, updates to a DynamoDB table, custom events generated by your applications, etc.

**Amazon MQ**: Amazon MQ is a managed message broker service for Apache ActiveMQ and RabbitMQ that makes it easy to set up and operate message brokers in the cloud. Message brokers allow different software systems to communicate and exchange information.

These services can be used individually or in combination, depending on your specific integration needs. For instance, you might use SQS and SNS together to decouple and scale microservices, distributed systems, and serverless applications. Or, you could use Lambda and EventBridge to respond to system-wide operational changes. By leveraging these application integration services, you can create scalable, serverless, event-driven applications and workflows.


## AWS Pricing and Cost Management

Understanding AWS Pricing and Cost Management is crucial for effectively using AWS services while controlling costs. Here are the main concepts related to this topic:

1. **Pay-as-you-go pricing**: AWS primarily follows a pay-as-you-go approach to pricing. You only pay for the individual services you need, for as long as you use them, without requiring long-term contracts or complex licensing.

2.** Savings Plans**: This is a flexible pricing model that provides significant savings on AWS usage. AWS Savings Plans offer lower prices on Amazon EC2 instances usage, regardless of instance family, size, OS, tenancy or AWS Region, and also apply to AWS Fargate and AWS Lambda usage.

3. **Reserved Instances** (RIs): Reserved Instances provide a significant discount (up to 75%) compared to On-Demand instance pricing and provide a capacity reservation when used in a specific Availability Zone.

4. **Spot Instances**: Spot Instances allow you to request unused EC2 instances at steep discounts — up to 90% compared to On-Demand prices. Spot Instances are recommended for applications that have flexible start and end times, or that can withstand interruptions.

5. **AWS Cost Explorer**: Cost Explorer is a tool that enables you to visualize, understand, and manage your AWS costs and usage over time. You can explore your cost data at a high level (e.g., total costs and usage across all accounts) or for highly specific requests.

6. **AWS Budgets**: AWS Budgets allows you to set custom cost and usage budgets that alert you when your costs or usage exceed (or are forecasted to exceed) your budgeted amount.

7. **AWS Cost and Usage Report** (CUR): The AWS Cost and Usage Report lists AWS usage for each service category used by an account and its IAM users in hourly or daily line items, as well as any tags that you have activated for cost allocation purposes.

8. **AWS Trusted Advisor**: This tool provides real-time guidance to help you provision your resources following AWS best practices, including cost optimization.

9. **AWS Pricing Calculator**: The AWS Pricing Calculator lets you explore AWS services, and create an estimate for the cost of your use cases on AWS.

Each AWS service might have a different pricing model based on a variety of factors. The factors can include the number of requests, the duration of usage, data transfer, storage needs, or even the features used within a service. For this reason, it's crucial to understand the specifics of pricing for any AWS services you plan to use.

Lastly, always consider data transfer costs. Transferring data between AWS services in different regions, or transferring data out of AWS entirely, may incur costs. These costs can be a common oversight, and they can add up over time, especially for data-intensive applications.


## AWS Well-Architected Framework

The AWS Well-Architected Framework is a set of guidelines and best practices for building and deploying systems and applications on AWS. It provides a consistent approach to evaluating systems against the quality attributes of high-performing, resilient, and efficient cloud infrastructure.

The framework is built on five key pillars:

**Operational Excellence**: This pillar focuses on running and monitoring systems to deliver business value, and continually improving processes and procedures. Key topics include managing and automating changes, responding to events, and defining standards to manage daily operations.

**Security**: The Security pillar focuses on protecting information & systems. Key topics include confidentiality and integrity of data, identifying and managing who can do what with privilege management, protecting systems, and establishing controls to detect security events.

**Reliability**: This pillar emphasizes the ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues.

**Performance Efficiency**: This pillar focuses on using IT and computing resources efficiently. Key topics include selecting the right resource types and sizes based on workload requirements, monitoring performance, and making informed decisions to maintain efficiency as business needs evolve.

**Cost Optimization**: The final pillar focuses on avoiding unnecessary costs. Key topics include understanding and controlling where money is being spent, selecting the most appropriate and right number of resource types, analyzing spend over time, and scaling to meet business needs without overspending.

Each pillar has a set of design principles and best practices, and is associated with a number of questions that help guide the architectural review of your workloads.

The AWS Well-Architected Framework also includes a tool, the **AWS Well-Architected Tool** (AWS WA Tool), that helps you review the state of your workloads and compares them to the latest AWS architectural best practices. The AWS WA Tool provides recommendations for making your workloads more reliable, secure, efficient, and cost-effective.

The AWS Well-Architected Framework is designed to help you build secure, high-performing, resilient, and efficient infrastructure for your applications and workloads. Using this framework will help you make informed decisions about your architecture in a consistent, proactive manner, and guide you towards architectural best practices.


## AWS Shared Responsibility Model

The AWS Shared Responsibility Model is a security model that delineates the security responsibilities of AWS (the cloud service provider) and the customer to ensure the complete and effective security of the system. Understanding this model is critical to ensuring the appropriate security measures are in place for workloads running in AWS.

In this model:

AWS is responsible for "**security of the cloud**". This includes all the components from the host operating system and virtualization layer down to the physical security of the facilities in which these services operate. This covers aspects such as:



* **Infrastructure** (hardware, software, networking, and facilities)
* **Compute, storage, database, and networking services**
* **Security features and service capabilities that AWS provides and configures**
* **Patching and fixing flaws within the infrastructure, and responding to incidents of security violation**

The customer is responsible for "**security in the cloud**". Customers control and manage the security components from the guest operating system (including updates and security patches) to the applications running on top of that. Depending on the AWS services being used, customer responsibility will be determined. The customer's responsibilities can include:



* **Data encryption** (at rest and in transit)
* **Network traffic protection**
* **Operating system and application security patch updates**
* **Firewall configurations**
* **Identity and access management**, including managing AWS service security credentials and defining individual user accounts with permissions
* **Ensuring compliance with industry-specific regulations and standards**

The shared responsibility model aims to reduce the customer's operational burden in many ways, and in some cases, improves the level of security compared to what a customer could achieve in an on-premises environment. However, it's critical for customers to understand their role in this model and ensure they are carrying out their responsibilities to secure their workloads in the AWS environment. This shared model helps relieve the customer’s operational burden as AWS operates, manages and controls the components from the host operating system and virtualization layer down to the physical security of the facilities in which the service operates.


## AWS Architectural Principles

When designing systems on AWS, a number of key principles guide the architectural decisions to ensure efficient, reliable, secure, and cost-effective operations. Here are some of the fundamental AWS architectural principles:

**Design for failure and nothing will fail**: AWS encourages the assumption that every component can fail, and hence, systems should be designed to be resilient to these failures. This involves a combination of strategies, including redundancy, replication, and regular backups.

**Decouple your components**: Decoupling components reduces interdependencies, which can help improve system scalability and reduce the impact of any component failure. Services like AWS SQS and SNS can be used to build loosely coupled, distributed systems.

**Implement elasticity**: Elasticity is the ability to easily scale out or scale in your resources to meet demand. AWS Auto Scaling and on-demand capabilities of resources help to optimize costs and improve the ability to handle peaks in demand.

**Secure your application**: AWS provides several security capabilities and services to increase privacy and control network access. Utilize these tools, and follow best practices like least privilege access, encrypting data at rest and in transit, and enabling logging and monitoring.

**Think parallel**: The cloud allows for the processing of tasks in parallel. This can reduce the time required to process large amounts of data, and makes for highly scalable systems. Services like Amazon Elastic MapReduce (EMR) or AWS Batch allow for parallel processing.

**Leverage different storage options**: AWS provides several storage options, each with its own characteristics. Choose the right type of storage (Amazon S3, EBS, EFS, Glacier, etc.) based on factors like access speed, whether data needs to be object-based or block-based, and cost.

**Use serverless architectures**: Serverless architectures remove the need for you to manage servers and allow you to focus purely on product development. AWS provides several serverless services, including AWS Lambda, Amazon API Gateway, and Amazon DynamoDB.

**Automate where possible**: AWS encourages automation of your resources and systems to help achieve consistency, reduce errors, and save time. AWS provides several tools for automation including AWS CloudFormation, AWS OpsWorks, and AWS CodePipeline.

**Optimize for cost**: AWS provides several pricing options, including on-demand, reserved, and spot instances. Using these in the right combination can lead to significant cost savings.

These principles and the practices associated with them can guide you in designing, deploying, and managing your applications and workloads in the AWS Cloud effectively and efficiently.
