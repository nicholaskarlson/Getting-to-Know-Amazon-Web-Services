# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 11 - Well-Architected Framework


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


## AWS Well-Architected Framework - Detail

**Let's consider a growing online retail company**, "**RetailCo**", that has been experiencing a rapid increase in its user base. The company's existing infrastructure is no longer sufficient to handle the increased traffic, and they've begun experiencing site slowdowns and outages, particularly during peak times. This has led to customer dissatisfaction and loss of revenue. RetailCo has decided to migrate their web application to AWS to ensure scalability, reliability, and enhanced performance.

**Applying the AWS Well-Architected Framework**:

1. **Operational Excellence Pillar**:

First, RetailCo needs to focus on the Operational Excellence pillar, which involves running and monitoring systems to deliver business value and continually improving processes and procedures.

RetailCo can use services such as AWS CloudFormation to automate their infrastructure. They can also use AWS Systems Manager for operational insights and to take action on their AWS resources. They will use AWS CloudWatch and CloudTrail to monitor infrastructure and applications, getting system-wide visibility into resource utilization, and application performance.

To achieve continuous improvement, RetailCo will implement a culture of regular reviews and updates, using the learnings from AWS Trusted Advisor and AWS Well-Architected Tool to optimize their cloud usage. They will also put in place incident response protocols to ensure quick recovery and learning from any operational issues.

2. **Security Pillar**:

Security is critical for RetailCo, considering they handle customer data and transactions. They will leverage Amazon VPC for network segmentation, Amazon GuardDuty for threat detection, and AWS Shield for DDoS protection.

IAM roles and policies will be employed to follow the principle of least privilege and manage access to AWS services and resources securely. AWS Key Management Service (KMS) will be used to manage cryptographic keys for data encryption. AWS Certificate Manager will be used to easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services.

3. **Reliability Pillar**:

To ensure their application is reliable and available to their customers, RetailCo can utilize multiple Availability Zones within an AWS region. They will use Amazon RDS Multi-AZ deployment feature to automatically replicate databases for a failover support.

Amazon CloudFront coupled with AWS Route 53 will ensure that their global customers can access the site with low latency. AWS Auto Scaling will be used to maintain application availability and automatically add or remove Amazon EC2 instances according to conditions defined.

4. **Performance Efficiency Pillar**:

For Performance Efficiency, RetailCo will use services like AWS Auto Scaling and Amazon CloudFront to ensure that resources are being used efficiently. AWS Lambda will be used for serverless computing, allowing the company to run code without provisioning or managing servers.

RetailCo can also take advantage of various Amazon EC2 instance types, tailored to different workload types and optimized for different computing, memory, and storage needs. They can also use Amazon ElastiCache to improve the performance of web applications by retrieving information from fast, managed, in-memory caches, instead of relying solely on slower disk-based databases.

5. **Cost Optimization Pillar**:

For Cost Optimization, RetailCo will leverage AWS Cost Explorer and AWS Budgets to understand and manage their AWS costs and usage over time. They'll use AWS Trusted Advisor to access real-time guidance to provision resources following AWS best practices.

They will use different pricing models for Amazon EC2 instances like On-Demand Instances, Reserved Instances, and Spot Instances based on their workloads. They can also utilize services like AWS Fargate for running containers to avoid the need to manage the underlying EC2 instances, reducing operational overhead and cost.

The company can use S3 Intelligent-Tiering for automatic cost savings for data with unknown or changing access patterns in their S3 buckets.

**Application of Learnings**:

Once RetailCo has followed these steps, the organization should review their AWS Well-Architected Framework consistently to ensure it's achieving its goals. As the business evolves, their AWS environment should adapt to ensure it's meeting the five pillars: operational excellence, security, reliability, performance efficiency, and cost optimization.

For instance, as part of the continuous review under the Operational Excellence pillar, RetailCo might find that as they have grown, their original setup for incident management is no longer sufficient. They might need to implement AWS Chatbot to get alerts and run commands from Slack or Amazon Chime chat rooms to respond quickly to events.

**Architectural Best Practices**:

In addition to the Well-Architected Framework, RetailCo will also want to ensure it's following AWS architectural best practices, like decoupling their applications (using Amazon SQS or Amazon SNS), choosing the right database solution for the workload (e.g., Amazon RDS, DynamoDB), and leveraging serverless architectures where possible (like AWS Lambda or Amazon API Gateway).

**Conclusion**:

By diligently applying the AWS Well-Architected Framework to their migration and ongoing operations, RetailCo can ensure that their application is secure, reliable, cost-effective, and efficient, thereby providing a superior experience to their customers. Regular audits, proactive security, and performance management, and continuous optimization are key to getting the most value from AWS and achieving business objectives.

Finally, it's essential to remember that the AWS Well-Architected Framework isn't a one-time setup. It's an ongoing strategy that will evolve with the company's needs and technology advancements. Regular reviews, updates, and refinements are part of maintaining a well-architected AWS environment.
