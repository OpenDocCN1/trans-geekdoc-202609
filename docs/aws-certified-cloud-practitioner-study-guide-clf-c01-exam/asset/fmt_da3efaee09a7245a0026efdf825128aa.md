
Be able to evaluate trade-offs between different design decisions. If given two different implementation options for a given scenario, be able to identify some of the advantages and disadvantages of each. For example, you should know some of the trade-offs between using spot pricing for an EC2 instance versus on-demand pricing.

## Review Questions

1.  Which of the following is `not` one of the pillars of the Well-Architected Framework?

    1.  Performance efficiency

    2.  Reliability

    3.  Resiliency

    4.  Security

    5.  Cost optimization

2.  Which of the following are examples of applying the principles of the security pillar of the Well-Architected Framework? (Select TWO.)

    1.  Granting each AWS user their own IAM username and password

    2.  Creating a security group rule to deny access to unused ports

    3.  Deleting an empty S3 bucket

    4.  Enabling S3 versioning

3.  You’re hosting a web application on two EC2 instances in an Auto Scaling group. The performance of the application is consistently acceptable. Which of the following can help maintain or improve performance efficiency? (Select TWO.)

    1.  Monitoring for unauthorized access

    2.  Doubling the number of instances in the Auto Scaling group

    3.  Implementing policies to prevent the accidental termination of EC2 instances in the same Auto Scaling group

    4.  Using CloudFront

4.  Which of the following can help achieve cost optimization? (Select TWO.)

    1.  Deleting unused S3 objects

    2.  Deleting empty S3 buckets

    3.  Deleting unused application load balancers

    4.  Deleting unused VPCs

5.  Which of the following is a key component of operational excellence?

    1.  Adding more security personnel

    2.  Automating manual processes

    3.  Making minor improvements to bad processes

    4.  Making people work longer hours

6.  Your default VPC in the us-west-1 Region has three default subnets. How many Availability Zones are in this Region?

    1.  2

    2.  3

    3.  4

    4.  5

7.  Your organization is building a database-backed web application that will sit behind an application load balancer. You add an inbound security group rule to allow HTTP traffic on TCP port 80. Where should you apply this security group to allow users to access the application?

    1.  The application load balancer listener

    2.  The database instance

    3.  The subnets where the instances reside

    4.  None of these

8.  How does an application load balancer enable reliability?

    1.  By routing traffic away from failed instances

    2.  By replacing failed instances

    3.  By routing traffic to the least busy instances

    4.  By caching frequently accessed content

9.  Which of the following contains the configuration information for instances in an Auto Scaling group?

    1.  Launch directive

    2.  Dynamic scaling policy

    3.  CloudFormation template

    4.  Launch template

10.  You’ve created a target tracking policy for an Auto Scaling group. You want to ensure that the number of instances in the group never exceeds 5. How can you accomplish this?

     1.  Set the group size to 5.

     2.  Set the maximum group size to 5.

     3.  Set the minimum group size to 5.

     4.  Delete the target tracking policy.

11.  Which of the following is an example of a static website?

     1.  A WordPress blog

     2.  A website hosted on S3

     3.  A popular social media website

     4.  A web-based email application

12.  Which of the following features of S3 improve the security of data you store in an S3 bucket? (Select TWO.)

     1.  Objects in S3 are not public by default.

     2.  All objects are readable by all AWS users by default.

     3.  By default, S3 removes ACLs that allow public read access to objects.

     4.  S3 removes public objects by default.

13.  Which of the following is required to enable S3 static website hosting on a bucket?

     1.  Enable bucket hosting in the S3 service console.

     2.  Disable default encryption.

     3.  Disable object versioning.

     4.  Enable object versioning.

     5.  Make all objects in the bucket public.

14.  You’ve created a static website hosted on S3 and given potential customers the URL that consists of words and numbers. They’re complaining that it’s too hard to type in. How can you come up with a friendlier URL?

     1.  Re-create the bucket using only words in the name.

     2.  Use a custom domain name.

     3.  Re-create the bucket in a different Region.

     4.  Re-create the bucket using only numbers in the name.

15.  Which of the following is true regarding static websites hosted in S3?

     1.  The content served is not encrypted in transit.

     2.  Anyone can modify the content.

     3.  You must use a custom domain name.

     4.  A website hosted on S3 is stored in multiple Regions.

16.  Which of the following can impact the reliability of a web application running on EC2 instances?

    1.  Taking EBS snapshots of the instances.

    2.  The user interface is too difficult to use.

    3.  Not replacing a misconfigured resource that the application depends on.

    4.  Provisioning too many instances.

17.  You have a public web application running on EC2 instances. Which of the following factors affecting the performance of your application might be out of your control?

    1.  Storage

    2.  Compute

    3.  Network

    4.  Database

18.  An Auto Scaling group can use an EC2 system health check to determine whether an instance is healthy. What other type of health check can it use?

    1.  S3

    2.  SNS

    3.  VPC

    4.  ELB

19.  You’re hosting a static website on S3. Your web assets are stored under the Standard storage class. Which of the following is true regarding your site?

    1.  Someone may modify the content of your site without authorization.

    2.  You’re responsible for S3 charges.

    3.  You’re charged for any compute power used to host the site.

    4.  An Availability Zone outage may bring down the site.

20.  You’re hosting a static website on S3. Your web assets are stored in the US East 1 Region in the bucket named mygreatwebsite. What is the URL of the website?

    1.  `http://mygreatwebsite.s3-website-us-east-1.amazonaws.com`

    2.  `http://mygreatwebsite.s3.amazonaws.com`

    3.  `http://mygreatwebsite.s3-website-us-east.amazonaws.com`

    4.  `http://mygreatwebsite.s3-us-east-1.amazonaws.com`

# Appendix A  

Answers to Review Questions

## Chapter 1: The Cloud

1.  C. Having globally distributed infrastructure and experienced security engineers makes a provider’s infrastructure more reliable. Metered pricing makes a wider range of workloads possible.

2.  A, D. Security and virtualization are both important characteristics of successful cloud workloads, but neither will directly impact availability.

3.  B, D. Security and scalability are important cloud elements but are not related to metered pricing.

4.  A, B. Security and elasticity are important but are not directly related to server virtualization.

5.  D. A hypervisor is software (not hardware) that administrates virtualized operations.

6.  B. Sharding, aggregating remote resources, and abstracting complex infrastructure can all be accomplished using virtualization techniques, but they aren’t, themselves, virtualization.

7.  A. IaaS products provide full infrastructure access, SaaS products provide end-user services, and serverless architectures (like AWS Lambda) let developers run code on cloud servers.

8.  A. IaaS products provide full infrastructure access, SaaS products provide end-user services, and serverless architectures (like AWS Lambda) let developers run code on cloud servers.
