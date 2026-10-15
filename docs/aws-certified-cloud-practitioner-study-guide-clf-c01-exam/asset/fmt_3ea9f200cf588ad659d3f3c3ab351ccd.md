
1. It can make infrastructure more fault tolerant.

2. It can make applications available to end users with lower latency.

3. It can make applications more compliant with local regulations.

4. It can bring down the price of running.

7. Why is it that most AWS resources are tied to a single region?

1. Because those resources are run on a physical device, and that device must live somewhere

2. Because security considerations are best served by restricting access to a single physical location

3. Because access to any one digital resource must always occur through a single physical gateway

4. Because spreading them too far afield would introduce latency issues

8. You want to improve the resilience of your EC2 web server. Which of the following is the most effective and efficient approach?

1. Launch parallel, load-balanced instances in multiple AWS Regions.

2. Launch parallel, load-balanced instances in multiple Availability Zones within a single AWS Region.

3. Launch parallel, autoscaled instances in multiple AWS Regions.

4. Launch parallel, autoscaled instances in multiple Availability Zones within a single AWS Region.

9. Which of the following is the most accurate description of an AWS Availability Zone?

1. One or more independently powered data centers running a wide range of hardware host types

2. One or more independently powered data centers running a uniform hardware host type

3. All the data centers located within a broad geographic area

4. The infrastructure running within a single physical data center

10. Which of the following most accurately describes a subnet within the AWS ecosystem?

1. The virtual limits imposed on the network access permitted to a resource instance

2. The block of IP addresses assigned for use within a single region

3. The block of IP addresses assigned for use within a single Availability Zone

4. The networking hardware used within a single Availability Zone

11. What determines the order by which subnets/AZ options are displayed in EC2 configuration dialogs?

1. Alphabetical order

2. They (appear) to be displayed in random order.

3. Numerical order

4. By order of capacity, with largest capacity first

12. What is the primary goal of autoscaling?

1. To ensure the long-term reliability of a particular physical resource

2. To ensure the long-term reliability of a particular virtual resource

3. To orchestrate the use of multiple parallel resources to direct incoming user requests

4. To ensure that a predefined service level is maintained regardless of external demand or instance failures

13. Which of the following design strategies is *most* effective for maintaining the reliability of a cloud application?

1. Resource isolation

2. Resource automation

3. Resource redundancy

4. Resource geolocation

14. Which of the following AWS services are *not likely* to benefit from Amazon edge locations? (Select TWO.)

1. RDS

2. EC2 load balancers

3. Elastic Block Store (EBS)

4. CloudFront

15. Which of the following is the primary benefit of using CloudFront distributions?

1. Automated protection from mass email campaigns

2. Greater availability through redundancy

3. Greater security through data encryption

4. Reduced latency access to your content no matter where your end users live

16. What is the main purpose of Amazon Route 53?

1. Countering the threat of distributed denial-of-service (DDoS) attacks

2. Managing domain name registration and traffic routing

3. Protecting web applications from web-based threats

4. Using the serverless power of Lambda to customize CloudFront behavior

17. According to the AWS Shared Responsibility Model, which of the following are responsibilities of AWS? (Select TWO.)

1. The security of the cloud

2. Patching underlying virtualization software running in AWS data centers

3. Security of what’s in the cloud

4. Patching OSs running on EC2 instances

18. According to the AWS Shared Responsibility Model, what’s the best way to define the status of the software driving an AWS managed service?

1. Everything associated with an AWS managed service is the responsibility of AWS.

2. Whatever is added by the customer (like application code) is the customer’s responsibility.

3. Whatever the customer can control (application code and/or configuration settings) is the customer’s responsibility.

4. Everything associated with an AWS managed service is the responsibility of the customer.

19. Which of the following is one of the first places you should look when troubleshooting a failing application?

1. AWS Acceptable Use Monitor

2. Service Status Dashboard

3. AWS Billing Dashboard

4. Service Health Dashboard

20. Where will you find information on the limits AWS imposes on the ways you can use your account resources?

1. AWS User Agreement Policy

2. AWS Acceptable Use Policy

3. AWS Acceptable Use Monitor

4. AWS Acceptable Use Dashboard

# Chapter 5  

Securing Your AWS Resources

**THE AWS CERTIFIED CLOUD PRACTITIONER EXAM OBJECTIVES COVERED IN THIS CHAPTER MAY INCLUDE, BUT ARE NOT LIMITED TO, THE FOLLOWING:**

*   **Domain 2: Security**

*   **![images](images/correction.png) 2.2 Define AWS Cloud security and compliance concepts**

*   **![images](images/correction.png) 2.3 Identify AWS access management capabilities**

![images](images/clogo.jpg) 

## Introduction

Everyone in the IT world knows that application and infrastructure security are critically important elements of any deployment. Unfortunately, the constant stream of news about catastrophic data breaches suggests that some of us may not yet realize just *how* important.

No matter what role you play within your organization’s cloud deployment life cycle, ensuring that your assets are properly protected is part of your job. This chapter will help you explore the tools AWS provides to help you with that responsibility.

You’ll learn how to use the *Identity and Access Management* (IAM) service to control which people and processes get past the wall guarding your resources (authentication) and what they’re allowed to do once they’re in (authorization). You’ll learn how IAM does that through the smart use of users, groups, roles, and federated identities.

We’ll discuss applying *encryption* to your cloud data—both while it’s on its way from your local data center and after it’s comfortably settled into its AWS home—and managing the encryption keys that do all that heavy lifting. Finally, we’ll talk about all the work AWS has done ensuring that its infrastructure is compliant with as wide a range of regulatory frameworks as possible.

## AWS Identity and Access Management

We’ll start with IAM, whose management dashboard ([https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)) connects you to all the administration tools you’ll need to manage the basics of account security. As you can see in [Figure 5.1](#c05.xhtml#figure5-1), the Security Status section of that page provides a friendly reminder that there might be some issues requiring your attention.

Those suggestions include protecting your account by locking down the root user (the user identity that was generated when you first created your AWS account) and replacing the *effective* functionality of root by setting up IAM users and groups for your day-to-day administration tasks. The coming sections will explain both why and how these changes are made.

![FIGURE 5.1 The Security Status section of the IAM Dashboard includes important configuration advice that’s especially important for new accounts ](images/c05f001.jpg)
