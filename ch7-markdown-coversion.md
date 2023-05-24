# Getting to Know Amazon Web Services (AWS) as of September 2021


## An Open Textbook

By Nicholas Elliott Karlson


# Chapter 7 - AWS Security, Identity & Compliance


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


# AWS Security, Identity & Compliance - Detail


## AWS Identity and Access Management

**AWS Identity and Access Management **(IAM) is a web service that helps you securely control access to AWS resources for your users. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

Here are some of the key features and aspects of AWS IAM:

1. Shared Access to Your AWS Account: IAM lets you grant other people permission to administer and use resources in your AWS account without having to share your password.

2. Granular Permissions: With IAM, you can grant different permissions to different people for different resources. For example, you might allow a group of administrators unrestricted access to your resources, while allowing other users only the ability to view and submit job data.

3. Multi-Factor Authentication (MFA): IAM supports multi-factor authentication for privileged accounts, including options for hardware and virtual MFA devices. This provides an extra layer of security for your AWS account.

4. Identity Federation: IAM allows you to enable identity federation to allow existing identities (users, groups, and roles) in your enterprise to access the AWS Management Console, AWS APIs, and resources, without the need to create an IAM user for each identity.

5. AWS STS Temporary Security Credentials: IAM can be used with Amazon Security Token Service (STS) to grant trusted users temporary and limited administrative permissions.

6. Integrated with Many AWS Services: IAM is integrated with most AWS services such as EC2, S3, DynamoDB, and RDS, which means you can use the same set of identities and permissions to manage access across many AWS services.

7. Policy Variables: IAM also allows you to use policy variables to tailor permissions to each user, allowing for easier and more efficient permission management.

8. AWS Identity Federation: This allows you to integrate IAM with your corporate directory to provide single sign-on access to the AWS Management Console.

9. Role-based Access Control: This allows you to assign permissions to a role and then grant that role to an AWS resource such as an EC2 instance.

In summary, IAM is a powerful tool that helps you manage access to your AWS resources, providing secure and granular control over who can do what with your resources. It integrates with numerous AWS services, offering a consistent and robust method for securing access to and control over your AWS environment.


## Amazon Cognito

**Amazon Cognito** is a service that makes it easy to add user sign-up, sign-in, and access control to your web and mobile apps. It scales to millions of users and supports sign-in with social networks, Active Directory, and user identity providers.

**Here are some of the key features and aspects of Amazon Cognito**:

1. User Pools: Amazon Cognito User Pools are user directories that provide sign-up and sign-in options for your app users. This includes support for user registration, authentication, account recovery, and other operations. When you create a User Pool, you're creating a fully managed user directory that can scale to hundreds of millions of users.

2. Identity Pools (Federated Identities): Amazon Cognito Identity Pools enable you to create unique identities for your users and federate them with identity providers. With an identity pool, you can obtain temporary, limited-privilege AWS credentials to access other AWS services. This is important for providing your users secure access to AWS resources, such as reading data from an Amazon S3 bucket, or updating a DynamoDB table.

3. Social and Enterprise Identity Federation: Cognito supports public identity providers like Google, Facebook, and Amazon, and also supports OpenID Connect (OIDC) and SAML 2.0 providers. You can use these providers with Cognito User Pools or Identity Pools.

4. User Data Synchronization: Amazon Cognito Sync allows you to synchronize user profile data across mobile devices and the web without requiring your own backend. The service supports offline access, syncing only when the device is online.

5. MFA (Multi-Factor Authentication): Cognito supports multi-factor authentication and encryption of data-at-rest and in-transit.

6. Customizable UI for User Experience: Cognito provides a customizable UI for user authentication that can be embedded directly into your web or mobile app.

7. App Integration: Cognito supports integration with Amazon Pinpoint for analytics and user engagement reporting.

In summary, Amazon Cognito is a robust user identity and authentication service that helps you secure and manage user data while also offering the flexibility to create, configure, and connect with user directories, identity providers, and other identity services.


## AWS Key Management Service

**AWS Key Management Service** (KMS) is a managed service that makes it easy for you to create and control the cryptographic keys used to encrypt your data. It's integrated with other AWS services to help protect the data you store in these services and the keys you manage in AWS KMS.

**Here are some of the key features and aspects of AWS KMS**:

1. Centralized Key Management: AWS KMS provides a centralized control point to manage cryptographic keys and control their use across a wide range of AWS services and in your applications.

2. Integrated with AWS Services: AWS KMS is integrated with AWS CloudTrail to provide logs of all key usage and helps meet your regulatory and compliance needs. It's also integrated with many other AWS services such as Amazon S3, Amazon EBS, Amazon RDS, Amazon Redshift, Amazon EMR, AWS Lambda, and many more, to help protect data stored in these services.

3. Regulatory Compliance: AWS KMS is designed so that no one, including AWS employees, can retrieve your plaintext keys. KMS keys are stored in hardware security modules (HSMs) that are validated under FIPS 140-2, or are protected by FIPS 140-2 validated HSMs.

4. Customer Master Keys (CMKs): In AWS KMS, you work with customer master keys. You can either generate these keys in KMS, or import them from your own key management infrastructure.

5. Envelope Encryption: AWS KMS uses envelope encryption, which means data keys are used to encrypt data. Data keys are then encrypted using a customer master key (CMK), and stored with the encrypted data. When data needs to be decrypted, the process is reversed.

6. Key Rotation: AWS KMS supports automatic key rotation, which creates new cryptographic material for CMKs every year.

7. Access Control: You can control who can manage and use your keys by defining IAM policies, key policies, and grants.

8. Multi-Region Key Replication: KMS allows for multi-Region key replication, enabling you to replicate keys from one AWS region to another.

In summary, AWS KMS offers a robust, secure, and scalable mechanism for managing cryptographic keys, with comprehensive logging and control features that ensure compliance with stringent regulatory standards. By integrating with a wide range of AWS services, KMS allows you to add an extra layer of security to data stored within the AWS ecosystem.


## Amazon Macie

**Amazon Macie** is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS. It automatically provides an inventory of Amazon S3 buckets including a list of unencrypted buckets, publicly accessible buckets, and buckets shared with AWS accounts outside those you have defined in AWS Organizations.

**Here are some of the key features and aspects of Amazon Macie**:

1. Data Discovery: Macie automatically discovers and classifies data stored in Amazon S3. It uses machine learning and pattern matching to identify sensitive data such as personally identifiable information (PII). It provides visibility into where this data is located and how it's being accessed, along with additional context about the data to help you assess its risk level.

2. Data Protection: By continuously monitoring data access activity for anomalies, Macie can detect unusual data access patterns or uncharacteristic user behavior. This could include large data transfers or irregular access patterns, which might indicate a data breach or misuse of credentials.

3. Risk Assessment: Macie provides an overall risk rating for each S3 bucket, which combines the bucket’s permissions settings, encryption settings, and other information to assess its level of risk.

4. Compliance Assistance: Macie can help meet regulatory compliance requirements by providing a detailed inventory of your Amazon S3 buckets along with automatic alerts for any policy-defined issues. It includes support for standards and regulations like the General Data Protection Regulation (GDPR) and the California Consumer Privacy Act (CCPA).

5. Security Automation: You can create security automation workflows based on findings in Macie. For instance, if Macie discovers unencrypted sensitive data in S3 buckets, you can create a Lambda function to automatically encrypt that data.

6. Integration with AWS Services: Macie integrates with other AWS services like AWS CloudTrail to analyze event data and provide detailed information about API calls.

In summary, Amazon Macie is a powerful tool for securing sensitive data in the cloud. It uses advanced machine learning and pattern matching techniques to discover and protect sensitive data, helping organizations meet their security and privacy obligations.


## Amazon GuardDuty

**Amazon GuardDuty** is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts, workloads, and data stored in Amazon S3. It uses machine learning, anomaly detection, and integrated threat intelligence to identify and prioritize potential threats.

**Here are some key features and aspects of Amazon GuardDuty**:

1. Intelligent Threat Detection: GuardDuty identifies unusual or unauthorized activity, such as cryptocurrency mining, credential compromise behavior, communication with known command-and-control servers, or API calls from known malicious IPs. It uses machine learning to detect anomalous behavior that could indicate a threat.

2. Integrated Threat Intelligence: GuardDuty uses threat intelligence feeds, such as lists of known malicious IP addresses and domains, and it applies machine learning to detect threats. This includes integration with AWS Security Hub to consolidate security alerts and findings from multiple AWS services.

