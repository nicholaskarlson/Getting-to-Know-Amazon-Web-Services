# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 6 - AWS Networking & Content Delivery


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


# AWS Networking & Content Delivery - Detail


## Amazon VPC

**Amazon Virtual Private Cloud** (Amazon VPC) is a service that lets you launch AWS resources in a logically isolated virtual network that you define. This enables you to have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways.

**Here are the key features and aspects of Amazon VPC**:

1. Security: With Amazon VPC, you can use multiple layers of security, including security groups and network access control lists (ACLs) to help control inbound and outbound access to your instances and subnets. Furthermore, you can establish a private connection between your VPC and your corporate datacenter using an IPsec AWS Site-to-Site VPN connection.

2. Custom IP Range: You can select your IP address range from the entire IPv4 and IPv6 address spaces, which enables you to choose an IP address range that fits your network requirements.

3. Subnets: Within a VPC, you can divide your IP address range into one or more subnets to organize your network as efficiently as possible. This is useful for managing resources and controlling access to those resources.

4. Route Tables: Route tables allow you to control the traffic going out of your subnets. You might, for instance, want to create a public-facing subnet for your webservers that has access to the internet, and place your backend systems such as databases or application servers in a private-facing subnet with no internet access.

5. Network Gateways: Amazon VPC provides two types of network gateways - the Internet Gateway (IGW) that allows communication between instances in your VPC and the internet, and the Virtual Private Gateway (VPG) that allows communication between your VPC and your own corporate datacenter.

6. VPC Peering: VPC peering allows you to connect one VPC with another in a single region or across different AWS regions. This is done via a network connection route between the VPCs' CIDR blocks, which can be useful for sharing resources across multiple VPCs.

7. VPC Endpoints: VPC endpoints allow you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, VPN connection, or AWS Direct Connect connection.

8. NAT Devices: Network Address Translation (NAT) devices enable instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating connections with the instances.

9. Flow Logs: VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC.

In summary, Amazon VPC provides a highly customizable and secure environment within AWS where you can deploy your applications and services. Its flexibility in network design along with high degree of control over security makes it a fundamental component of the AWS ecosystem.


## Amazon Route 53

**Amazon Route 53** is a highly available and scalable Domain Name System (DNS) web service offered by Amazon Web Services. It is designed to give developers and businesses a reliable and cost-effective way to route end users to Internet applications by translating human-readable domain names (like 'www.example.com') into the numeric IP addresses that computers use to connect to each other.

**Here are the key features and aspects of Amazon Route 53**:

1. Domain Registration: Amazon Route 53 allows you to register new domain names or transfer existing ones. It supports a wide variety of domain name extensions, such as .com, .org, .net, etc.

2. DNS Routing: Amazon Route 53 translates friendly domain names like www.example.com into IP addresses like 192.0.2.1, which are used by computers to communicate with each other. It uses a global network of DNS servers to ensure a consistent and fast response, regardless of the geographical location of your end-users.

3. Health Checking: Amazon Route 53 can monitor the health and performance of your application, and your web servers, and if there's an issue, it can reroute traffic to healthy endpoints.

4. Scalability and Availability: Amazon Route 53 is built using AWS’s highly available and reliable infrastructure. The distributed nature of the AWS DNS servers helps ensure a consistent ability to route end users' traffic.

5. Traffic Flow: Route 53's Traffic Flow feature allows you to manage traffic globally through a variety of routing types, such as Latency Based Routing, Geo DNS, Geoproximity, and Weighted Round Robin.

6. DNSSEC: As of September 2021, Route 53 supports DNSSEC for domain registration. DNSSEC (Domain Name System Security Extensions) is designed to protect against forged DNS answers.

7. Integration with AWS Services: Route 53 is integrated with other AWS services such as AWS Shield for DDoS protection, AWS CloudFront for content delivery, and AWS Certificate Manager for SSL/TLS certificate management.

8. Security and Compliance: Amazon Route 53 supports DNSSEC for domain registration, which adds a layer of authentication on top of the DNS protocol to protect against certain types of attacks.

9. Cost-effectiveness: Amazon Route 53 follows a pay-as-you-go pricing model where you pay for the number of queries that the service answers.

In summary, Amazon Route 53 is a scalable, highly available, and reliable DNS web service designed to route end users to internet applications. Its capabilities make it a crucial part of any application running on AWS.


## Amazon CloudFront

**Amazon CloudFront** is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to users globally with low latency, high transfer speeds, all within a developer-friendly environment. CloudFront is integrated with AWS – both physical locations that are directly connected to the AWS global infrastructure, as well as other AWS services.

**Here are the key features and aspects of Amazon CloudFront**:

1. Global CDN: Amazon CloudFront uses a global network of edge locations, strategically located near users in the United States, Europe, Asia, South America, and Australia. When content is requested, it is delivered from the edge location that provides the lowest latency.

2. Integration with AWS Services: CloudFront is designed to work seamlessly with services including AWS Shield for DDoS mitigation, Amazon S3, Elastic Load Balancing or Amazon EC2 as origins for your applications, and Lambda@Edge to run custom code closer to customers’ users and to customize the user experience.

3. Performance: CloudFront uses a variety of techniques to boost performance, including persistent connections with origin servers, regional edge caches that help keep more of your content closer to your viewers, and automatic compression of certain text and binary objects.

4. Security: CloudFront offers several security features, including AWS Shield Standard, which provides automatic protections that help guard your applications against DDoS attacks. It also supports HTTPS using both SNI and dedicated IP, provides SSL/TLS encryption, and you can use AWS Certificate Manager (ACM) to create and manage custom SSL certificates at no extra cost. It also integrates with AWS Web Application Firewall to protect against common web exploits.

5. Cost-effective: With Amazon CloudFront, you only pay for the data transfer and requests that your users incur. There are no upfront costs, and it comes with a free tier for new AWS customers.

6. Developer-friendly: CloudFront provides APIs for managing your distribution and the CloudFront SDK for .NET and Java. It also supports AWS CloudFormation for creating CloudFront application templates for solutions that require content delivery.

7. Caching: You can specify how long CloudFront caches your files at edge locations. You can also invalidate objects, which removes them from CloudFront edge caches.

8. Lambda@Edge: This feature allows you to run AWS Lambda functions at the AWS edge locations, which means you can run functions that customize the content that CloudFront delivers, executing the functions closer to your application’s viewers.

In summary, Amazon CloudFront is a powerful content delivery network service that integrates well with other AWS services, providing an easy way to distribute content to end users with low latency, high data transfer speeds, and no commitments. It's suitable for a wide variety of web content and is especially valuable for serving static content and streaming media content.


## AWS Direct Connect

**AWS Direct Connect** is a cloud service solution that makes it easy to establish a dedicated network connection from your premises to AWS. Using AWS Direct Connect, you can establish private connectivity between AWS and your datacenter, office, or colocation environment, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections.

**Here are the key features and aspects of AWS Direct Connect**:

1. Reduced Bandwidth Costs: If you have significant data transfer requirements, AWS Direct Connect can reduce your network costs into and out of AWS in two ways. First, by transferring data to and from AWS directly, you can reduce your bandwidth commitment to your Internet service provider. Second, all data transferred over your dedicated AWS Direct Connect connection is charged at the reduced AWS Direct Connect data transfer rate rather than internet data transfer rates.

2. Compatible with all AWS Services: AWS Direct Connect is a network service, and works with all AWS services that are accessible over the Internet, such as Amazon Simple Storage Service (Amazon S3), Amazon Elastic Compute Cloud (Amazon EC2), and Amazon Virtual Private Cloud (Amazon VPC).

3. Private Connectivity to Your Amazon VPC: With AWS Direct Connect, you can establish private connectivity between your Amazon VPC and your datacenter, office, or colocation environment, which can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections.

4. Elastic: AWS Direct Connect makes it easy to scale your connection to meet your business needs. AWS Direct Connect provides 1 Gbps and 10 Gbps connections, and you can easily provision multiple connections if you need more capacity.

5. Dynamic or Static Routing: With AWS Direct Connect, you can choose either dynamic or static routing. Dynamic routing uses Border Gateway Protocol (BGP) to automatically update your router about the IP addresses that are reachable from your AWS Direct Connect connection. Static routing may be desirable if your network environment does not support BGP.

6. High Speed and Low Latency: Since your network traffic to AWS does not traverse the public internet, you get benefits such as consistent performance and increased privacy and security. This makes AWS Direct Connect well suited for applications that need high bandwidth, low latency communication with AWS resources.

In summary, AWS Direct Connect provides a dedicated, private network connection between your network and AWS, offering increased performance, security, and cost benefits for high-scale applications.


## Amazon Elastic Load Balancing

**Amazon Elastic Load Balancing** (ELB) automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions. It can handle the varying load of your application traffic in a single Availability Zone or across multiple Availability Zones.

**Elastic Load Balancing offers three types of load balancers**, all featuring high availability, automatic scaling, and robust security. These include the Classic Load Balancer (v1), Application Load Balancer (v2), and Network Load Balancer (v3).

1. **Classic Load Balancer** (v1): This provides basic load balancing across multiple Amazon EC2 instances and operates at both the request level and connection level. Classic Load Balancer is intended for applications that were built within the EC2-Classic network.

