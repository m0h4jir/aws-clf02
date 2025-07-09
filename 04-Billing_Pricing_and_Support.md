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

 
**4.3 Identify resources available for billing support**

 ## [Support Plans](https://aws.amazon.com/premiumsupport/plans/)
 
   1. Basic - free. 
    * Email support only and discussion forums.
   1. Developer - $29 pm : 
    * Fordevelopment and testing. 
    * 1 contact. 
    * Cloud support associate via email during business hours.
   1. Business - $100 pm : 
    * Production workloads. 
    * Unlimited contact.
    * Full Trusted Advisory. 
    * Email, phone and chat 24/7. Production system down - less than one hour.
   1. Enterprise - $15k pm
    * Mission-critical production workloads. 
    * Exclusive: Technical Account Manager, Concierge support team, infrastructure event support. 
    * Less than 15m for business critical system down.

 ##  [BACK](./03-Cloud_Technology_and_Services.md)  |  [NEXT](./README.md)
