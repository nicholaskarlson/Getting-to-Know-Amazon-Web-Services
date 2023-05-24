# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 3 - AWS Compute Services


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


## AWS Compute Services

**AWS Compute Services** are the backbone of many applications running on Amazon Web Services. They offer a range of services suitable for different workloads and requirements. Here are the key services:

**Amazon EC2** (Elastic Compute Cloud): EC2 is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale computing easier by providing a simple web service interface that allows you to obtain and configure capacity with minimal friction. EC2 offers a variety of instance types optimized to fit different use cases, such as memory-optimized, compute-optimized, and storage-optimized instances.

**AWS Lambda**: This service lets you run your code without provisioning or managing servers. You just upload your code, and Lambda takes care of everything required to run and scale your code with high availability. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app. This is an example of "Function as a Service" or FaaS, and is used for serverless computing.

**Amazon ECS** (Elastic Container Service): Amazon ECS is a highly scalable, high-performance container orchestration service that supports Docker containers and allows you to run applications on a managed cluster of Amazon EC2 instances. ECS eliminates the need for you to install, operate, and scale your own cluster management infrastructure.

**Amazon EKS** (Elastic Kubernetes Service): Amazon EKS is a managed service that makes it easy for you to run Kubernetes on AWS without needing to install and operate your own Kubernetes control plane or nodes. Kubernetes is a popular open-source system for automating the deployment, scaling, and management of containerized applications.

**AWS Fargate**: Fargate is a compute engine for Amazon ECS and EKS that allows you to run containers without having to manage the underlying EC2 instances. With Fargate, you can focus on designing and building your applications instead of managing the infrastructure that runs them.

**AWS Batch**: This is a set of batch computing services. It efficiently plans, schedules, and executes your batch computing workloads across the full range of AWS compute services and features, such as EC2 and Spot Instances.

**Amazon Lightsail**: Lightsail provides virtual private servers (instances). It's designed to be the easiest way to launch and manage a virtual private server with AWS. It includes everything you need for a project, such as a virtual machine, SSD-based storage, data transfer, DNS management, and a static IP, for a low, predictable price.

Each of these services is designed for different workloads and use cases. For example, you might use EC2 for an application requiring a great deal of custom configuration, while Lambda might be a better fit for a microservices architecture. Understanding these services is crucial for using AWS effectively.


# AWS Compute Services - Detail


## Amazon Elastic Compute Cloud

**Amazon Elastic Compute Cloud** (EC2) is one of the foundational services of Amazon Web Services (AWS) that offers secure, resizable compute capacity in the cloud. It is designed to make web-scale computing easier for developers by providing a simple web service interface that allows you to obtain and configure capacity with minimal friction.

**Key aspects of Amazon EC2 include**:

1. **Instances**: Amazon EC2 provides virtual servers known as instances for computing capacity. You can launch instances with different configurations of CPU, memory, storage, and network capacity to suit your needs.

2. **Amazon Machine Images (AMI)**: An AMI is a template that contains a software configuration (an operating system, an application server, and applications) which you can use to launch instances. You can select an AMI provided by AWS, the user community, or through the AWS Marketplace. You can also create your own AMIs.

3. **Instance Types**: EC2 provides a variety of instance types optimized to fit different use cases, ranging from memory-optimized to compute-optimized instances, as well as instances optimized for storage or GPU processing.

4. **Regions and Availability Zones**: Amazon EC2 is hosted in multiple locations world-wide, which are composed of AWS regions and Availability Zones. You can launch your instances in a location that meets your requirements, whether it be near certain customers, or to meet legal or other requirements.

5. **Security Groups and Network Access Control Lists (NACLs)**: EC2 instances can be controlled with both security groups and network access control lists to enable certain inbound and outbound traffic.

6. **Elastic IP addresses**: These are static, public IPv4 addresses designed for dynamic cloud computing. An Elastic IP address is associated with your AWS account, and you can easily remap it to any instance in your account.

7. **Auto Scaling**: Amazon EC2 Auto Scaling allows you to automatically adjust the number of EC2 instances in response to traffic patterns, helping to provide enough instances to handle the load during peak periods and reducing capacity during off-peak times to save money.

8. **Load Balancing**: Elastic Load Balancing automatically distributes incoming application traffic across multiple Amazon EC2 instances for fault tolerance and load distribution.

9. **Pricing Models**: EC2 offers several pricing models including On-Demand (pay for what you use), Reserved Instances (commit to one or three years of usage and receive a discount), Spot Instances (bid on spare EC2 computing capacity), and Dedicated Hosts (physical EC2 server dedicated for your use).

