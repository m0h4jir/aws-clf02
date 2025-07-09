
# **1. Cloud Concepts**

## **1.1 Define the AWS Cloud and its value proposition**
    
**Cost Saving**: Running Data Centers ⇒ Focusing on Users and apps
    - Focus on projects that differentiate your business, not the infrastructure. Cloud computing lets you focus on your own customers, rather than on the heavy lifting of racking, stacking, and powering servers.
    
**Variable Expenses:** Upfront Expenses ⇒ Variable Expenses
    - Instead of having to invest heavily in data centers and servers before you know how you’re going to use them, you can pay only when you consume computing resources, and pay only for how much you consume.
    
**Elasticity / Scability**: Guessing Capacity Sizing ⇒ Scaling in/out as required 
     - Stop guessing capacity – Eliminate guessing on your infrastructure capacity needs. When you make a capacity decision prior to deploying an application, you often end up either sitting on expensive idle resources or dealing with limited capacity. With cloud computing, these problems go away. You can access as much or as little capacity as you need, and scale up and down as required with only a few minutes’ notice.
    
**Economies of Scale:** Smaller scale ⇒ Economies of scale
    - By using cloud computing, you can achieve a lower variable cost than you can get on your own. Because usage from hundreds of thousands of customers is aggregated in the cloud, providers such as AWS can achieve higher economies of scale, which translates into lower pay as-you-go prices.
    
**Speed/ Agility**:  Months of waiting time ⇒ Few Mins!
    - In a cloud computing environment, new IT resources are only a click away, which means that you reduce the time to make those resources available to your developers from weeks to just minutes. This results in a dramatic increase in agility for the organization, since the cost and time it takes to experiment and develop is significantly lower.
    
    focus your valuable IT resources on developing application

**Global in minutes**: build new DC  ⇒ Go Global in Mins
    - Easily deploy your application in multiple regions around the world with just a few clicks. This means you can provide lower latency and a better experience for your customers at minimal cost.
        
    On-Premise: Private Cloud (Data Center)
    Hybrid : (On-Premise+Public Cloud)
    Cloud: Public Cloud (AWS,Azure, GCP,etc.)
    

The **pay-as-you-go (PAYG)** pricing model is a flexible, usage-based approach where costs are directly tied to consumption. Here's a structured breakdown:

