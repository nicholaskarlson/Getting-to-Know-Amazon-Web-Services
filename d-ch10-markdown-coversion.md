# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 10 - AWS Pricing and Cost Management


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


# AWS Pricing and Cost Management - Detail


## AWS Pay-as-you-go pricing

**AWS's "Pay-As-You-Go" pricing model** is one of the key selling points of cloud services like AWS. This model means that you only pay for the specific resources you use, when you use them. You do not need to commit to long-term contracts or purchase dedicated infrastructure.

**Here are some important aspects of AWS's Pay-As-You-Go pricing**:

1. No Upfront Costs: You don't have to invest in hardware upfront. AWS allows you to access and use their vast infrastructure on a rental basis, thereby saving the upfront costs of setting up and running on-site data centers or servers.

2. Granular Billing: AWS offers granular billing for its services, meaning you are billed based on the exact amount of resources you have used. For instance, Amazon EC2 is billed by the second, with a minimum of 60 seconds. This granular billing extends to data transfer, storage, and other features.

3. Scale as Needed: One of the major advantages of the Pay-As-You-Go model is that it allows you to scale your resources as per your needs. You can increase resources during peak demand and decrease resources during off-peak times, ensuring that you only pay for what you use.

4. Free Tier: AWS offers a free tier, which includes a limited amount of free usage for many of their popular services for 12 months after you sign up for an AWS account. This lets you explore and get hands-on experience with AWS services, and even host a small scale app without any costs.

5. Cost Explorer and Budgets: AWS provides tools like AWS Cost Explorer to visualize, understand, and manage your AWS costs and usage over time. AWS Budgets lets you set custom cost and usage budgets that alert you when your usage exceeds your budgeted amount.

6. Savings Plans and Reserved Instances: While the basic model is Pay-As-You-Go, AWS also offers ways to save on costs if you have predictable workload patterns. These include Savings Plans and Reserved Instances, which allow you to commit to a consistent amount of usage (e.g., hours of Amazon EC2 usage) in exchange for discounted rates.

In summary, AWS's Pay-As-You-Go model offers significant flexibility and cost savings, allowing businesses of all sizes to effectively manage their budget and only pay for the services they use. It also removes the need for significant upfront hardware investments and allows for rapid scaling of resources in response to changing demand.


## AWS Savings Plans

**AWS Savings Plans** is a flexible pricing model that offers significant savings on AWS compute usage. It provides a simpler and more flexible alternative to Reserved Instances (RIs). While RIs require customers to commit to using specific instance types in specific regions, Savings Plans offer savings on a broader level, allowing for changes in instance usage.

**There are two types of Savings Plans**:

1. **Compute Savings Plans**: These provide the most flexibility and can help save up to 66% on compute costs. They apply to any EC2 instance regardless of region, instance family, size, or tenancy, including those that are part of EMR, ECS, or EKS clusters, or launched via Fargate. They also apply to AWS Lambda and AWS Fargate usage.

2. **EC2 Instance Savings Plans**: These provide the lowest prices, offering savings of up to 72%, in exchange for commitment to usage of individual instance families in a specific region (e.g., M5 usage in N. Virginia). This is similar to regional Reserved Instances.

**The key features of AWS Savings Plans include**:

Flexible Commitment: Customers commit to a certain level of compute usage, measured in dollars per hour, for a term of 1 or 3 years.

Simplified Billing: The hourly commitment is automatically applied to the customer’s bill across accounts and regions, optimizing the cost savings against any eligible compute usage.

Easy Management: AWS Cost Explorer makes it easy to manage Savings Plans. It provides recommendations based on your historical usage, helps you understand how Savings Plans are applied to your bill, and lets you see the remaining commitment.

Plan Options: Customers can pay for Savings Plans in three ways: All upfront, Partial upfront, or No upfront. The All upfront option usually yields the highest savings.

In conclusion, AWS Savings Plans are a flexible and cost-effective way to use AWS services. By committing to a certain amount of usage over a period of time, customers can achieve significant savings compared to on-demand rates. It's especially beneficial for users with predictable workloads and long-term usage, offering the benefits of Reserved Instances but with more flexibility.


