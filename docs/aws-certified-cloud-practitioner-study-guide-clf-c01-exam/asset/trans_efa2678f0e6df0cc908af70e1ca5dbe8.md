
-   [您可以通过在 AWS 服务 URL 末尾添加 `/pricing` 来在线查找定价信息。例如，`aws.amazon.com/s3/` (https://aws.amazon.com/s3/) 将变为 `aws.amazon.com/s3/pricing` (https://aws.amazon.com/s3/pricing)。了解计费费率以及用于衡量这些费率的具体指标很重要。

-   AWS Simple Monthly Calculator 和 AWS Total Cost of Ownership Calculator 让您能够预估实际使用的 AWS 部署费用，并在 TCO 计算器的情况下，将您的支出与其本地等效进行比较。

-   如果您的请求会导致您的使用量超过服务限制，则请求可能会被拒绝（并且启动会失败）。

-   AWS Billing Dashboard 是访问账户管理、支付和税务状态管理、成本监控以及成本控制的中心。

## Exam Essentials

**Understand the value of the 12-month Free Tier.** The Free Tier lets you run light services such as the `t2.micro` EC2 instance type and a 30 GB SSH EBS volume. The goal is to get you comfortable with the AWS environment so you can learn how it can be used to host your applications.

**Understand the value of permanent Free Tier services.** Low-volume consumption includes the retrieval of up to 10 GB of stored objects from Glacier or 62,000 outbound emails through Amazon SES. The goal is to give you the opportunity to launch proof-of-concept deployments.

**Know how to access Amazon’s resource pricing online documentation.** To accurately calculate the true costs of an AWS deployment, you must understand the pricing for the particular level of resource you launch within a particular AWS Region. Each service resource (like an EC2 instance) is billed by metrics unique to its characteristics.

**Use the AWS Simple Monthly Calculator to accurately model multitiered application stack pricing.** Pricing for all variations of the core AWS services is prebuilt into the calculator, allowing you to model pricing for multiple resource configurations.

**Use the AWS Total Cost of Ownership Calculator to compare on-premises with AWS deployment costs.** You can conveniently compare apples to apples—capital expenses for on-premises versus operating expenses for cloud—to know whether the AWS cloud is really right for your workload.

**Understand how your use of AWS services is limited by default.** Access to all service resources is restricted by default limits. In many cases, you can manually request limit increases from AWS support.

**Understand the value of cost management tools for avoiding costly cloud overspends.** AWS budgets can be configured to send alerts when your resource consumption approaches or passes a preset limit. Cost Explorer provides visualizations to more easily monitor historical and current costs. Cost and usage reports can send in-depth and ongoing CSV-formatted data to Redshift or QuickSight for analysis. You can use cost allocation tags to more effectively track and manage the source of account costs. The security and operations of multiple AWS accounts controlled by a single company can be managed through AWS Organizations.

## Review Questions

1.  Which of the following EC2 services can be used without charge under the Free Tier?

    1.  Any single EC2 instance type as long as it runs for less than one hour per day  
    2.  Any single EC2 instance type as long as it runs for less than 75 hours per month  
    3.  A single `t2.micro` EC2 instance type instance for 750 hours per month  
    4.  `t2.micro` EC2 instance type instances for a total of 750 hours per month  

2.  You want to experiment with deploying a web server on an EC2 instance. Which two of the following resources can you include to make that work while remaining within the Free Tier? (Select TWO.)

    1.  A 5 GB bucket on S3  
    2.  A `t2.micro` instance type EC2 instance  
    3.  A 30 GB solid-state Elastic Block Store (EBS) drive  
    4.  Two 20 GB solid-state Elastic Block Store (EBS) drives  

3.  Which of the following usage will always be cost-free even after your account’s Free Tier has expired? (Select TWO.)

    1.  One million API calls/month on Amazon API Gateway  
    2.  10 GB of data retrievals from Amazon Glacier per month  
    3.  500 MB/month of free storage on the Amazon Elastic Container Registry (ECR)  
    4.  10 custom monitoring metrics and 10 alarms on Amazon CloudWatch  

4.  Which of the following tools are available to ensure you won’t accidentally run past your Free Tier limit and incur unwanted costs? (Select TWO.)

    1.  Automated email alerts when activity approaches the Free Tier limits  
    2.  The Top Free Tier Services by Usage section on the Billing & Cost Management Dashboard  
    3.  Billing & Cost Management section on the Top Free Tier Services Dashboard  
    4.  The Billing Preferences Dashboard  

5.  Which of the following is likely to be an accurate source of AWS pricing information?

    1.  Wikipedia pages relating to a particular service  
    2.  The AWS Command Line Interface (AWS CLI)  
    3.  AWS online documentation relating to a particular service  
    4.  The AWS Total Cost of Ownership Calculator  

6.  Which of the following will probably not affect the pricing for an AWS service?

    1.  Requests for raising the available service limit  
    2.  AWS Region  
    3.  The volume of data saved to an S3 bucket  
    4.  The volume of data egress from an Amazon Glacier vault  

7.  Which of the following is a limitation of the AWS Simple Monthly Calculator?

    1.  You can calculate resource use for only one service at a time.  
    2.  Not all v[user]][20[usercomes,[comescomes usersandings[user]2[user][1101[user][1101[user_1[comes[11101[useres][comes12[1comesuser][1121[121[121comes121comes121comes121[1211comesuser[1121112111211121112111211121112111211121[121112111<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><｜begin▁of▁sentence|>content
[/content]