3. Easy to Enable: GuardDuty can be enabled with just a few clicks in the AWS Management Console. Once enabled, it immediately starts analyzing billions of events across your AWS accounts for signs of risk.

4. Continuous Monitoring: GuardDuty operates continuously and is always up-to-date. It doesn't rely on static threat lists and is continually fine-tuned using machine learning to adapt to new threats and malicious behaviors.

5. Account and Resource Agnostic: GuardDuty is designed to provide a consistent view of threat activity across all your AWS accounts, regardless of their size or the region in which they operate. It also works across AWS workloads and services to detect threats and unauthorized behavior.

6. Automated Notifications: GuardDuty can send notifications to AWS CloudWatch Events when it identifies findings. This allows you to automate responses and remediation actions, or generate alerts for quick incident response.

7. Low Impact: GuardDuty is designed to have no impact on your AWS workloads, because it does not require any agents or sensors to be installed, and it does not affect the performance or reliability of your applications.

In summary, Amazon GuardDuty is a powerful and intelligent threat detection service that makes it easy to secure your AWS accounts and workloads. With its machine learning capabilities, continuous monitoring, and easy setup, GuardDuty can significantly enhance your organization's security posture on AWS.


## AWS Security Hub

**AWS Security Hub** is a service that gives you a comprehensive view of your high-priority security alerts and security status across your AWS accounts. It provides a central place where you can monitor your security and compliance situation, with data from AWS services and other tools.

**Here are some of the key features and aspects of AWS Security Hub**:

1. Centralized Security and Compliance View: AWS Security Hub aggregates findings from AWS services like Amazon GuardDuty, Amazon Inspector, Amazon Macie, AWS Firewall Manager, and AWS IAM Access Analyzer. It also integrates with a wide range of security solutions from AWS partners. It provides a unified, organized, and prioritized set of these findings in one place.

2. Automated Compliance Checks: AWS Security Hub runs continuous, automated configuration and compliance checks based on industry standards and best practices, such as the Center for Internet Security (CIS) AWS Foundations Benchmark. The service aggregates the results of these checks across all of your accounts and Regions into a single dashboard.

3. Integrated Dashboard: Security Hub presents the results using integrated dashboards that include graphical security cards. These cards provide high-level summaries of your security and compliance status, and they include actionable findings for each relevant resource.

4. Insights and Trends: The service includes built-in "insights" which are correlated sets of related findings. They provide a high-level summary of potential issues, trends, and patterns, helping you to understand the security posture of your environment.

5. Custom Actions: You can take specific actions on findings by selecting them and choosing a custom action. When you define a custom action, Security Hub publishes an event to Amazon CloudWatch Events. You can configure various AWS resources, like AWS Lambda, to listen and respond to this event.

6. Cross-Account Management: Security Hub allows you to manage security and compliance across multiple AWS accounts. You can enable AWS Security Hub in a master account and invite member accounts to join. The master account can then view findings from the member accounts.

In summary, AWS Security Hub provides a centralized, comprehensive, and standardized approach to managing security and compliance across your AWS environment. It simplifies security management by providing an overview of high-priority alerts and compliance status, and it offers a single place to enable and manage other AWS security services.


## AWS Secrets Manager

**AWS Secrets Manager** is a secrets management service that helps you protect access to your applications, services, and IT resources. This service enables you to easily rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle.

**Here are some of the key features and aspects of AWS Secrets Manager**:

1. Secure and Manage Secrets: Secrets Manager helps you secure and manage secrets used to access resources in the AWS Cloud, on third-party services, and on-premises. It can store database credentials, on-premises resource credentials, SaaS application credentials, third-party API keys, and Secure Shell (SSH) keys.

2. Secret Rotation: One of the significant features of AWS Secrets Manager is its built-in support for secret rotation. Secrets Manager makes it easier to follow security best practices by enabling you to replace secrets periodically without impacting your applications.

3. Centralized Management: Secrets Manager provides a single console for managing secrets. This makes it easier to govern access to secrets and meet your compliance requirements.

4. Integration with AWS Services: AWS Secrets Manager integrates with other AWS services. For instance, AWS Identity and Access Management (IAM) policies allow you to control who can access your secrets. It also integrates with AWS CloudTrail to enable auditing of secrets' usage.