- **Usage-Based Billing**
- **No Upfront Costs or Long-Term Commitments**
- **Granular Pricing**
    
 [For more details, visit AWS Cloud Computing](https://aws.amazon.com/what-is-cloud-computing/?pg=TOCC)   
## **1.2 Identify aspects of AWS Cloud economics**

**Total Cost of Ownership (TCO) in AWS**
    
    - **Direct Costs**:
        - AWS service charges (e.g., EC2, S3, RDS, Lambda).
        - Data transfer/egress fees.
        - Support plans (e.g., Business/Enterprise Support).
    - **Indirect Costs**:
        - Migration costs (tools, labor, downtime).
        - Training for cloud teams.
        - Compliance/security management.
    - **Avoided Costs** (vs. on-premises):
        - No upfront hardware purchases (CapEx).
        - Reduced power, cooling, and physical data center costs.
        - No hardware maintenance or refresh cycles.
    
**OpEx in AWS**
    
    **Pros**:
    
    - **Flexibility**: Scale resources up/down with demand.
    - **No Upfront Costs**: Aligns expenses with revenue.
    - **Reduced Overhead**: AWS handles maintenance, security patches, and hardware refreshes.
    
    **Cons**:
    
    - Unoptimized usage can lead to cost overruns (e.g., idle EC2 instances).
    - Data egress fees can add up for hybrid/multi-cloud setups.
    
 **CapEx in AWS**
    
    **Pros**:
    
    - **Cost Savings**: Significant discounts for predictable workloads.
    - **Budget Predictability**: Lock in rates for long-term projects.
    
    **Cons**:
    
    - **Less Flexibility**: Commitments can lead to overprovisioning.
    - **Upfront Payments**: Ties up capital.
    
    - Recognize cost-saving opportunities (e.g., AWS Free Tier, Reserved Instances, and Spot Instances).

**Free Tier Types:**

Free Trials: RedShift 2 Month, SageMaker 2 Month, AppStream 2.0 40 Hours, etc..

12 months free: EC2 750 Hours per month, S3 5 GB of standard storage, etc…

Always Free: 1 Million free request per month, 25 GB DynamoDB of Storage, etc…

Three Types of Saving Plans:

1. EC2 Saving Plan:
2. Compute Saving Plan: apply to usage across EC2, Lambda, Fargate
3. SageMaker Savings Plan
4. Dedicated:
- Dedicated Instances: EC2 instances that run on hardware that’s dedicated to a single customer
- Dedicated Host: Physical EC2 server fully dedicated for your use “BYOL“

**1.3 List the different cloud architecture design principles**
    
 ### **AWS Well-Architected Framework:**
    
    Helps cloud architects build secure, high-performing, resilient, and efficient infrastructure for a variety of applications and workloads:
    
    Built around six pillars:

1. **Operational Excellence:**
        - **Principle:** run and monitor systems to deliver business value and to continually improve supporting processes and procedures.
        - **Key Strategies:**
            - Perform operations as code
            - Annotate documentation
            - Anticipate failure
            - Refine operations procedures frequently
            - Make frequent, small, reversible changes
2. **Security:**
        - **Principle:** Protect Information,systems, and assets while delivering business value through risk assessments and mitigation strategies
        - **Key Strategies:**
            - Automate security best practices
            - Apply security at all layers
            - Protect data in transit and at rest
3. **Reliability:**
        - **Principle:** Test recovery procedures, scale horizontally to increase aggregate system availability, and automatically recover from failure
        - **Key Strategies:**
            - **Recover from infrastructure or service disruptions**
            - Dynamically acquire computing resources to meet demand
            - Test Recovery procedures
            - Scale horizontally to increase aggregate workload availability
4. **Performance Efficiency:**
        - **Principle:** Use computing resources efficiently to meet system requirements and maintain that efficiency as demand changes and technologies evolve
        - **Key Strategies:**
            - Go Global in minutes
            - Experiment more often
            - Use Serverless architectures
5. **Cost Optimization:**
        - **Principle:** Run systems to deliver business value at the lowest price point
        - **Key Strategies**:
            - Adopt a consumption model
            - **Stop spending money on undifferentiated heavy lifting**
            - Analyze and attribute expenditure
6. **Sustainability**:
        - **Principle:** Minimize the environmental impacts of running cloud workloads
        - **Key Strategies**:
            - Understand your impact
            - **Maximize utilization**
            - Reduce the downstream impact of workload
            - Establish sustainability goals

Fault tolerance and disaster recovery are critical aspects of designing and managing AWS infrastructure to ensure high availability, data integrity, and business continuity. Here’s why they are important:

### **1. Fault Tolerance in AWS**

**Fault tolerance** refers to a system’s ability to continue operating despite failures in components such as servers, networks, or storage. AWS provides various tools and strategies to achieve fault tolerance, including:

- **Multi-AZ Deployments:** Services like Amazon RDS, DynamoDB, and Elastic Load Balancing (ELB) can distribute workloads across multiple Availability Zones (AZs) to ensure minimal downtime.
- **Auto Scaling:** EC2 Auto Scaling automatically replaces unhealthy instances to maintain performance and availability.
- **Elastic Load Balancing (ELB):** Distributes traffic across multiple instances to prevent single points of failure.
- **AWS Lambda & Serverless Architectures:** Reduce reliance on single servers by running code in response to events without infrastructure management.

### **2. Disaster Recovery in AWS**

**Disaster recovery (DR)** focuses on restoring data, applications, and services after a major failure or catastrophic event. AWS offers various DR strategies:

- **Backup & Restore:** Using Amazon S3, S3 Glacier, or AWS Backup to store snapshots and backups for quick recovery. $
- **Pilot Light Approach:** Keeping critical systems running at minimal capacity, ready to scale up when needed. $$
- **Warm Standby:** Maintaining a scaled-down but fully functional version of the production environment, which can be quickly expanded. $$$
- **Multi-Region Deployment:** Deploying resources across multiple AWS Regions to withstand regional failures. $$$$

Companies Migrate to the AWS Cloud:

to improve their Service Level Agreements (SLAs) through High Availability, Reliability and Scability

to Reduce costs related to infrastructure, freeing the budget for reinvestment in other areas

### **2. Cloud Computing Models

AWS offers a range of cloud computing models, including:

1. **Infrastructure as a Service (IaaS)**: Examples include Amazon EC2, allowing you to manage virtualized infrastructure.

2. **Platform as a Service (PaaS)**: Services like AWS Cloud9 provide a platform for application development, simplifying the development process.

3. **Software as a Service (SaaS)**: Sagemaker is an example of SaaS, offering ready-to-use software solutions.

# **3. Cloud Adoption Framework**

Leverages AWS experience and best practices to help organizations digitally transform and accelerate their business outcomes through innovative use of AWS.

**Business**

- Business:

The *business* perspective focuses on ensuring that your cloud investments accelerate your digital transformation ambitions and business outcomes. It comprises eight capabilities shown in the following figure. Common stakeholders include the CEO, CFO, COO, CIO, and CTO.

- People:

The *people* perspective serves as a bridge between technology and business, accelerating the cloud journey to help organizations more rapidly evolve to a culture of continuous growth, learning, and where change becomes business-as-normal, with focus on culture, organizational structure, leadership, and workforce. This perspective comprises seven capabilities shown in the following figure. Common stakeholders include CIO, COO, CTO, cloud director, and cross-functional and enterprise-wide leaders.

- Governance:

The *governance* perspective focuses on orchestrating your cloud initiatives while maximizing organizational benefits and minimizing transformation-related risks. It comprises seven capabilities shown in the following figure. Common stakeholders include chief transformation officer, CIO, CTO, CFO, CDO, and CRO.

**Technical**

- Platform:

The *platform* perspective focuses on accelerating the delivery of your cloud workloads via an enterprise-grade, scalable, hybrid cloud environment. It comprises seven capabilities shown in the following figure. Common stakeholders include CTO, technology leaders, architects, and engineers.

- Security:

The *security* perspective helps you achieve the confidentiality, integrity, and availability of your data and cloud workloads. It comprises nine capabilities shown in the following figure. Common stakeholders include CISO, CCO, internal audit leaders, and security architects and engineers.

- Operations:

The *operations* perspective focuses on ensuring that cloud services are delivered at a level that is agreed upon with your business stakeholders. Automating and optimizing operations will allow you to effectively scale while improving the reliability of your workloads. This perspective comprises nine capabilities shown in the following figure. Common stakeholders include infrastructure and operations leaders, site reliability engineers, and information technology service managers.

# **4.Best Practice Architecting for the AWS cloud.** 

1. **Design for failure**:only encourages you to be a pessimist when designing architectures in the cloud; assume things will fail. In other words, you should always design, implement and deploy for automated recovery from failure.

2. **Decouple your components**: tells us that we should build components that do not have tight dependencies on each other, so that if one component were to die (fail), sleep (not respond) or remain busy (slow to respond) for some reason, the other components in the system are built so as to continue to work as if no failure is happening. The cloud reinforces the Service-Oriented Architecture (SOA) design principle that the more loosely coupled the components of the system, the bigger and better it scales.

3. **Implement elasticity**: this principle is primarily implemented by automating your deployment process and streamlining the configuration and build process of your architecture. This ensures that the system can scale without any human intervention.

4. **Think parallel**: the concept of parallelization when designing architectures in the cloud. It advocates to not only implement parallelization wherever possible but also automate it because the cloud allows you to create a repeatable process very easily.

The AWS-specific tactics for parallelization are:

- Multi-thread your Amazon S3 requests as detailed in the best practices paper.
- Multi-thread your Amazon SimpleDB GET and BATCHPUT requests.
- Create a JobFlow using the Amazon Elastic MapReduce Service for each of your daily batch processes (indexing, log analysis, etc.) which will compute the job in parallel and save time.
- Use the Elastic Load Balancing service and spread your load across multiple web app servers dynamically.

Global Services : CloudFront, IAM, STS, Route 53, WAF

Regional Services: AWS Batch, RDS, DyanamoDB, EFS

Zonal Services :  EC2, EBS

EFS, RDS  to deploy its high-frequency trading (HFT) application which will store constantly changing financial data in AWS and require low latency acces.

When a storage device reaches the end of its lifespan: AWS follows a strict decommissioning process as described in compliance procedures

**Amazon S3** is used as scalable object storage and not as a nonrelational database in itself.

S3 Glacier Flexible Retrieval: lowest-cost storage option for retaining database  backups

Amazon DynamoDB: This is the perfect database to use for JSON-type documents.

Amazon Aurora: suitable for launching a highly scalabe MySQL OLTP Database

Internet Gateway: enable instances in the public subnet to connect to the public internet

An **Amazon VPC Site-to-Site VPN connection** can link your data center (or network) to your Amazon Virtual Private Cloud (VPC). A *customer gateway* is an anchor on your side of that connection. It can be a physical or software appliance. The anchor on the AWS side of the VPN connection is called a *virtual private gateway*.

From time to time, AWS also performs routine maintenance on the virtual private gateway, which may briefly disable one of the two tunnels of your VPN connection. Your VPN connection automatically fails over to the second tunnel while this maintenance is performed. When you configure your customer gateway, it’s therefore important that you configure both tunnels.

**Amazon Route 53** is a highly available and scalable cloud Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost-effective way to route end users to Internet applications by translating names like www.tutorialsdojo.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other.

This service can also help you create a hybrid cloud architecture using the Amazon Route 53 Resolver, which provides recursive DNS for your Amazon VPC and on-premises networks over AWS Direct Connect or a VPN solution.

**Amazon Aurora** is a MySQL and PostgreSQL-compatible relational database built for the cloud that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open-source databases.

Amazon Aurora is up to five times faster than standard MySQL databases and three times faster than standard PostgreSQL databases. It provides the security, availability, and reliability of commercial databases at 1/10th the cost. Amazon Aurora is fully managed by Amazon Relational Database Service (RDS), which automates time-consuming administration tasks like hardware provisioning, database setup, patching, and backups.

[Your journey into AWS continues to the next section](./02-Security_and_Compliance.md)