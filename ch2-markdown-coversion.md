# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 2 - AWS Global Infrastructure


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


## AWS Global Infrastructure - Detail

**AWS Regions** represent distinct geographical areas around the world where AWS has clusters of data centers. Each region is a separate geographic area and is designed to be isolated from the other AWS regions to achieve the greatest possible fault tolerance and stability. This design helps ensure that applications remain available and operational, even in the event of a catastrophic event affecting an entire region.

**Key aspects of AWS Regions include**:

**Isolation**: Each AWS Region is physically isolated from and independent of every other AWS Region to provide the highest possible fault tolerance and stability. They have separate power grids and networking to reduce shared points of failures.

**Consistency**: Every AWS Region (except the AWS GovCloud Regions and China Regions) has at least three Availability Zones (AZs), which are multiple, isolated data centers within a region. This consistent approach across most regions helps you design and operate applications that meet high availability, fault tolerance, and scalability needs.

**Data Sovereignty**: Because data is not automatically replicated between regions, customers can control where their data is stored and serve their end-users with lower latencies. This is particularly important for compliance with data protection laws and regulations in many countries and industries.

**Selection**: As of September 2021, AWS has 25 geographic regions around the world, including in the Americas, Asia Pacific, Europe, Middle East, and Africa. AWS continues to expand its services globally to help meet customers' needs.

**Pricing**: Pricing for AWS services can vary by region, reflecting the cost of doing business in the various geographic locations. This means that the costs associated with running a workload in one region may be different from the costs in another region.

**Services Availability**: Not all AWS services are available in every region. Typically, new services or features are rolled out gradually across regions, starting with North Virginia (us-east-1).

When selecting a region, you should consider factors like data sovereignty and compliance requirements, latency to end users, service availability, and pricing. You can choose the region that best meets your needs.


## AWS Availability Zones

**Availability Zones** (AZs) are one of the key components of AWS infrastructure and are crucial for building reliable and scalable applications. Here are the main points about AWS Availability Zones:

1. **Definition**:** Availability Zones are essentially data centers**. Each AZ is a distinct location within a region that is insulated from failures in other AZs.

2. **Redundancy and Fault Tolerance**: Every AWS Region has at least three AZs for redundancy and fault tolerance. Each AZ is designed with power, cooling, physical security, and network connectivity to offer high reliability. They are physically separated by a meaningful distance, many kilometers, from any other AZ, to reduce risk of simultaneous failure, yet linked with fast, private fiber-optic networking to allow rapid failover between AZs.

3. **Resource Distribution**: When you launch instances or create other resources in a region, you can specify the AZ or let AWS select an AZ on your behalf. Distributing your instances across multiple AZs provides the ability to remain resilient in the face of most failure modes, including outages.

4. **High Availability and Failover**: By taking advantage of multiple AZs, you can design and operate applications and databases that automatically failover between AZs without interrupting the functions of your applications. So, if one AZ experiences an outage, your application can continue to run from another AZ.

5. **Scalability**: You can use AZs to scale your applications and databases, meeting the needs of more demanding workloads and ensuring smoother user experiences.

6. **Data Replication**: Services like Amazon RDS (Relational Database Service) and Amazon S3 (Simple Storage Service) can automatically replicate data across AZs to ensure robustness and data durability.

7. **Pricing**: Data transfer between the same AWS service in different AZs in the same region incurs charges. But transfer between services within the same AZ, using private IP addresses, does not have any cost.

Using AWS Availability Zones allows you to build highly available, fault-tolerant applications, satisfying the requirements of the most demanding workloads. It's a good practice to distribute applications and data across multiple AZs in a region to achieve high availability and reliability.


## AWS Edge Locations

AWS Edge Locations are sites that AWS uses to cache data to reduce latency for end users. These locations are mainly used by Amazon CloudFront, a content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds.

Here are the key points you need to know about AWS Edge Locations:

1. **Definition and Function**: AWS Edge Locations are sites deployed in major cities and highly populated areas across the globe, separate from AWS Regions and Availability Zones. They are used to deliver content to end users with reduced latency. When a user requests content, the request is automatically routed to the nearest edge location, so content delivery is done with the best possible performance.

2. **Relationship with CloudFront**: CloudFront uses a global network of edge locations to cache copies of content closer to users. When a user requests content that's hosted on AWS, the request is routed to the edge location that provides the lowest latency.

3. **Number of Edge Locations**: As of September 2021, AWS has over 200 edge locations across the world, and this number is continually growing.