5. Programmatically Retrieve Secrets: Applications can programmatically retrieve secrets using the Secrets Manager APIs, eliminating the need to hardcode sensitive information in plain text.

6. Disaster Recovery: Secrets Manager helps protect access to your applications, services, and IT resources without upfront investment and on-going maintenance costs of operating your infrastructure.

In summary, AWS Secrets Manager allows for easy management of secrets, providing a central source of truth, automatic secret rotation, and tight integration with other AWS services. This simplifies the task of managing the lifecycle of secrets while also enhancing the security posture by limiting the potential for unauthorized access or leakage of sensitive credentials.


## AWS Inspector

**AWS Inspector** is a security vulnerability assessment service that helps improve the security and compliance of applications deployed on AWS. It automatically assesses applications for vulnerabilities or deviations from best practices, including exposed access keys or insecure configurations.

**Here are some of the key features and aspects of AWS Inspector**:

1. Automated Security Assessment: AWS Inspector automatically assesses a set of predefined rules against the AWS resources and applications to identify potential security issues or vulnerabilities. These rules are based on AWS best practices and common compliance standards.

2. Detailed Reports: After performing an assessment, AWS Inspector provides a detailed list of security findings prioritized by level of severity. These reports can provide detailed descriptions of the security issues found, suggest possible remediation steps, and offer recommendations for improving the security of the assessed resources.

3. Integration with Other AWS Services: AWS Inspector can be used in conjunction with other AWS services. For example, it can send reports and notifications through Amazon Simple Notification Service (SNS), and its findings can be stored and analyzed in Amazon Simple Storage Service (S3).

4. Flexible Assessments: AWS Inspector allows for both on-demand and scheduled assessments. You can run security assessments as needed or on a regular schedule, depending on your organization's needs.

5. Rule Packages: AWS Inspector uses rule packages, which are collections of security checks. AWS provides several built-in rule packages, and you can also create your own. These rule packages can include checks for networking configurations, authentication mechanisms, application behaviors, and more.

6. Agent-Based and Agentless Assessments: AWS Inspector can perform both agent-based and agentless assessments. Agent-based assessments require the AWS Inspector Agent to be installed on the target instance, while agentless assessments can be performed using AWS APIs.

In summary, AWS Inspector is a powerful tool for enhancing the security of your AWS resources. It automates the process of finding potential security issues, helping you to proactively improve your security posture and comply with regulatory standards.


## Amazon Detective

**Amazon Detective** is an AWS service that helps make it easier to analyze, investigate, and quickly identify the root cause of potential security issues or suspicious activities. Amazon Detective automatically collects log data from your AWS resources and uses machine learning, statistical analysis, and graph theory to build interactive visualizations that help you conduct faster and more efficient security investigations.

**Here are some of the key features and aspects of Amazon Detective**:

1. Data Aggregation and Analysis: Amazon Detective automatically aggregates data from AWS CloudTrail, Amazon VPC Flow Logs, and Amazon GuardDuty findings. It normalizes and correlates this disparate data and presents it as a unified view, enabling easy analysis.

2. Visualizations and Graphical User Interface: Amazon Detective uses machine learning models to generate graphical representations of your resource behaviors, their interactions over time, and how they compare to past behavior. This graphical visualization helps in understanding complex relationships and identifying anomalous activities.

3. Anomaly Detection: Amazon Detective helps identify unusual behavior and outliers, which may indicate unauthorized or malicious activity. It uses machine learning models to establish a baseline for normal account behavior and then highlights deviations from this baseline.

4. Efficient Investigations: Amazon Detective simplifies the investigation process. It automatically creates a "murder mystery"-like storyline linked to the selected findings. Each point in the storyline represents a security event. Clicking on a point opens a detailed profile with related events, allowing investigators to understand the issue quickly.

5. Continuous Monitoring: Amazon Detective continuously monitors AWS telemetry sources to maintain an up-to-date view of resources and behaviors in your AWS environment. This aids in ongoing security analysis and helps identify security gaps.

6. No Data Retention Limits: Amazon Detective maintains up to a year of aggregated data, helping you conduct long-term trend analysis and investigate historical incidents.

