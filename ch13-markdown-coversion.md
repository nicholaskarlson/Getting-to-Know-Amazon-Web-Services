# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 13 - AWS Architectural Principles


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


## AWS Architectural Principles - Detail

Let's consider a hypothetical company, MediaCo, which is a popular media streaming company with millions of users across the globe. They have a large, monolithic application hosted on their on-premises servers, which has been experiencing downtime due to heavy traffic during peak hours, affecting customer experience and causing loss of revenue.

They've decided to migrate to AWS to leverage its scalability, reliability, and cost-effectiveness. The migration and the subsequent operations will be guided by the AWS Architectural Principles, which are as follows:

1. Design for failure and nothing fails

While designing the AWS architecture, MediaCo keeps in mind that components may fail. To handle such scenarios, they use Amazon EC2 Auto Scaling to maintain application availability and automatically add or remove EC2 instances according to conditions defined. They deploy the application across multiple Availability Zones (AZs) for high availability and fault tolerance.

2. Implement elasticity

Given the nature of the media streaming business, user demand is variable. To handle the load during peak hours, MediaCo uses AWS Elastic Load Balancer to distribute incoming application traffic across multiple EC2 instances, in multiple AZs. They also implement Auto Scaling to automatically adjust the number of EC2 instances in response to traffic patterns and maintain a steady, predictable performance at the lowest possible cost.

3. Leverage different storage solutions

MediaCo uses Amazon S3 for storing and retrieving any amount of media data at any time, from anywhere. They use Amazon Glacier for archiving older media content not frequently accessed. For their databases, they use Amazon RDS for relational databases and Amazon DynamoDB for NoSQL databases.

4. Build security in every layer

Security is a top priority for MediaCo. They use Amazon VPC to create a private, isolated portion of the AWS cloud where they launch their resources in a secure environment. They also use AWS Identity and Access Management (IAM) to securely manage access to AWS services and resources. AWS Key Management Service (KMS) is used for creating and managing cryptographic keys and controlling their use across a wide range of AWS services and in their applications.

5. Think parallel

To speed up processing and improve the user experience, MediaCo designs their application to operate in a distributed, parallel manner wherever possible. For example, they distribute encoding jobs over multiple EC2 instances. They also leverage Amazon Elastic MapReduce (EMR) for processing huge amounts of data efficiently.

6. Don’t fear constraints

MediaCo leverages the AWS cloud to experiment with new ideas and technologies without huge upfront costs or long-term commitments. They don’t have to buy and maintain costly hardware for a service that may not be successful. This enables them to innovate more quickly.

7. Use serverless architectures

Wherever possible, MediaCo employs serverless architectures to eliminate the need to manage servers. They use AWS Lambda to run their code without provisioning or managing servers. They also use Amazon S3 for serverless storage, Amazon API Gateway for serverless APIs, and AWS Step Functions for serverless workflows.

8. Experiment often

With the ability to spin up and down resources quickly, MediaCo frequently experiments with different configurations, tests new features, and rolls out updates without affecting the entire application. They can learn from failures and continuously improve their services.

9. Automate to make architectural experimentation easier

MediaCo uses AWS CloudFormation to automate the deployment of their infrastructure. This makes it easy to replicate their infrastructure for testing or development purposes and helps reduce human errors.

In summary, by applying these AWS Architectural Principles, MediaCo successfully migrates their monolithic application to AWS, increasing their application's availability and reliability, improving customer experience, and reducing costs.

**Now let's revisit the hypothetical scenario of RetailCo and apply the AWS Architectural Principles to it:**

1. Design for failure

RetailCo creates a robust system that assumes hardware failures will occur and automatically heals when there are disruptions. They replicate their services across multiple Availability Zones to provide a higher level of availability and durability, ensuring the application can tolerate the failure of a single instance or even an entire Availability Zone.

2. Implement elasticity

Given the retail nature of RetailCo, the web traffic and customer demand may fluctuate significantly during sales events or holiday seasons. They utilize Amazon EC2 Auto Scaling to automatically adjust the number of instances in response to traffic patterns. They also employ Amazon RDS for its read replicas feature, allowing them to handle increased read traffic during peak times.

3. Leverage different storage options

RetailCo uses Amazon S3 for storing static assets like product images and downloadable content. For structured data storage like user profiles, orders, and product catalog, they use Amazon RDS. For caching and speeding up retrieval of frequently accessed data, they use Amazon ElastiCache.

4. Build security in every layer

RetailCo builds security at all layers from the edge network to the VPC, including using security groups and NACLs at the subnet and instance levels. They leverage AWS Identity and Access Management (IAM) to control user access and permissions. AWS Shield and AWS WAF are utilized to protect against DDoS and application layer attacks respectively.

5. Think parallel

RetailCo leverages AWS services like Lambda and SQS to process data concurrently, such as handling user requests or processing orders, to increase throughput and decrease latency.

6. Don’t fear constraints

RetailCo takes advantage of the scalability, speed, and agility of AWS to innovate and experiment without worrying about the limitations of their infrastructure. They can easily try new ideas and rollback if they don't work.

7. Use serverless architectures

RetailCo makes use of AWS Lambda and Amazon DynamoDB to create a serverless architecture for certain parts of their application, reducing the operational overhead of managing servers.

8. Experiment often

RetailCo frequently runs A/B testing on their services by easily duplicating their environment using AWS CloudFormation. They use Route53 for routing users to different versions of their service.

9. Automate to make architectural experimentation easier

RetailCo automates infrastructure setup using AWS CloudFormation, and uses AWS CodePipeline and AWS CodeDeploy for continuous integration and continuous delivery, ensuring rapid, consistent deployment of updates.

By following these AWS Architectural Principles, RetailCo is able to build a secure, resilient, efficient, and scalable e-commerce platform that provides an exceptional user experience while managing costs effectively.

**Note that A/B testing, also known as split testing, is a method of comparing two versions of a webpage or application against each other to determine which one performs better.** This technique is commonly used in website optimization, marketing campaigns, and user interface design. It can significantly improve a business's operational metrics, whether they're related to conversion rates, user engagement, or any other key performance indicators (KPIs).

In the context of RetailCo, let's take an example. Suppose RetailCo wants to test a new design for their product detail page, with the aim to increase the 'Add to Cart' conversion rate. They suspect that changing the color and position of the 'Add to Cart' button may influence user behavior. But before rolling out this new design to all customers, they want to ensure it actually improves conversions and doesn't negatively impact the user experience or any other metrics.

This is where A/B testing comes into play:

Version A, also called the control, would be the current design of the product detail page.

Version B, or the variant, would be the new design with the differently colored and positioned 'Add to Cart' button.

RetailCo would then split their website traffic so that half of their visitors see Version A, and the other half see Version B. This split can be random, or it can be controlled to ensure that each group is similar in terms of demographics, user behavior, or any other relevant factor.

Once a significant number of users have visited both versions of the page, RetailCo can analyze the data collected. They would examine the 'Add to Cart' conversion rate (or other metrics relevant to the test) for both versions. If Version B outperforms Version A, then RetailCo may decide to roll out the new design to all users. If not, they've gained valuable insights about user preferences without a full-scale rollout.

In RetailCo's case, AWS services like Route53 (for traffic routing) and CloudWatch (for data collection and monitoring) would be instrumental in facilitating these A/B tests. Furthermore, the ability to quickly duplicate and modify environments using services like AWS CloudFormation enables frequent and cost-effective testing, allowing RetailCo to continually optimize their user interface based on data-driven decisions.