10. **Elastic Block Store** (EBS): Amazon EC2 uses Amazon EBS for block-level storage volumes that you can attach to your instances. They persist independently from the life of an instance.

11. **Integration with other AWS services**: EC2 works together with many other AWS services like Amazon S3, RDS, DynamoDB, etc. to provide a complete, secure solution for computing, query processing, and cloud storage across a wide range of applications.

Amazon EC2 is a powerful service that forms the backbone of many applications running on AWS. Its flexibility, scalability, and broad feature set make it a core component of any AWS-based infrastructure.

**AWS Lambda**

AWS Lambda is a serverless compute service that lets you run your code without provisioning or managing servers. It executes your code only when needed and scales automatically, from a few requests per day to thousands per second.

**Key aspects of AWS Lambda include**:

1. **Event-driven**: AWS Lambda is designed to use events to trigger functions. These events could come from a change to data in an Amazon S3 bucket, an update to a DynamoDB table, custom events from mobile applications or web applications, and more.

2. **Serverless**: With Lambda, you don't have to worry about server maintenance, capacity provisioning, or automatic scaling. This allows developers to focus on core product functionality and ignore the operational aspects.

3. **Automatic Scaling**: Lambda functions automatically scale up and down in response to events. Whether you are running 1 request or 1000 requests concurrently, AWS Lambda scales precisely with the size of the workload.

4. **Programming Languages**: AWS Lambda supports several programming languages, including Node.js, Python, Ruby, Java, Go and .NET.

5. **Integration with AWS Services**: Lambda integrates well with other AWS services, like Amazon S3 for event-driven processing of objects, DynamoDB for executing code in response to table updates, Amazon Kinesis for processing streaming data in real-time, and many more.

6. **Pricing**: With AWS Lambda, you are charged for every 100ms your code executes and the number of times your code is triggered. You don't pay for idle time.

7. **Security**: Lambda functions operate within a VPC by default. You can also configure a function to access resources in a VPC, allowing you to interact with databases, storage, and other services.

8. **Stateless and Stateful Processing**: By default, AWS Lambda executes your functions in a stateless environment. However, if your application needs to maintain a consistent state, like in a web session, you can leverage services like Amazon DynamoDB or utilize AWS Step Functions.

9. **Microservices Architecture**: Lambda is used in microservices architectures because it allows developers to focus on product development rather than infrastructure management. Each function can be a separate microservice, with its own responsibility, and can be developed, updated, scaled, and monitored independently.

AWS Lambda has revolutionized the way we think about compute resources for applications, by allowing developers to focus on writing code without having to worry about the underlying infrastructure, scaling, or deployment pipeline. It is an essential service for anyone looking to build applications in the AWS ecosystem.


## Amazon Elastic Container Service

**Amazon Elastic Container Service** (ECS) is a highly scalable, high-performance container orchestration service that allows you to easily run, stop, and manage Docker containers on a cluster. It's used to host, scale, and manage the infrastructure required by containerized applications.

**Key aspects of Amazon ECS include**:

1. **Docker Compatibility**: ECS supports Docker, a popular open-source containerization technology. This means that you can package applications as Docker containers and ECS can run them.

2. **Scalability**: ECS can scale to run potentially thousands of containers across multiple instances based on the requirements of your workloads.

3. **Service Scheduler**: ECS has a built-in scheduler that ensures your containers are kept healthy and maintains the desired count. If a container goes down, the scheduler launches another one.

4. **Task Definitions**: In ECS, a task definition is like a blueprint for your application. It specifies various parameters for your application such as the Docker image to use, the required CPU and memory, the Docker networking mode, data volumes, and the IAM role that the task can assume.

5. **Clusters**: A cluster is a grouping of tasks or services. If you're running tasks or services that use the EC2 launch type, a cluster is also a grouping of container instances. If you're using capacity providers, a cluster is also a logical grouping of capacity providers.

6. **Integration with AWS Services**: ECS integrates well with other AWS services, such as Amazon Route 53 for service discovery, AWS Identity and Access Management (IAM) for security, Amazon CloudWatch for metrics, and AWS CloudTrail for auditing, among others.

7. **Security**: ECS allows granular permission levels through the use of IAM roles. This allows you to adhere to the principle of least privilege and not give more permissions than necessary to your containers.

8. **Networking**: ECS supports Docker networking and integrates with Amazon VPC to provide isolation for containers. This allows you to control inbound and outbound access to your containers using VPC security groups.