## AWS Reserved Instances

**AWS Reserved Instances** (RIs) offer a significant discount (up to 75%) compared to on-demand instance pricing. They provide a capacity reservation and offer a significant discount on the hourly charge for an instance. Reserved Instances can be purchased for a one-year or three-year term, and the longer the commitment, the greater the discount.

**There are three types of Reserved Instances**:

1. **Standard Reserved Instances**: These offer the most significant savings on a per-hour cost but cannot be changed after they are purchased.

2. **Convertible Reserved Instances**: These are more flexible than Standard RIs. They can be exchanged for RIs of equal or greater value at any point during their term, which allows you to change the instance type during the RI term.

3. **Scheduled Reserved Instances**: These are designed to match predictable recurring schedules that only require a fraction of a day, a week, or a month. For example, you might purchase an RI for every Saturday from 1 AM to 5 AM if you run a batch process every week at that time.

**Key concepts related to Reserved Instances**:

Scope: The scope of an RI can be set to a region or a specific availability zone. Regional RIs apply the discount to any instance usage in a region, while AZ-specific RIs provide a capacity reservation and apply the discount only to instance usage in a specific availability zone.

Instance Size Flexibility: With regional RIs, AWS provides instance size flexibility, which means your RI's discounted rate will automatically apply to usage of any size within the same instance family (M5, T2, etc.) in the region.

Payment Options: Reserved Instances can be purchased with three payment options: All Upfront, Partial Upfront, and No Upfront. The All Upfront option typically offers the highest savings.

Reserved Instances can be a cost-effective choice if you have a predictable workload with steady state usage and can commit to using EC2 over a one- or three-year term. However, since the advent of Savings Plans, which offer similar or better savings with greater flexibility, the use of RIs has become less common.


## AWS Spot Instances

**AWS Spot Instances** allow you to take advantage of unused EC2 capacity in the AWS cloud at a significant discount compared to On-Demand pricing — up to 90% off. Spot Instances are ideal for use cases where applications have flexible start and end times, or applications that are only feasible at very low compute costs.

Spot Instances work on a bidding principle, where you specify the maximum price you are willing to pay per hour per instance. When your bid exceeds the current Spot price, your request is fulfilled and your instances will run until either you choose to terminate them or the Spot price exceeds your maximum price.

**Here are some key concepts related to Spot Instances**:

Spot Price: The Spot price is determined by supply and demand for unused AWS capacity. The Spot price changes periodically based on these factors and the price you pay varies accordingly.

Spot Instance Requests: A Spot Instance request is a mechanism to request Spot Instances. You can specify the maximum price you're willing to pay, the instance types you want, and the Availability Zones in which you're interested.

Interruptions: Spot Instances can be interrupted by AWS with two minutes of notification when AWS needs the capacity back, or when the Spot price exceeds your maximum price.

Spot Instance Pools: Each combination of instance type, operating system, and Availability Zone forms a separate Spot Instance pool. Therefore, diversifying your Spot Instance requests across different Spot Instance pools will increase the chance that your requests will be fulfilled and decrease the chance that AWS interrupts your instances.

Spot Fleet: A Spot Fleet is a set of Spot Instances, and optionally On-Demand Instances. The Spot Fleet attempts to launch the number of Spot Instances and On-Demand Instances to meet the target capacity you specified during launch.

Spot Instances are great for fault-tolerant and flexible applications. They can be used for various applications like big data analytics, containerized workloads, CI/CD, web servers, high-performance computing (HPC), and other test & development workloads.

Spot Instances are a cost-effective choice if your applications can withstand possible instance interruptions. However, they require a good understanding of the AWS Spot market dynamics and careful management to avoid unexpected charges or interruptions.


## AWS Cost Explorer

**AWS Cost Explorer** is a tool that enables you to visualize, understand, and manage your AWS costs and usage over time. It provides a set of default reports that you can use as starting points for detailed breakdowns of your costs. You can view your cost data as far back as the last 13 months, and forecast how much you are likely to spend for the next three months.