4. **Regional Edge Caches**: In addition to edge locations, AWS has regional edge caches, which are slightly larger cache locations situated between AWS's edge locations and the origin servers (which are the source of the content, often located in an AWS Region). Regional edge caches help keep more popular content closer to end users without contacting the origin servers, improving performance and reducing the load on origin servers.

5. **AWS Services Using Edge Locations**: In addition to CloudFront, other AWS services that make use of edge locations include Amazon Route 53 (DNS service), AWS Shield (DDoS protection), AWS WAF (web application firewall), and AWS Lambda@Edge (run AWS Lambda functions at AWS locations closest to the user).

6. **Data Privacy**: Edge locations adhere to the same stringent AWS security standards as AWS Regions and Availability Zones. Also, objects are only cached at edge locations for a specified duration, reducing the risk of data being left at these sites.

Edge locations are a crucial part of AWS's infrastructure, and they play a critical role in providing lower latency and a better user experience for AWS customers around the globe.


## AWS Local Zones

AWS Local Zones are a type of AWS infrastructure deployment that places AWS compute, storage, database, and other services closer to large population, industry, and IT centers. They are built to provide users with the ability to run applications that require single-digit millisecond latencies to end-users in a specific geographic area.

**Key points about AWS Local Zones include**:

1. **Location and Purpose**: Local Zones are essentially an extension of an AWS Region where you can run latency-sensitive applications closer to end-users. They are ideal for applications that need real-time, interactive user experiences, like video gaming, media & entertainment content creation, live video streaming, AR/VR, machine learning, and others.

2. **Service Availability**: You can use a variety of services in AWS Local Zones including Amazon Elastic Compute Cloud (Amazon EC2), Amazon Virtual Private Cloud (VPC), Amazon Elastic Block Store (EBS), Amazon FSx, and Amazon Elastic Load Balancer (ELB), and more.

3. **Data Transfer and Latency**: Applications in the Local Zone can securely access the full range of AWS services in the parent region using VPC peering, AWS PrivateLink, AWS Direct Connect, and AWS VPN. This can help you to further reduce data transfer costs or address regulatory requirements while providing a consistent hybrid experience.

4. **High Availability and Fault Tolerance**: You can design and architect applications that run in Local Zones to increase availability and fault tolerance. For example, you can spread your instances across multiple Local Zones in a region to protect your applications from the rare event of a Local Zone being isolated.

5. **Pricing**: AWS services running in Local Zones are priced the same as in the parent AWS Region.

As of September 2021, AWS started rolling out Local Zones starting with Los Angeles in the US, and continued adding more Local Zones in major cities around the world. Local Zones can help you to deliver applications that require low latency to a specific geographic area by providing a selection of compute, memory, storage, and networking capacity closer to end-users.


## AWS Wavelength Zones

AWS Wavelength Zones are infrastructure offerings that embed AWS services at the edge of telecommunications providers' 5G networks. The goal is to minimize latency for mobile and edge-based devices, and to allow developers to build applications that can benefit from the ultra-low latency promised by 5G networks.

**Here are the key points about AWS Wavelength Zones**:

1. **Purpose and Functionality**: AWS Wavelength Zones are designed to support applications that require single-digit millisecond latencies by providing AWS services closer to the end-user within the telecommunications provider’s data center. This is particularly useful for applications like machine learning inference at the edge, autonomous industrial equipment, smart cars, live video streaming, video games, and augmented or virtual reality.

2. **Reduced Latency**: By bringing AWS services to the edge of the 5G network, data doesn't need to travel large distances to a centralized data center or cloud. This significantly reduces the round-trip time for data, thereby reducing latency.

3. **AWS Services**: Wavelength Zones support a wide variety of AWS services, including EC2 instances and EBS volumes, ECS and EKS for container-based applications, and more.

4. **Integration with AWS Regions**: Wavelength Zones are associated with an AWS Region. They extend the Region’s VPC to the Wavelength Zones using VPC Subnets, providing a consistent developer experience.

5. **Deployment**: You can deploy components of your application that require ultra-low latency to the Wavelength Zone and the rest of the application back in the AWS Region.

6. **Carrier Partnerships**: AWS has partnered with several telecommunications providers around the world to roll out Wavelength Zones.

7. **Pricing**: AWS services in Wavelength Zones are priced differently than in AWS Regions, and you also pay for data transfer in and out of a Wavelength Zone.

As of September 2021, AWS had rolled out Wavelength Zones with Verizon in several cities in the United States, and with other telecommunications providers in other countries. By using Wavelength Zones, developers can take full advantage of the advancements in 5G technology and create applications with ultra-low latencies to provide enhanced user experiences.
