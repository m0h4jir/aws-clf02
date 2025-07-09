# **4. AWS Costs, Economics and Billing Practices**

**4.1 Compare and contrast the various pricing models for AWS**

* [EC2 Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html) are [priced](https://aws.amazon.com/ec2/pricing/) as follows
    * On-Demand: EC2 capacity billed to the second.
        * Pay for what you use.
        * Use case: When Applications are under development, or workloads are not expected to run for more than a year, no upfront payment or long-term committment, unpredictable workloads but don't want to be interrupted.
        * On-Demand Capacity Reservation: It is possible to buy upfront capacity to mitigate against capacity contraints in an availability zone (AZ).
    * Spot: unused EC2 capacity on sale.
        * Pay the least but no guarantee of runtimes or interruptions. A 2-minute warning is provided via instance meta-data that your application should check for and prepare for shutdown.
        * Use case: Start and stop time of the workload does not matter. 90% savings over On-Demand. When your workload is feasable only at the lowest price points. 
        * Spot price in effect at the beginning of each hour.
    * Reserved: Upfront capacity reservation committment for long running workloads.
        * Pay upfront with a contract to get discounts.
        * Use case: Save 75% versus On-Demand and willing to pay upfront for 1 or 3 year reservation. 
        * Flexibility: All upfront, partial upfront or no upfront is possible. A contract is required. Provides convertible types at 54% discount - change tenancy, OS or region.
    * Dedicated Instance and Dedicated Host: 
        * [Dedicated Host](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-hosts-overview.html): Dedicated bare metal rental and host exclusively for you to install software that have licensing tied to host size.
        * [Dedicated Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-instance.html): Instances run on VPCs on a hardware dedicated to a single customer.
        * Use Case: Save 70% off of On-Demand. Software that is licensed based on per-core, per-socket or per-VM. Regulations that require tenancy exclusivity.
        * Dedidicated host is a physical server, dedicated instance runs on a host.
    * Savings Plan: Compute usage committment for 1 or 3 years applicable across multiple compute services.
        * Save upto 72% off of On-Demand.
        * Use Case: For flexibility across various services like Lambda, Fargate, and EC2.
        * This is a billing convenience nothing to do with a capacity reservation.
* Lambda Pricing
    * Computer Time - no charge for times that code is not running.
    * Duration - duration of compute and memory usage while execution is counted.
    * Free Tier - the free tier includes 1 million free requests each month
* S3 Pricing
    * Storage Class
    * Storage - number of items, and size.
    * Data transfer - outbound.
    * Request and data retrieval - number of requests made.
* RDS Pricing
    * Running Clock Hours
    * Type of Database - brand, size, memory class etc
    * Storage - amount of data
    * Purchase type - on-demand, reserved instance
    * DB count - number of instance
    * API - number of calls
    * Deployment type - is it multi-AZ
    * Outbound - data transfer

**4.2 Recognize the various account structures in relation to AWS billing and pricing**

Compute, storage and outbound data transfer is where the costs are for AWS. Data in flight moving between system. Data movement within the AWS region are usually not charged. Data out of AWS to end user is where the data transfer costs are.
   
How AWS Pricing Works [whitepaper](https://docs.aws.amazon.com/pdfs/whitepapers/latest/how-aws-pricing-works/how-aws-pricing-works.pdf)

* [TCO](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/aws-pricingtco-tools.html) 
        * Total Cost of Ownership. Direct and indirect cost of running AWS workloads. How can I reduce my TCO using AWS?
        * Minimize capital expenditures.
        * Utilize reserved instances.
        * Right size your resources.
        * Does not consider Networking or Data costs. No personnel or facilities costs.
* [AWS Price List API](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/price-changes.html)
        * Query the price of AWS Services using JSON or CSV. Bulk price or individual APIs.
        * Receive price alerts when prices change.
* [Application Disovery Service](https://docs.aws.amazon.com/application-discovery/latest/userguide/what-is-appdiscovery.html)
        * Determine the cost of migrating to the cloud.
        * Plan migration projects and estimate TCO.
        * You can view the discovered servers, group them into applications, and then track the migration status of each application from the Migration Hub console in your home Region.
* [Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)
        * Set custom budgets for cost and usage tracking. Alerts.
        * Cost, usage and reservation budgets.
        * You can choose to be notified through email and Amazon SNS topics when your utilization drops below 80 percent for a given day.
* [Cost and Usage Reports](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html)
        * Break down costs by the hour, day, or month, by product or product resource, or by tags that you define yourself.
        * If you get a huge bill - this is where you need to find the needle in the haystack.
        * Downloadable detailed and comprehensive report, list usage for each service category and aggregate usage data on a daily, hourly or monthly level.
        * Cost Allocation Tags
            * Label resources using key-value pairrs.
            * Track costs via the cost allocation report.
* [Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)
        * Visualize, understand, and manage your AWS costs and usage over time.
        * Forecast, build custom apps that use it's apis, and use granular filtering offered by it's analytical engine.
* [Organizations](https://aws.amazon.com/organizations/)
        * Centrally manage your environment as you scale your AWS resources. Consolidate billing, save costs via volume discounts + reserved instance sharing and govern accounts centrally.
        * Programmatically create AWS accounts as you scale at no additional charge.
        * Centrally secure and audit. Manage and optimize costs centrally. Group accounts and apply policies across.
        * Root Organization is the master payer account that pays for all the accounts. 
        * You can apply Service Control Policies (SCPs) across all member accounts within the organization.
* [Control Tower](https://aws.amazon.com/controltower/)
        * Set up well-architected multi-account environments with pre-configured controls to ensure best practices.
        * Provides dashboard to help manage accounts.
        * Example, if you want to disallow public write access to all S3 buckets across your accounts - you can use Control Tower to enforce this.
* [Systems Manager](https://aws.amazon.com/systems-manager/)
        * Operation insights into AWS resources, other cloud resources and on-prem resources.
        * Automate configuration and ongoing management including instance compliance relative to patch, configuration and custom policies.
        * Visibility and control. Group resources to take action. Patch and run commands on multiple EC2 and RDS.
        * Usecase: Deploy operating system and software patchs automatically across a large group of instances. 
* [Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/)
        * Cost, Performance, Security, Fault Tolerance, and Service Limits.
        * Checks IAM password policy (not free). RDS public snapshot, service usage greater than 80% (available to business or enterprise). Check for exposed access keys (business support) and various other checks.
        * Use case: check read and write capacity service limits for DynamoDB.
* [Personal Health Dashboard](https://aws.amazon.com/premiumsupport/technology/aws-health-dashboard/)
        * Alerts you on impacts to your AWS environment.
* [Marketplace](https://aws.amazon.com/marketplace)
        * Digital catalog of prebuilt solutions you can purchase or license.
* [AWS Partner Network (APN)](https://aws.amazon.com/partners/)
        * Global community of approved partners that offer solutions and consulting services
        * Help design and build a new application.
* [Managed Services](https://aws.amazon.com/managed-services/)
        * Augment internall staff with additional resources to manage AWS.
        * Patch management, monitoring, event management, cost optimization etc.
        * Will not operate or configur your applications.
* [Professional Services](https://aws.amazon.com/professional-services/)
        * Move to a cloud based operating model
        * Propose solutions.
        * Architect soutions.
        * You can quickly move from on-prem to cloud.
* [AWS License Manager](https://aws.amazon.com/license-manager/)
        * AWS and on-premise license manager.
        * Fine-tune your license costs.

 ### **Consolidated Billing**:

You can use the **consolidated billing** feature in AWS Organizations to consolidate billing and payment for multiple AWS accounts or multiple Amazon Internet Services Pvt. Ltd (AISPL) accounts. Every organization in AWS Organizations has a *master account* that pays the charges of all the *member accounts*. The master account is also called a payer account, and the member account is also known as a linked account.

Consolidated billing has the following benefits:

**One bill** – You get one bill for multiple accounts.

**Easy tracking** – You can track the charges across multiple accounts and download the combined cost and usage data.

**Combined usage** – You can combine the usage across all accounts in the organization to share the volume pricing discounts and Reserved Instance discounts. This can result in a lower charge for your project, department, or company than with individual standalone accounts.

**No extra fee** – Consolidated billing is offered at no additional cost.

If you have access to the payer account, you can see a combined view of the AWS charges that the linked accounts incur. You also can get a cost report for each linked account. AWS and AISPL accounts can’t be consolidated together. If your contact address is in India, you can use AWS Organizations to consolidate AISPL accounts within your organization.

When a linked account leaves an organization, the linked account can no longer access Cost Explorer data that was generated when the account was in the organization. The data isn’t deleted, and the payer account in the organization can still access the data. If the linked account rejoins the organization, the linked account can access the data again.

**Consolidated Billing** allows multiple AWS accounts to be billed together, offering several benefits:

- **Centralized Payment**: Instead of receiving individual bills for each AWS account, a single bill is generated for all accounts under a master account.
- **Volume Discounts**: By combining usage across accounts, consolidated billing can unlock volume-based discounts (such as for EC2 instances, S3 storage, etc.).
- **Cost Visibility**: The consolidated bill provides a comprehensive view of total usage and costs, with detailed breakdowns per account and service. This helps in understanding overall spending.
- **Simplified Billing Management**: It reduces administrative overhead by centralizing payments and reducing the number of invoices.
  
**4.3 Identify resources available for billing support**

 ## [Support Plans](https://aws.amazon.com/premiumsupport/plans/)
 
 ### **1. Basic Support (Free)**

- **Role**:
    - Self-service access to AWS documentation, whitepapers, and forums.
    - Basic account and billing support (e.g., payment issues).
    - Service health dashboards for outage monitoring.
- **Best For**:
    - Personal projects, experimentation, or non-critical workloads.
    - Users comfortable troubleshooting without direct AWS assistance.

---

### **2. Developer Support ($29+/month)**

- **Role**:
    - Email support during business hours (e.g., 9 AM–5 PM in your timezone).
    - Guidance for development/test environments (non-production).
    - Response times:
        - < 24 hours for **non-critical** issues.
        - No SLA for urgent issues.
- **Key Features**:
    - Limited Trusted Advisor checks (7 core checks).
    - Access to AWS Support API for programmatic case management.
- **Best For**:
    - Developers or small teams building/test environments.
    - Early-stage startups with limited budgets.

---

### **3. Business Support ($100+/month + usage-based)**

- **Role**:
    - 24/7 support via email, phone, and chat for **production workloads**.
    - Architectural guidance (e.g., optimizing costs, performance).
    - Response times:
        - < 1 hour for **urgent** issues (e.g., production system down).
        - < 24 hours for non-critical issues.
- **Key Features**:
    - Full access to **Trusted Advisor** (all checks for cost, security, performance).
    - Infrastructure Event Management (IEM) for event planning (additional fee).
    - Third-party software support (e.g., OS, libraries).
- **Best For**:
    - Production environments requiring reliable uptime.
    - Mid-sized businesses with SLA-driven needs.

---

### **4. Enterprise Support (Custom Pricing)**

- **Role**:
    - **Mission-critical support** with a dedicated **Technical Account Manager (TAM)**.
    - Proactive monitoring, guidance, and quarterly reviews.
    - Response times:
        - < 15 minutes for **business-critical** system-down scenarios.
        - < 1 hour for urgent issues.
- **Key Features**:
    - **Concierge Support Team**: Assists with billing and account escalations.
    - **Infrastructure Reviews**: Regular assessments of security, performance, and architecture.
    - **Operations Support**: Assistance with third-party tools (e.g., Kubernetes, Jenkins).
    - **Training and Workshops**: Customized sessions for your team.
- **Best For**:
    - Large enterprises with complex, high-availability architectures.
    - Regulated industries (e.g., healthcare, finance) requiring compliance guidance.

 ##  [BACK](./03-Cloud_Technology_and_Services.md)  |  [NEXT](./README.md)