**Key features of AWS Cost Explorer include**:

Detailed Reporting: AWS Cost Explorer includes features such as filtering and grouping, allowing you to analyze your costs by AWS service, linked account, tag, and more. You can also download your Cost and Usage report, Reserved Instance (RI) report, and Savings Plans reports in CSV format.

Forecasting: You can use Cost Explorer to identify trends, pinpoint cost drivers, and detect anomalies. The tool uses your past cost data to extrapolate future expenses, which is particularly useful for budgeting purposes.

Cost Allocation Tags: Cost Explorer supports cost allocation tags, which are key-value pairs that you can add to your AWS resources. These tags allow you to organize your resources and allocate costs precisely, enhancing your cost reporting.

RI Utilization and Coverage: You can track Reserved Instances utilization and coverage to maximize your RI benefits. These reports help you manage your RIs and identify opportunities to save more with RIs.

Savings Plans Utilization and Coverage: Just like with RIs, you can also track your Savings Plans' utilization and coverage to maximize your savings.

API Access: Cost Explorer also provides an API, which gives you programmatic access to your cost and usage data.

Using AWS Cost Explorer can help you track where your AWS spending is going, and identify areas where you might be able to cut costs. For instance, if you're spending a lot on a particular AWS service, you can analyze your usage to see if it aligns with your expectations, and whether you might be able to utilize resources more efficiently.


## AWS Budgets

**AWS Budgets** provides tools that enable you to manage your costs and usage, and keep track of your AWS resource spending. It lets you set custom cost and usage budgets that alert you when your user-defined thresholds are breached.

**Here are some of the key features of AWS Budgets**:

Cost Budgets: You can set a budget for your AWS costs, and track them based on your preferences. The budget can be tracked either at an aggregate level, such as for overall AWS costs, or for individual services.

Usage Budgets: In addition to setting a budget based on costs, you can also set a budget based on usage for a specific service or set of services.

Reservation Budgets: This helps you set a budget for your Reserved Instance (RI) or Savings Plan usage, allowing you to track the utilization of your purchased RIs or Savings Plans.

Budget Alerts: AWS Budgets lets you create alerts that notify you via email or SMS when your usage or costs exceed the thresholds you've set in your budgets.

Cost Explorer Integration: AWS Budgets is integrated with AWS Cost Explorer, enabling you to visualize the cost or usage anomalies of each budget.

AWS Budgets Dashboard: The dashboard provides a consolidated view of all your budgets and tracks their performance over time.

You can use AWS Budgets to track your AWS expenditure and avoid unexpected charges. For example, you can create a budget to track your monthly AWS costs, and receive alerts when your costs exceed 80% of your budget.

Remember, AWS Budgets allows you to plan your service usage, cost, and RI or Savings Plans utilization - but it doesn't prevent services from being used after the budget is met. Stopping the usage of services once the budget has been met requires manual intervention or automation set up through AWS services such as AWS Lambda.


## AWS Cost and Usage Report

**The AWS Cost and Usage Report** (CUR) is a comprehensive set of AWS usage data provided by Amazon Web Services. This report provides detailed information about your AWS costs, including information related to product, pricing, and usage. Users can configure AWS to deliver this report to a specified S3 bucket in their account.

**Here are the key features and uses of the AWS Cost and Usage Report**:

Granular Data: CUR provides the most detailed view of your AWS costs and usage. This includes line-item level details, resource IDs, and more.

Customization: You can customize the AWS Cost and Usage Report to meet your specific needs. You can include additional details, like resource IDs, and you can also choose to have your report data aggregated by hour, day, or month.

Integrated with Other AWS Services: The CUR can be directly imported into Amazon Athena, Amazon Redshift, and AWS QuickSight for further analysis. This integration makes it easy to perform complex queries on your cost and usage data, and visualize the results.

Support for Reserved Instances (RIs) and Savings Plans: The CUR includes information about your Reserved Instance and Savings Plans usage, amortized costs, and other relevant data. This can help you manage and optimize your RIs and Savings Plans.

