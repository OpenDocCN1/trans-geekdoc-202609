
8. B, D. When you register a domain name, you can choose a term between 1 year and 10 years. If you use Route 53, it will automatically create a public hosted zone for the domain. The registrar and DNS hosting provider don’t have to be the same entity, but often are.

9. B. A Multivalue Answer routing policy can return a set of multiple values, sorted randomly. A simple record returns a single value. A Failover routing policy always routes users to the primary resource unless it’s down, in which case it routes users to the secondary resource. A Latency routing policy sends users to the resource in the AWS Region that provides the least latency.

10. C. All Route 53 routing policies except for Simple can use health checks.

11. C. An Endpoint health check works by connecting to the monitored endpoint via HTTP, HTTPS, or TCP. A CloudWatch alarm health check simply reflects the status of a CloudWatch alarm. A Calculated health check derives its status from multiple other health checks. There is no such thing as a Simple health check.

12. A. A Weighted routing policy lets you distribute traffic to endpoints according to a ratio that you define. None of the other routing policies allows this.

13. B. A private hosted zone is associated with a VPC and allows resources in the VPC to resolve private domain names. A public hosted zone is accessible by anyone on the internet. Domain name registration is for public domain names. Health checks aren’t necessary for name resolution to work.

14. A. Route 53 private hosted zones provide DNS resolution for a single domain name within multiple VPCs. Therefore, to support resolution of one domain names for two VPCs, you’d need one private hosted zone.

15. B. CloudFront has edge locations on six continents (Antarctica is a hard place to get to).

16. B. A CloudFront origin is the location that a distribution sources content from. Content is stored in edge locations. A distribution defines the edge locations and origins to use.

17. B. The RTMP distribution type is for delivering streaming content and requires you to provide a media player. A Web distribution can also stream audio or video content but doesn’t require you to provide a media player. Streaming and Edge are not distribution types.

18. A. The more edge locations you use for a distribution, the more you’ll pay. Selecting the minimum number of locations will be the most cost effective.

19. B. There are more than 150 edge locations throughout the world.

20. A, B. An origin can be an EC2 instance or a public S3 bucket. You can’t use a private S3 bucket as an origin.

## Chapter 11: Automating Your AWS Workloads

1. C. CloudFormation can create AWS resources and manages them collectively in a stack. Templates are written in the CloudFormation language, not Python. CloudFormation can’t create resources outside of AWS. It also doesn’t prevent manual changes to resources in a stack.

2. B, D. CloudFormation templates are written in the YAML or JSON format.

3. A. Parameters let you input customizations when creating a CloudFormation stack without having to modify the underlying template. Parameters don’t prevent stack updates or unauthorized changes. A template can be used to create multiple stacks, regardless of whether it uses parameters.

4. A, B. Resources CloudFormation creates are organized into stacks. When you update a stack, CloudFormation analyzes the relationships among resources in the stack and updates dependent resources as necessary. This does not, however, mean that any resource you create using CloudFormation will work as you expect. Provisioning resources using CloudFormation is not necessarily faster than using the AWS CLI.

5. A, C. CodeCommit is a private Git repository that offers versioning and differencing. It does not perform deployments.

6. B. Differencing lets you see the differences between two versions of a file, which can be useful when figuring out what change introduced a bug. Versioning, not differencing, is what allows reverting to an older version of a file. Differencing doesn’t identify duplicate lines of code or tell you when an application was deployed.

7. D. Continuous integration is the practice of running code through a build or test process as soon as it’s checked into a repository. Continuous delivery and continuous deployment include continuous integration but add deployment to the process. Differing only shows the differences between different versions of a file but doesn’t perform any testing.

8. B, D. Build.general1.medium and build.general1.large support Windows and Linux operating systems. Build.general1.small supports Linux only. The other compute types don’t exist.

9. A, B. A CodeBuild build environment always contains an operating system and a Docker image. It may contain the other components but doesn’t have to.

10. A, B, C. CodeDeploy can deploy application files to Linux or Windows EC2 instances and Docker containers to ECS. It can’t deploy an application to smartphones, and it can’t deploy files to an S3 bucket.

11. B. At the very least, a CodePipeline must consist of a source stage and a deploy stage.

12. D. A launch template can be used to launch instances manually and with EC2 Auto Scaling. A launch configuration can’t be used to launch instances manually. An instance role is used to grant permissions to applications running on an instance. Auto Scaling can’t provision instances using a CloudFormation template.

13. A, D. The maximum and minimum group size values limit the number of instances in an Auto Scaling group. The desired capacity (also known as the group size) is the number of instances that Auto Scaling will generally maintain, but Auto Scaling can launch or terminate instances if dynamic scaling calls for it.

14. B. Auto Scaling will use self-healing to replace the failed instance to maintain the desired capacity of 7. Terminating an instance or failing to replace the failed one will result in 6 instances. Auto Scaling won’t ever change the desired capacity in response to a failed instance.

15. A. Predictive scaling creates a scheduled scaling action based on past usage patterns. Scheduled scaling and dynamic scaling do not create scheduled scaling actions. There is no such thing as pattern scaling.

16. B. A Command document can execute commands on an EC2 instance. An Automation document can perform administrative tasks on AWS, such as starting or stopping an instance. There is no such thing as a Script document or a Run document.

17. D. An Automation document can perform administrative tasks on AWS, such as starting or stopping an instance. A Command document can execute commands on an EC2 instance. There is no such thing as a Script document or a Run document.

18. B. AWS OpsWorks Stacks uses Chef recipes, while AWS OpsWorks for Puppet Enterprise uses Puppet modules. There is no service called AWS OpsWorks Layers or AWS OpsWorks for Automation.

19. B, D. OpsWorks supports the Puppet Enterprise and Chef configuration management platforms. It doesn’t support SaltStack, Ansible, or CFEngine.

20. C. Only an OpsWorks layer contains at least one EC2 instance. There’s no such thing as an EC2 Auto Scaling layer.

## Chapter 12: Common Use-Case Scenarios

1. C. The five pillars of the Well-Architected Framework are reliability, performance efficiency, security, cost optimization, and operational excellence. Resiliency is not one of them.

2. A, D. Security is about protecting the confidentiality, integrity, and availability of data. Granting each AWS user their own IAM username and password makes it possible to ensure the confidentiality of data. Enabling S3 versioning protects the integrity of data by maintaining a backup of an object. Deleting an empty S3 bucket doesn’t help with any of these. It’s not possible to create a security group rule that denies access to unused ports since security groups deny any traffic that’s not explicitly allowed.
