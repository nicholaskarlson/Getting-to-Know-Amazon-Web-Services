# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 12 - AWS Shared Responsibility Model


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


## AWS Shared Responsibility Model - Detail

**Let's consider a hypothetical software-as-a-service (SaaS) company**, **TechCo**, which plans to launch its new data analytics tool. The tool will be accessible via a web interface, and its primary audience includes businesses that want to get insights from their data, so security is paramount. TechCo has decided to use AWS as their cloud service provider, due to its scalability and range of services.

Under the AWS Shared Responsibility Model, both AWS and TechCo have distinct roles to play in ensuring the security and compliance of the application.

**Responsibilities of AWS**:

**Security "of" the Cloud**: AWS is responsible for protecting the infrastructure that runs all the services offered in the AWS Cloud, including hardware, software, networking, and facilities. This typically includes the foundational services TechCo plans to use, such as Amazon EC2 for compute, Amazon S3 for storage, and AWS databases like Amazon RDS.

In our scenario, AWS would be responsible for protecting the global infrastructure, maintaining the physical security of data centers, destroying data storage devices properly, ensuring the separation of customer data, and maintaining the availability of services through backup and disaster recovery measures.

**Responsibilities of TechCo**:

**Security "in" the Cloud**: TechCo is responsible for securing their specific use of AWS services, customer data, platform, applications, identity and access management, operating systems, network configuration, and client and server-side data encryption.

**Here's how TechCo could handle these responsibilities**:

Customer Data: TechCo would be responsible for determining what data to store and how to secure it. They might use AWS services like AWS Key Management Service (KMS) to manage cryptographic keys used to encrypt their data and Amazon Macie to identify and protect sensitive data.

Platform & Applications: TechCo would ensure that their applications are designed and coded securely. They might use AWS tools like AWS CodeStar for source code control, and AWS CodeDeploy for automated deployments.

Identity & Access Management: TechCo must manage who has access to their AWS resources and what they can do with them. This could involve using AWS Identity and Access Management (IAM) to manage users and their permissions, Amazon Cognito for user identity in their app, and AWS Multi-Factor Authentication (MFA) for an additional layer of security.

Operating System: For instances they launch on Amazon EC2, TechCo would be responsible for managing the guest operating system (including updates and security patches), any application software or utilities installed by them on the instances, and the security groups they configure.

Network Configuration: TechCo would need to set up appropriate firewall rules and other access controls for their resources, possibly using Amazon VPC for network segmentation, and AWS Shield and AWS WAF for protection against DDoS attacks and malicious web traffic respectively.

Through the effective application of the AWS Shared Responsibility Model, TechCo can ensure that their new data analytics tool is secure and compliant while being hosted on the AWS Cloud. This case highlights how the responsibilities for security and compliance are shared between AWS and the customer. TechCo can focus on securing their application, safe in the knowledge that AWS is taking care of the foundational security of the cloud.

**Let's now consider again the hypothetical company**, **RetailCo**, which operates a successful chain of retail stores and wants to create an e-commerce platform to sell its products online. RetailCo has chosen to use AWS to host its e-commerce platform due to its scalability and extensive range of services.

In this context, the AWS Shared Responsibility Model would apply as follows:

**Responsibilities of AWS**:

Security "of" the Cloud: AWS is responsible for protecting the infrastructure that runs all of the services offered in the AWS Cloud. This includes hardware, software, networking, and the physical facilities that run AWS services.

For RetailCo, AWS will handle the security of the core infrastructure and services, such as Amazon EC2 for compute resources, Amazon S3 for storage, and Amazon RDS for relational databases. This includes securing physical data centers, segregating customers' data, and ensuring the services are available and resilient to threats.

**Responsibilities of RetailCo**:

Security "in" the Cloud: RetailCo is responsible for anything they put on the cloud or connect to the cloud. This includes the security of customer data, managing AWS service configurations that they use, identity and access management, and client and server-side data encryption.

**Here's how RetailCo might manage these responsibilities**:

Customer Data: RetailCo is responsible for ensuring that their customer data is stored and handled securely. They can use AWS services like AWS Key Management Service (KMS) to manage encryption keys for their data and AWS Macie to identify and protect sensitive data.

Platform & Applications: RetailCo will ensure that their e-commerce platform is built and maintained securely. They may use AWS services such as AWS CodeStar for managing their source code, and AWS CodeDeploy for handling deployments.

Identity & Access Management: RetailCo needs to control who can access their AWS resources and what actions they can take. This could involve using AWS Identity and Access Management (IAM) to manage users and their permissions, and Amazon Cognito for handling user identity within their e-commerce platform.

Operating System: RetailCo is responsible for the security of the guest operating systems on their Amazon EC2 instances, including managing updates and security patches, any application software or utilities installed on the instances, and the configuration of their security groups.

Network Configuration: RetailCo should implement appropriate network configurations to secure access to their AWS resources. They might use Amazon VPC for network isolation, and services like AWS Shield and AWS WAF for protection against DDoS attacks and malicious web requests.

In applying the AWS Shared Responsibility Model, RetailCo can ensure the security and compliance of its e-commerce platform on AWS. The company can focus on securing their specific applications and data, while AWS handles the security of the cloud infrastructure.