2. **Application Load Balancer** (v2): This is best suited for load balancing of HTTP and HTTPS traffic and provides advanced request routing targeted at the delivery of modern application architectures, including microservices and containers. Operating at the individual request level (Layer 7), Application Load Balancer routes traffic to targets within Amazon Virtual Private Cloud (VPC) based on the content of the request.

3. **Network Load Balancer** (v3): This is best suited for load balancing of Transmission Control Protocol (TCP), User Datagram Protocol (UDP), and Transport Layer Security (TLS) traffic where extreme performance is required. Operating at the connection level (Layer 4), Network Load Balancer routes traffic to targets within Amazon VPC and is capable of handling millions of requests per second while maintaining ultra-low latencies.

**Key features of Amazon Elastic Load Balancing**:

High Availability: ELB automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, and scales its capacity to meet traffic demands.

Health Checks: ELB can automatically perform health checks on registered instances so it can send requests only to the healthy instances.

Security Features: Users can add a security group to a load balancer, or SSL/TLS certificates to secure the communication between the clients and the load balancer.

Automatic Scaling: ELB is designed to automatically scale its capacity in response to incoming traffic.

Integration with AWS Services: ELB integrates with other AWS services such as AWS Certificate Manager for SSL/TLS certificates, Amazon CloudWatch for metrics, AWS CloudTrail for logging, and AWS Auto Scaling for adding/removing EC2 instances.

In summary, Amazon Elastic Load Balancing is a crucial service in AWS for ensuring high availability and fault tolerance of applications, and it comes with advanced features to meet various requirements of different types of applications.


## Amazon API Gateway

**Amazon API Gateway** is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the "front door" for applications to access data, business logic, or functionality from your back-end services. These back-end services can be a variety of services such as workloads running on Amazon Elastic Compute Cloud (EC2), code running on AWS Lambda, or any web application.

**Here are some of the key features and aspects of Amazon API Gateway**:

1. Performance at Scale: API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including traffic management, CORS support, authorization and access control, throttling, monitoring, and API version management.

2. Security: You have multiple options for authorizing access to your APIs and supporting secure data transfer. It can verify incoming requests by executing a Lambda authorizer from AWS Lambda. You can also use AWS Identity and Access Management (IAM) to verify and authenticate users, or you can use Cognito for user identity management. Furthermore, API Gateway can also verify API requests to ensure they're secure in transit against tampering or man-in-the-middle (MITM) attacks.

3. Lifecycle Management: Amazon API Gateway lets you operate multiple versions of the same API simultaneously so that applications can continue to call previous API versions even after the latest ones have been published.

4. Developer Productivity: API Gateway can generate client SDKs for a number of platforms, which can simplify the client-side development process.

5. Seamless integration with AWS services: It is built to work seamlessly with other AWS services like AWS Lambda, AWS CloudTrail, CloudWatch, etc.

6. API Operations Monitoring: API Gateway provides you with tools to monitor API usage, so you can track performance and identify trends to better understand the needs of your users.

7. Cost Efficiency: With API Gateway, you only pay for calls made to your APIs and data transfer out, and there are no minimum fees or upfront commitments.

8. RESTful API and WebSocket Support: API Gateway supports RESTful APIs and WebSocket APIs. REST APIs are synchronous and require a request-response model, while WebSocket APIs enable you to set up bidirectional communication between clients such as chatbots or real-time gaming.

In summary, Amazon API Gateway is a powerful, flexible service for managing your APIs, providing advanced features to control access, monitor use, improve performance, and reduce the code and resources required on your end.


## AWS Transit Gateway

**AWS Transit Gateway** is a service that enables customers to connect their Amazon Virtual Private Clouds (VPCs) and their on-premises networks to a single gateway. As you grow the number of workloads running on AWS, you need to be able to scale your networks across multiple accounts and Amazon VPCs to keep up with the growth. AWS Transit Gateway significantly simplifies management and reduces operational costs because each network only has to connect to the Transit Gateway and not to every other network. Any new VPC is simply connected to the Transit Gateway and is then automatically available to every other network that is connected to the Transit Gateway.

**Here are some key features and benefits of AWS Transit Gateway**:

1. Simplify Network Architecture: Before AWS Transit Gateway, you needed to implement a full mesh network between your Amazon VPCs and your on-premises VPNs. With AWS Transit Gateway, you only have to create and manage a single connection from the central gateway into each Amazon VPC, on-premises data center, or remote office across your network.

2. Scale Connectivity Across Thousands of Amazon VPCs: AWS Transit Gateway scales elastically to support the growth of your business, allowing you to connect thousands of Amazon VPCs and on-premises networks.