Billing Management: The CUR is an essential tool for managing your AWS billing. By understanding how resources are being used, you can identify opportunities for cost savings and more effectively allocate costs across your organization.

Cost Allocation Tags: AWS CUR supports cost allocation tags, which are user-defined key-value pairs that help you organize your AWS resources. These tags can be included in your CUR, enabling you to break down your AWS costs by different categories such as cost center, project, or environment.

Remember, setting up the AWS Cost and Usage Report requires appropriate permissions in your AWS account, and there may be additional costs associated with storing the report data in an Amazon S3 bucket and using other AWS services to analyze your report data.


## AWS Trusted Advisor

**AWS Trusted Advisor** is a tool that provides real-time guidance to help you provision your resources following AWS best practices. Trusted Advisor inspects your AWS environment and makes recommendations for saving money, improving system performance, reliability, and security. It essentially acts as your customized cloud expert, helping you to observe best practices for the use of AWS products and services.

**Here are some of the key features of AWS Trusted Advisor**:

Cost Optimization: Trusted Advisor provides recommendations that can help you save money by identifying idle and underutilized resources, and suggesting potential cost-cutting options like reserving instances or consolidating billing.

Performance Improvement: It can detect and bring attention to potential bottlenecks, over-provisioned instances, and identify opportunities for improved system performance and speed.

Security: Trusted Advisor checks for security vulnerabilities and discrepancies in your security settings. This includes open ports, poorly configured security groups, and IAM use.

Fault Tolerance: It identifies potential points of failure and suggests redundancy measures, helping you achieve higher availability and reduce chances of system failure.

Service Limits: Trusted Advisor helps track service usage against limits and can give you early warnings about nearing those thresholds.

Access to Trusted Advisor: Trusted Advisor can be accessed via the AWS Management Console, CLI, or SDK. There is also an API available for automating tasks and integrating Trusted Advisor into your existing workflows.

The core checks and recommendations of Trusted Advisor are available for free to all AWS customers, while additional, more detailed checks are available for customers with Business or Enterprise support plans. As an AWS customer, you are encouraged to regularly review and act on the recommendations provided by Trusted Advisor, as it is one of the most effective tools for optimizing your AWS environment.


## AWS Pricing Calculator

**The AWS Pricing Calculator** is a tool that allows you to estimate the cost of using AWS services. It's a valuable resource for planning and budgeting as it helps you understand the financial impact of moving your workloads to AWS. It allows users to model their solutions before building them, explore the price points and options available, and estimate the total cost of utilizing specific AWS services.

**Here are some key features of the AWS Pricing Calculator**:

Customizable Templates: You can define the parameters of your AWS workload in the calculator by choosing from pre-set templates, or create your own configurations from scratch.

Detailed Breakdowns: The calculator provides a detailed cost breakdown, including monthly and annual costs for each service. This can be very helpful for understanding how different services contribute to your overall costs.

Cost Comparisons: You can compare the costs of different configurations or scenarios. This feature can help in decision making, such as choosing between different instance types, purchasing models (On-Demand, Savings Plans, or Reserved Instances), or different regions.

Export and Share: You can export the estimates to a CSV file for further analysis or share the estimates with others via a URL.

Inclusion of Discounts: The tool also takes into account any applicable discounts, such as those from reserved instances or savings plans.

Integration with Other AWS Tools: The AWS Pricing Calculator can be used in conjunction with other AWS tools, like AWS Budgets and AWS Cost Explorer, to manage your AWS costs more effectively.

To use the AWS Pricing Calculator, you define a project based on your needs, add products to your project, and then estimate the cost. Each product in a project includes one or more cost items, each of which maps to a pricing term in an AWS price list. The Pricing Calculator then uses this information to estimate cost.

Remember that while the AWS Pricing Calculator provides an estimate of costs, actual costs can vary based on usage and other factors. It's therefore always a good idea to monitor actual usage and costs using tools like AWS Cost Explorer.