9. **AWS Fargate**: With AWS Fargate, a serverless compute engine for containers, you can use ECS to manage containers without having to manage the underlying EC2 instances, further reducing the need to manage infrastructure.

10. **Cost-Effectiveness**: With ECS, you pay for AWS resources (e.g. EC2 instances or EBS volumes) you create to store and run your applications. There is no additional charge for ECS itself.

In summary, Amazon ECS provides a simplified way of running and managing Docker containers at scale, with deep AWS integration and enterprise-level security. It is a powerful tool in the toolkit of any organization looking to deploy containerized applications.


## Amazon Elastic Kubernetes Service

**Amazon Elastic Kubernetes Service** (EKS) is a fully managed service provided by AWS that makes it easy for you to use Kubernetes, an open-source system for automating the deployment, scaling, and management of containerized applications.

**Here are key aspects of Amazon EKS**:

1. **Managed Kubernetes**: EKS automatically handles the underlying Kubernetes infrastructure, dealing with the complexity of planning, deploying, and scaling the Kubernetes clusters. This allows developers to focus on building applications rather than managing Kubernetes control planes.

2. **Kubernetes Compatibility**: EKS runs upstream Kubernetes, providing compatibility with existing plugins and tooling from the Kubernetes community. Applications running on Amazon EKS are fully compatible with applications running on any standard Kubernetes environment.

3. **High Availability and Scalability**: Amazon EKS runs the Kubernetes control plane instances across multiple AWS Availability Zones, automatically detects and replaces unhealthy control plane instances, and provides automated version upgrades and patching.

4. **Security and Compliance**: Amazon EKS is integrated with key AWS features like Elastic Load Balancing for load distribution, IAM for authentication, Amazon VPC for isolation, AWS PrivateLink for private network access, and AWS CloudTrail for logging.

5. **Integration with AWS Services**: EKS integrates with services like Amazon RDS, Amazon S3, Amazon DynamoDB, AWS Lambda, AWS Fargate, Amazon CloudWatch, AWS CloudFormation, AWS CodeStar, and the AWS CLI.

6. **Networking and Communication**: Amazon EKS fully supports the Kubernetes Network Policy API that allows you to control the traffic flow at the IP address or port level.

7. **AWS Fargate Integration**: AWS Fargate is a serverless compute engine for containers that works with both Amazon EKS and Amazon ECS. With Fargate, you don't need to provision, configure, or scale clusters of virtual machines to run containers.

8. **Community and Ecosystem**: Since EKS is based on Kubernetes, it benefits from the vibrancy of the Kubernetes ecosystem. It can work with many existing extensions and plugins from the Kubernetes community.

9. **Pricing**: You pay for AWS resources (e.g., EC2 instances or EBS volumes) you create to run your Kubernetes worker nodes. There is an additional charge for the EKS control plane.

In summary, Amazon EKS is a powerful, scalable and flexible service for running Kubernetes in the cloud. It takes care of the undifferentiated heavy lifting of maintaining Kubernetes control planes, so you can focus on building and deploying applications.


## AWS Fargate

**AWS Fargate** is a serverless compute engine for containers that works with both Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS). It removes the need to provision, configure, and manage servers to run your containers.

**Key aspects of AWS Fargate include**:

1. **Serverless**: With Fargate, you don't have to worry about server maintenance or capacity planning. This allows developers to focus on building applications without the need to manage the underlying infrastructure.

2. **Cost Efficiency**: Fargate uses a pay-as-you-go model, charging based on the vCPU and memory resources consumed by your containerized applications. This can lead to cost savings, as you only pay for the resources your applications actually use.

3. **Scalability**: Fargate can quickly scale up to handle high demand, then scale back down when demand subsides. This elasticity means you don't have to over-provision resources to ensure your applications remain available during peak times.

4. **Security**: Each Fargate task runs in its own isolated environment with its own resources, which minimizes the risk of one task affecting another. Also, because you don't have to manage the underlying servers, Fargate reduces your infrastructure attack surface.

5. **Integration with AWS Services**: Fargate integrates with AWS services like VPC, ALB (Application Load Balancer), CloudWatch, and IAM, and works seamlessly with ECS and EKS, allowing you to use the same APIs and choose the orchestrator that best fits your needs.

6. **Simplified Networking**: AWS Fargate tasks use Elastic Network Interfaces (ENIs) to allow each task to have its own networking namespace, which includes its own IP address, MAC address, and network interfaces.