3. Centralized Routing Policies: With AWS Transit Gateway, you can maintain one large network and control routing policies through the central hub. This makes it easier to manage and troubleshoot your ever-growing AWS environment.

4. High Availability and Elasticity: AWS Transit Gateway is built to offer high availability and elasticity, and you are not required to size your gateway for peak bandwidth.

5. Transit Gateway Network Manager: This feature allows you to visualize and monitor your AWS and on-premises networks from a single console. You can also leverage global accelerators with Transit Gateway to improve the performance of your network for your global users.

6. Integration with Other AWS Services: Transit Gateway works seamlessly with other AWS services like AWS Direct Connect, Amazon Route 53 Resolver, and more.

7. Security and Compliance: AWS Transit Gateway provides a secure, centralized gateway to control your network traffic and routing. You can segregate your workloads and only allow necessary communication paths for a security-conscious design.

In summary, AWS Transit Gateway is a powerful tool for simplifying and scaling your network architecture within AWS. It provides centralized control, easier management, and improved connectivity.


## AWS Global Accelerator

**AWS Global Accelerator** is a networking service that helps to improve the availability and performance of the applications that you offer to your users. It does this by using the highly available and congestion-free AWS global network infrastructure to direct user traffic to your applications in the most efficient way possible.

**Here are the key features and aspects of AWS Global Accelerator**:

1. Improve Performance: AWS Global Accelerator uses the AWS global network to optimize the path from your users to your applications, improving the performance of your TCP and UDP traffic. AWS continually optimizes paths to ensure your users are routed to your application along the fastest path.

2. Increase Availability: AWS Global Accelerator ensures that your user traffic is directed to a healthy application endpoint. It instantly reacts to changes in the health or configuration of your application and its endpoints.

3. Simplify Operations: Instead of managing IP addresses for all your resources, you can manage a single IP address provided by AWS Global Accelerator. This simplifies DNS setup and makes it easy to switch your backend services, like moving from an EC2 instance to a Network Load Balancer.

4. Protect Your Applications: AWS Global Accelerator uses AWS Shield Standard to protect your applications against DDoS attacks.

5. Application Failover: In the event of failure of an application instance or a decrease in application performance, AWS Global Accelerator automatically redirects user traffic to another available and healthy location.

6. Fixed Entry Points: AWS Global Accelerator provides static IP addresses that act as a fixed entry point to your applications hosted in any number of AWS Regions. These IP addresses are announced from multiple AWS edge locations.

7. Regional Endpoint Weighting: This feature allows you to assign weights, which determine the proportion of traffic directed to your AWS Regions. It can be useful for testing new versions of applications, for blue/green deployment, and for more control over regional failover.

In summary, AWS Global Accelerator is designed to improve the availability and performance of your applications for users across the globe. By leveraging the AWS global network infrastructure, it provides users with consistently high performance and availability by routing user requests to the nearest healthy endpoint based on geographic proximity, application health, and routing policies that you can configure.


## AWS App Mesh

**AWS App Mesh** is a service mesh that provides application-level networking to make it easy for your services to communicate with each other across multiple types of compute infrastructure. AWS App Mesh standardizes how your services communicate, giving you end-to-end visibility and helping to ensure high availability for your applications.

**Here are some of the key features and aspects of AWS App Mesh**:

1. Service Mesh: AWS App Mesh makes it easy to run microservices by providing consistent visibility and network traffic controls for services built across multiple types of compute infrastructure. AWS App Mesh removes the need to update application code to change how monitoring data is collected or traffic is routed between services.

2. Consistent Visibility: AWS App Mesh provides consistent visibility into your application behavior by exporting logs, metrics, and traces to the tools of your choice. This allows you to monitor and identify the source of performance issues or errors, and resolve them quickly.

3. Application-level Networking: With AWS App Mesh, you can route traffic based on application-level metrics like request counts or response times. This allows you to more effectively manage deployments, rollouts, and canary releases.

4. Fine-grained Traffic Controls: AWS App Mesh allows you to control traffic routing at the application level to guide the flow of traffic between services. This can help when you're rolling out new versions of services, testing new features, or performing A/B testing.

5. Service-Level Insights: AWS App Mesh tracks communications across your services and collects end-to-end traces of requests. This data can be used to build a comprehensive view of your services, their interactions, and their dependencies.

6. Integration with AWS Services: AWS App Mesh works well with Amazon ECS, Amazon EKS, AWS Fargate, and Kubernetes running on AWS, allowing you to manage, secure, and control communication across a wide variety of compute types.

In summary, AWS App Mesh helps manage, monitor, and control traffic for microservices applications, across various types of compute infrastructure. By providing a unified and consistent layer of control and visibility, it helps to ensure that applications are highly available, resilient, and scalable.