In summary, Amazon Detective makes it easier to analyze and visualize security data, investigate incidents, find the root cause of issues, and quickly take corrective actions. It brings automation and machine learning to security incident investigation, reducing the typical time and effort required.


## AWS Single Sign-On

**AWS Single Sign-On** (SSO) is a cloud SSO service that makes it easy to centrally manage SSO access to multiple AWS accounts and business applications. With AWS SSO, users get one user portal for accessing all their assigned AWS accounts, cloud applications, and custom applications, using their existing corporate credentials.

**Here are some of the key features and aspects of AWS Single Sign-On**:

1. Centralized Access Management: AWS SSO simplifies management by allowing you to manage user access to AWS accounts and applications from one place. You can assign user permissions based on common job functions and can customize these permissions to meet specific needs.

2. SSO Access: AWS SSO provides a user portal where your users can find and access all their assigned AWS accounts, applications, and custom applications from a central location. Users sign in using their existing corporate credentials.

3. Integration with AWS Organizations: AWS SSO is integrated with AWS Organizations to enable you to manage access to AWS accounts in your organization. It simplifies the management of your AWS accounts by enabling you to manage access centrally.

4. Integration with Other Identity Sources: AWS SSO also integrates with Microsoft Active Directory, allowing you to authenticate users with their existing corporate credentials. It also supports automatic synchronization of users and groups from your Microsoft AD to AWS SSO.

5. Support for SAML 2.0: AWS SSO supports Security Assertion Markup Language (SAML) 2.0, enabling you to extend SSO access to your SAML-enabled applications.

6. Multi-Factor Authentication (MFA): AWS SSO supports MFA. This provides an extra layer of protection for your sensitive resources. When a user tries to access a resource, they must provide another piece of information in addition to their password.

7. Auditability: With AWS CloudTrail, you can log all AWS SSO events to monitor who is doing what, when, and from where. This provides you with a record of actions taken through AWS SSO for audit purposes.

In summary, AWS Single Sign-On is a centralized and flexible service that simplifies the management and control of access to AWS accounts and business applications. It enables users to use their existing credentials to access their resources through a user-friendly portal.


## AWS Certificate Manager

**AWS Certificate Manager** (ACM) is a service that allows you to easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services and your internal connected resources. SSL/TLS certificates are used to secure network communications and establish the identity of websites over the Internet as well as resources on private networks.

**Here are some of the key features and aspects of AWS Certificate Manager**:

1. Simplified Certificate Management: ACM removes the time-consuming manual process of purchasing, uploading, and renewing SSL/TLS certificates. With a few clicks in the AWS Management Console, you can provision a certificate, deploy it on ACM-integrated AWS resources, and let ACM handle certificate renewals.

2. Free Public Certificates: ACM provides public SSL/TLS certificates for your domains at no cost. These certificates can be used with ACM-integrated services, such as Elastic Load Balancers, Amazon CloudFront distributions, and APIs on API Gateway.

3. Private Certificate Authority: ACM Private Certificate Authority (CA) is a managed private CA service that helps you easily and securely manage the lifecycle of your private certificates. ACM Private CA provides you a highly-available private CA service without the upfront investment and on-going maintenance costs of operating your own private CA.

4. Integration with AWS Services: ACM is integrated with several AWS services to make it easier to enable SSL/TLS for a workload. Services that integrate with ACM include Elastic Load Balancing (ELB), Amazon CloudFront, Amazon API Gateway, and more.

5. Certificate Transparency: ACM publishes all new and renewed public SSL/TLS certificates to at least two public Certificate Transparency (CT) logs. This meets the requirements of Chrome, Safari, and Firefox which block certificates that are not in CT logs.

6. Automatic Certificate Renewal: ACM handles the complexity of creating and managing public SSL/TLS certificates for your AWS based websites and applications. This includes automated renewal processes to help avoid unexpected expiration notifications.

7. Wildcard Certificates and SANs: ACM allows the creation of wildcard certificates to protect multiple subdomains, and Subject Alternative Names (SANs) can be added to a certificate to protect multiple domains or subdomains.

In summary, AWS Certificate Manager is a key service for enhancing the security of your AWS hosted websites or applications, by simplifying and automating the management and deployment of SSL/TLS certificates.
