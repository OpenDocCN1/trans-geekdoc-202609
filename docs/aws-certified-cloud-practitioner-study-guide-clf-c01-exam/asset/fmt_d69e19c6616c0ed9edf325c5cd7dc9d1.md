
Security is concerned with ensuring the confidentiality, integrity, and availability of data. In short, only those people and systems that need access to data should have it, and that data needs to be protected from unauthorized modification. When it comes to securing the data stored on your AWS resources, you should know the following basic principles:

*   Follow the principle of least privilege to create IAM user and resource policies that grant delete or modify access only to those principals that need it.

*   Avoid data loss by using backups and replication. Use Elastic Block Store (EBS) snapshots at any time to create recovery points for EC2 instances. Configure S3 object versioning and replication to make it possible to recover modified or destroyed data.

*   Enforce confidentiality by using encryption to protect data at rest (such as data stored on EBS volumes and in S3 buckets) as well as data in transit as it moves into and out of your AWS infrastructure.

*   Track every activity that occurs on your AWS resources by enabling detailed logging. This can tell you how well your security procedures are working. It can also help you identify security incidents during or after the fact.

![](images/note.jpg) These principles are basic guidelines and not an exhaustive checklist for securing your AWS resources. The AWS Trusted Advisor (which you learned about in Chapter 3, “Getting Support on AWS”) can offer you specific recommendations for securing your AWS resources.

### Cost Optimization

Cost optimization isn’t about getting your costs as close to zero as possible. Rather, you achieve cost optimization when you use the cloud to meet your needs at the lowest possible cost. For instance, if reliability is important to you and you reduce costs in a way that makes your application less reliable, then you’re not practicing cost optimization.

The first step to achieving cost optimization is to analyze where your money is going in the cloud. Use AWS Cost Explorer and the Cost and Usage reports to see how much you’re spending on AWS services and how those expenditures change over time. Use cost allocation tags to break down resource costs by owner, department, or application. For more information on cost allocation tags, refer to Chapter 2, “Understanding Your AWS Account.”

One of the most effective ways to achieve cost optimization is to pay only for the resources you need at any given time. For example, if there are temporary EC2 instances used for testing only a few days out of the month, you can save money by terminating those instances when they’re not needed.

You can also save money by purchasing instance reservations or using spot instances to save over on-demand costs. See Chapter 7, “The Core Compute Services,” for information on reservations and spot instances.

In addition to looking at the cost of a resource, you should also consider the cost of operating it. For example, the hourly cost of running a MySQL database on a relational database service (RDS) instance will be greater than the hourly cost of running the same database on an EC2 instance that you build and manage yourself. But when you factor in the additional labor and time involved in performing database backups, upgrades, and monitoring, you may find that using RDS to handle these tasks for you would be more cost effective.

### Operational Excellence

Operational excellence is fundamentally about automating the processes required to achieve and maintain the other four goals of reliability, performance efficiency, cost optimization, and security. In reality, few organizations automate everything, so operational excellence is more of a journey than a goal. But the idea behind operational excellence is to incrementally improve and automate more activities for the purpose of strengthening the other pillars. Here are some simple examples of how automation can help achieve operational excellence:

**Reliability** Use elastic load balancing health checks to monitor the health of an application running on several EC2 instances. When an instance fails, route users away from the failed instance and create a new one.

**Performance efficiency** Use EC2 Auto Scaling dynamic scaling policies to scale in and out automatically, ensuring you always have as many instances as you need and no more.

**Security** Use CodeBuild to automatically test new application code for security vulnerabilities. When deploying an application, use CloudFormation to automatically deploy fresh, secure infrastructure, rather than following a manual checklist.

**Cost optimization** Automatically shut down or decommission unused resources. For example, implement S3 object life cycle configurations to delete unneeded objects. Or if you have EC2 instances that are used for testing only during business hours, you can automatically shut them down at the end of the workday and restart them the following morning.

Keep in mind that these examples are by no means exhaustive. Many opportunities for automation aren’t obvious until there’s a failure. For instance, if someone deletes an application load balancer that’s operating as the front end of a critical web application, recovering from such an event would entail performing some quick manual work-arounds and re-creating the load balancer. Understanding how failures affect your application can help you avoid such failures in the future and automate recovery when they occur.

## A Highly Available Web Application Using Auto Scaling and Elastic Load Balancing

The first scenario we’ll consider is a highly available web application that you’ll implement using the topology shown in [Figure 12.1](#c12.xhtml#figure12-1).

![FIGURE 12.1 A highly available web application using Auto Scaling and elastic load balancing ](images/c12f001.jpg)

[**FIGURE 12.1**](#c12.xhtml#figureanchor12-1) A highly available web application using Auto Scaling and elastic load balancing 

Don’t worry if this looks intimidating. We’ll start by taking a high-level look at how these components fit together, and then we’ll dig into the configuration specifics. EC2 Auto Scaling will initially provision two EC2 instances running in different Availability Zones inside the default VPC. Every default VPC has a default subnet in each Availability Zone, so there’s no need to create subnets explicitly. An application load balancer will proxy the connections from clients on the internet and distribute those connections to the instances that are running the popular open-source Apache web server.

We’ll implement this scenario in four basic steps:

1.  Create an inbound security group rule in the VPC’s default security group.

2.  Create an application load balancer.

3.  Create a launch template.

4.  Create an Auto Scaling group.

### Creating an Inbound Security Group Rule

Every VPC comes with a default security group. Recall that security groups block traffic that’s not explicitly allowed by a rule, so we’ll start by adding an inbound rule to the VPC’s default security group to allow only inbound HTTP access to the application load balancer and the instances. Complete Exercise 12.1 to create the inbound rule.

### Creating an Application Load Balancer

Next, you need to create an application load balancer that will distribute connections to the instances in the Auto Scaling group that you’ll create in a later exercise. The load balancer will route traffic to healthy instances using a round-robin algorithm that distributes traffic evenly to the instances without regard for how busy those instances are.