7. **Compute Isolation**: Fargate runs each task or pod in its own kernel runtime environment without sharing resources, providing workload isolation.

8. **Compliance and Standards**: Fargate is compliant with various standards like ISO, PCI, HIPAA, SOC, and GDPR, which makes it suitable for a wide range of applications and industries.

In summary, AWS Fargate is a powerful tool for running containerized applications without the hassle of managing the underlying servers. It's an excellent option for teams who want to focus on building applications without worrying about infrastructure management.


## AWS Batch

**AWS Batch** is a fully managed service that makes it easy to run batch computing workloads on the AWS Cloud. Batch computing is a form of computing where a large amount of data is processed in a series of jobs without user interaction. These jobs are often discrete and can be distributed across different servers.

**Key aspects of AWS Batch include**:

1. **Job Scheduling**: AWS Batch dynamically provisions the optimal quantity and type of compute resources (e.g., CPU or memory optimized instances) based on the volume and specific resource requirements of the batch jobs submitted.

2. **Managed Service**: AWS Batch handles job scheduling, cluster provisioning, failures, and retries without requiring user intervention. This removes the need to install and manage batch computing software, allowing developers to focus on analyzing results and optimizing code.

3. **Integration with AWS Services**: AWS Batch is deeply integrated with other AWS services like EC2, ECS (as it uses Docker containers to run jobs), S3, DynamoDB, and CloudWatch, offering a consistent experience across services.

4. **Cost Optimization**: AWS Batch is designed to be cost-efficient and uses EC2 Spot Instances to optimize cost. Spot Instances allow you to bid on spare EC2 computing capacity, often at significant discounts compared to On-Demand prices.

5. **Scalability**: AWS Batch is designed to scale. By queuing incoming jobs that cannot be immediately run, AWS Batch can accommodate sudden bursts in computation needs and then scale back down when demand subsides.

6. **Flexibility**: AWS Batch enables developers, scientists, and engineers to run hundreds of thousands of batch computing jobs on AWS. It can accommodate a wide variety of workloads, including data processing, data transformation, machine learning, and scientific simulations.

7. **Security**: AWS Batch follows the AWS Shared Responsibility Model for security. It integrates with AWS Identity and Access Management (IAM) to provide resource permissions and supports VPC to isolate resources and data.

In summary, AWS Batch is a powerful tool for running batch computing workloads, simplifying setup, scaling, and management of batch jobs, and allowing users to focus on their application code or scientific models.


## AWS Lightsail

**AWS Lightsail** is a cloud service from Amazon Web Services that simplifies the launch and management of a virtual private server (VPS). Lightsail includes everything you need for a project, like a compute instance, SSD-based storage, data transfer, DNS management, and a static IP, for a low, predictable monthly price.

**Key aspects of AWS Lightsail include**:

1. **Simplicity**: AWS Lightsail is designed for simplicity and ease of use. It simplifies the process of creating, running, and managing servers by providing a straightforward, easy-to-use interface, making it a good option for those new to the cloud or those who prefer a simpler management experience.

2. **Predictable Pricing**: Each Lightsail plan includes a monthly price for a bundle of resources. This makes cost management easier and helps to avoid surprise charges.

3. **Managed Environment**: Lightsail automatically handles maintenance and software updates, allowing developers to focus on creating and running their applications.

4. **Variety of Instances**: Lightsail offers a variety of instance types to meet different needs. This includes instances optimized for memory, compute, and storage.

5. **Preconfigured Application Stacks**: Lightsail offers a variety of pre-configured application stacks (like LAMP, Node.js, WordPress, Joomla, Drupal, and others) and development stacks (like MEAN, LAMP, Nginx, and more). This simplifies application setup and deployment.

6. **Networking Features**: Lightsail instances come with a set of networking features like static IP addresses, DNS management, and firewall controls.

7. **Scalability**: Although Lightsail is designed for simpler workloads, if a project grows, it's possible to transition smoothly to the more powerful EC2 service using instance snapshots.

8. **Integration with AWS Services**: Although it's designed to be simple, Lightsail is part of AWS and can therefore connect with other AWS services like RDS, S3, and CloudFront.

9. **Global Availability**: Lightsail is available in many AWS regions, meaning you can deploy your application closer to your users to reduce latency.

In summary, AWS Lightsail is a straightforward, easy-to-use platform that provides all the resources needed to build an application or website, with a low, predictable monthly price. It's particularly well-suited to simpler workloads, smaller applications, and websites, as well as developers just beginning with AWS.
