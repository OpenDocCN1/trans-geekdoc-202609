Creating standard configurations for VM use in your organization will also help protect them. Variability adds complexity and makes monitoring for unauthorized use more difficult. If the organization uses standard patterns, it is much simpler to identify malicious behavior and to enforce configuration policies.

Configuration guides can provide guidance on the use of cloud services. This will assist workforce members new to the cloud in creating secure solutions. For example, an S3 bucket has many configuration options. Which options are recommended or required and how they should be set can be explained. Cloud tools can then enforce the configuration, prevention, or alerts on changes outside of business guidance.

Other controls exist in the cloud environment to assist with monitoring performance, identifying malicious behavior, and enforcing or identifying variance with policy. Many tools are available to provide these controls—including tools integrated with major CSPs and tools that can be added to a customer's cloud environment.

For example, Amazon provides CloudWatch. This tool can monitor EC2 instances and other data storage systems. CloudWatch can also set alarms, store logs, view graphs, as well as respond to changes in AWS resources. The early alerting provided by this tool can prevent small changes from becoming large problems and may alert you to attacks, misuse of resources, and variations of approved customer configurations.

Azure provides a similar tool in Microsoft Cloud Monitoring (MCM). This tool will monitor Azure applications, analyze log files, and alert customers to potential threats. Like CloudWatch, MCM will monitor utilization, performance, and workloads. In both cases, the software is built into the services each CSP provides. Other CSPs provide similar tools.

Finally, the ability to run multiple VMs from multiple locations must find a balance between security and availability. VM usage can get out of control if not carefully managed. If VM usage is not carefully managed, the attack surface for the organization can actually grow over time.

# Identification, Authentication, and Authorization in Cloud Infrastructure

Many organizations will want to extend their current IAM system into the cloud. They may also choose a SaaS IAM and use it for both their cloud environment and their on-premise environment. They may also maintain their legacy IAM on-premise and use a separate SaaS IAM for cloud services. This is really a business decision. An SSO environment for the workforce is generally desirable but may not be possible to achieve.

Another option is to use the vendor's IAM system for each cloud resource. Using a vendor's IAM system introduces a number of risks. First, the security of the vendor's IAM system is unknown. If you are relying on the vendor to provide access to your business data, you should have confidence in their IAM system. For some cloud services, this