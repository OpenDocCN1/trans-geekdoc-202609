
considerations and design recommendations of enterprise-scale architecture may require trade-offs depending on the situation of cloud consumer organizations. Organizations can scale their organizations effectively when they follow the core recommendations.

When migrating to Azure, organizations can use landing zones and Microsoft's Cloud Adoption Framework to make informed decisions about governance, strategy, and security. Areas for designing landing zones in the Azure environment include the following considerations:

**Resource organization** Cloud users will organize their resources in order to grow their business, considering the needs of various teams, management groups, subscriptions, and business areas.

**Cloud subscription** A subscription is a way of managing, billing, and scaling Azure services. Designing for Azure adoption on a large scale requires them. Accelerate new application development and migrations by using subscriptions. Business areas and portfolio owners should align subscriptions with their needs and priorities.

**Azure billing offers and Active Directory tenants** Azure billing and Azure Active Directory (Azure AD) are the two highest alignment levels across all cloud Azure deployments within this critical area.

**Multi-tenancy** Multiple cloud tenants should enforce tagging policies and provide different security profiles for other tenants (dev/staging/prod).

**Network connectivity** Cloud consumers can create hybrid systems and multi-cloud adoption models by combining networking patterns with external data centers. Network implementation provides high availability, resilience, and scalability. We should ask the customers questions like the following before designing network connectivity: What will the topology of our network look like? Where will our resources be located?

**Identity and access management** An integrated MFA SSO platform is integrated with all hosted production applications and cloud consoles as the foundation of any fully compliant cloud architecture.

Compliance design areas for Azure landing zones include the following considerations:

**Security and compliance** Cloud users can implement data residency and compliance policies proactively and deductively through landing zones.

**Management** Management of Azure, hybrid, and multi-cloud environments is established here.

**Business continuity and disaster recovery (BCDR)** The smooth functioning of applications depends on resilience, and BCDR is a critical element of strength. By using BCDR, cloud consumers can protect cloud consumers’ data via backups and recover cloud consumers’ applications in the event of an outage.

Governance and operation How do cloud consumers intend to manage, monitor, and optimize their environment? How will cloud consumers ensure that their environment operates as expected?

Platform automation and DevOps Organization can increase productivity, scalability, and reliability by using automation. Part of DevOps is that a continuous integration/deployment (CI/CD) pipeline must be followed to deliver a new software version. By automating the software development life cycle, CI/CD pipelines improve software delivery.

Cloud landing zone automates CI/CD pipelines based on Terraform, ARM, or cloud formation templates to deploy multi-account subscription structures and increase productivity, scalability, and reliability.

Multisubscription Azure environments that account for scale, security governance, networking, and identity result in Azure landing zones. With Azure landing zones, enterprise applications can be migrated, modernized, and innovated at scale. There is no differentiation between infrastructure or platform as a service in these zones because they consider all platform resources needed for the customer’s application portfolio.

Designing and building an Azure environment requires a good understanding of security, governance, and compliance. These topics help you build solid foundations and maintain solid processes and controls over time.

The tools and processes you implement will help detect and respond to issues as you manage environments. Organizations will refine these compliance design areas iteratively as their cloud environments develop. These tools work in conjunction with controls that help maintain and demonstrate compliance. As a result of new applications introducing specific requirements or a new compliance standard, for example, business requirements may have changed.

## Design Security Review

Security should be a core consideration throughout the design and implementation process of an Azure landing zone. Additional guidance is provided on holistic security processes and tools using the Cloud Adoption Framework’s (CAF) Secure methodology. Security design focuses on considerations and recommendations for landing zone decisions. The Secure methodology in Cloud Adoption Framework will help you later enhance this foundation. It creates a solid foundation for security across Azure, hybrid, and multi-cloud environments.

In designing areas, ensure that you establish active roles and functions, what is in scope, and what is out of scope based on the following guidelines:

- Participating roles or functions: In this design area, cloud security, specifically the security architects within that team, is in charge. The cloud platform and cloud center of excellence must review networking and identity decisions. Collective roles may be needed to define and implement the technical requirements derived from this exercise. Cloud governance could also provide support for more advanced security guardrails.

- In scope: This exercise focuses on understanding and implementing the security requirements for your cloud platform, including Zero Trust and advanced network security.

- Out of scope: To streamline the conversation, this exercise must address some CAF Secure disciplines to establish a modern security operations center in the cloud. The discussion of this design area needs to cover security operations, asset protection, and innovation security, which will be based on your Azure landing zone deployment.

## Security Design Considerations

The security monitoring and audit logging of Azure platform services are crucial components of a scalable framework. An organization must see what's happening within its technical cloud estate. When designing security operations, follow these guidelines:

- Security alerts:
  - What teams need to be notified of security alerts?
  - Is there a group of services for which alerts should be routed to different teams?
  - Monitor and alert in real time to meet business requirements.
  - Integrate Microsoft Defender for Cloud and Microsoft Sentinel for security information and event management.

- Security logs:
  - There is a 30-day data retention period for audit data. Azure AD Premium reports have a 30-day data retention period.
  - Logs such as Azure activity logs, VM logs, and PaaS logs can be archived for years.

- Security controls:
  - Azure's in-guest VM policy provides basic security configurations.
  - Be sure to align your security controls with governance guidelines.

- Vulnerability management:
  - In the event of a critical vulnerability, emergency patches are applied.
  - Extensive offline patching is available for virtual machines.
  - Vulnerability assessment is conducted for virtual machines.

- Shared responsibility:
  - Know where the handoffs are for team responsibilities when monitoring or responding to security events.
  - Considering the Secure methodology for security operations is a good idea.

- Encryption and keys:
  - In the environment, who needs access to keys?
  - How will the keys be managed?

## Security in the Azure Landing Zone Accelerator

The Azure landing zone accelerator puts security at the core of its implementation, deploying various tools and controls to help organizations establish a baseline for security quickly.

The following, for example, are included:

- Tools:
  - A free or standard tier of Microsoft Defender for the Cloud
  - Microsoft Sentinel
  - Microsoft Azure DDoS standard protection plan
  - Microsoft Azure Firewall
  - Web Application Firewall
  - Privileged Identity Management

- Landing zone policies for online and corporate connections:
  - Deploy secure access, like HTTPS, to storage accounts.
  - Deploy auditing for Azure SQL Database.
  - Deploy encryption for Azure SQL Database.
  - Block IP forwarding.
  - Block inbound RDP from the Internet.
  - Deploy subnets that are associated with the network security group (NSG).

## Improve Security in the Azure Landing Zone

Data and assets must be protected when a workload or landing zone hosts sensitive data or critical systems.

Once you leave the Ready state, you must continue maintaining your environment's security. As a cloud security process rather than a static destination, it is essential to envision the end state of security based on objectives and key results. Develop roles and responsibilities for the human domain with concepts, frameworks, and standards in the CAF Secure methodology.

## Gain Risk Insights

Using security practices to recognize which risks are appropriate for planning and addressing, the security team should inform and advise decision-makers on how security risks fit into their frameworks.

- Understand cybersecurity risk: Determine any potential damage or destruction by human attackers trying to steal the business's currency, confidential information, or technology.
