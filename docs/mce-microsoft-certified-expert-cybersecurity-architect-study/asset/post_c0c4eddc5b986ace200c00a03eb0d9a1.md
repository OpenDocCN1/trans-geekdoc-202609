
- Support cloud-native patterns in an environment, continuing to use traditional IT operations practices while introducing DevOps practices.
- Configure Kubernetes clusters and extensions with custom locations as an abstraction layer.

## Azure Policy Enables Hybrid Environments to Be Run at Scale

Organizational standards can be enforced and compliance can be assessed at scale with Azure Policy. Through its compliance dashboard, users can see an aggregated view of the environment and drill down to the level of per-resource, per-policy granularity. Additionally, it allows bulk remediation of existing resources and automatic remediation of new ones to bring them into compliance.

The most common use cases for Azure Policy include implementing governance for resource consistency, regulatory compliance, security, and cost control. Azure environments already offer built-in policy definitions for these everyday use cases to assist architects.

The logic used to determine whether a resource is compliant is expressed in JavaScript Object Notation (JSON). A policy rule and metadata are included in the definition. Functions, parameters, logical operators, conditions, and property aliases can be used to define a rule. In an assignment, the policy rule determines what resources are evaluated.

Throughout the resource and policy assignment life cycles and for regular ongoing compliance evaluations, resources are evaluated at specific times. Resources are evaluated at the following times or events:

- A policy assignment creates or updates a resource in a scope.
- Scopes are newly assigned to policies or initiatives.
- The scope of a procedure or initiative is updated.
- Every 24 hours, the standard compliance evaluation cycle takes place.

## Plan Traffic Filtering and Segmentation Technical and Governance Strategies

The perimeter of a network assumes that all systems within it are trustworthy. However, today’s employees can access their organization’s resources from anywhere via various devices and apps, rendering perimeter security controls irrelevant. To master the balance between safety and productivity, security admins need to consider how resources are accessed and who can access them. More than focusing on who has access to resources is required regarding access control policies.

One endpoint within a trusted boundary can be compromised and can quickly spread its reach across the entire system if network security is compromised, as opposed to traditional defenses. The location of the network within the perimeter is not a factor in determining trust in Zero Trust networks. For new initiatives, adopt Zero Trust approaches that validate trust during access using devices and user trust claims. Zero Trust architectures use devices, and user trust claims to access organizational data and resources.

### Logically Segmented Subnets

An organization’s virtual machine, physical server, network, and security devices are isolated from each other through segmentation. This is an effective way of detecting and containing adversary movements. Segmentation can be achieved by isolating networks. Because different technical teams may not be aligned with business use cases and application workloads, this approach is not recommended. It can lead to reduced velocity or, worse cases, to wide network firewall exceptions due to this mismatch, especially regarding on-premises networking. A unified segmentation strategy should incorporate network control as part of a segmentation strategy.

Enterprise security has traditionally relied heavily on network security. As a result of cloud computing, network perimeters are increasingly porous, and attackers can bypass network controls when they attack identity system elements. Because of these factors, focusing primarily on identity-based access controls rather than network-based access controls has become increasingly essential to protect resources.

All technical teams (IT, security, applications) should use segmentation strategies to isolate access through networking, applications, identity, and other controls. For the strategy to be successful, it should do the following:

- Align your operational practices with your business applications to minimize operational friction.
- By adding cost to attackers, you can reduce risk. As a result, you are doing the following:
  - Protecting sensitive workloads from other assets’ compromise
  - Protecting high-exposure systems from being used as pivots
- Monitor operations that might threaten segment integrity (account usage, unexpected traffic).

A virtual network in Azure, for example, is similar to a local area network (LAN) on an on-premises network. All Azure virtual machines can be located on a single IP address. Class A (10.0.0.0/8), Class B (172.16.0.0/12), and Class C (192.168.0.0/16) are the three private IP address spaces that are currently known.

### Deploy Perimeter Networks for Security Zones

A perimeter network, also called a DMZ, serves as an additional layer of security between assets and the Internet. As part of a virtual network, specialized access control devices allow only desired traffic to enter a perimeter network. A perimeter network in Azure helps manage, monitor, log, and report on virtual network edge devices. Perimeter networks are used for the prevention of distributed denial of service (DDoS), intrusion detection and prevention systems (IDS/IPS), firewall rules, web filtering, and network antimalware. A network security device sits between an Azure virtual network and the Internet and has an interface on both networks.

Azure or a third-party solution can provide a perimeter network based on the Zero Trust concept to provide the next level of security between assets and the Internet.

## Avoid Exposure to the Internet with Dedicated WAN Links

The hybrid IT approach has been adopted by many organizations. Hybrid cloud deployment model uses Azure to store some information assets, while on-premises storage is used for others. Many services run some components in Azure and others on-premises. It is common for hybrid IT scenarios to include cross-premises connectivity, and Azure virtual networks can be connected to the organization's on-premises networks

## Use Virtual Network Appliances

A certain degree of network security can be provided by network security groups and user-defined routing at the network and transport layers. But in some situations, security must be enabled at high stack levels. Microsoft recommends deploying virtual network security appliances that Azure partners provide in such cases. Network-level controls cannot provide as much security as Azure network security appliances.

## Summary

This chapter explored several topics related to the basics of cloud networking and presented a brief overview of cloud computing and cybersecurity in cloud.

As your organization moves to Microsoft Azure, you must design and deploy a secured cloud environment. End users must obtain the cloud resources they need seamlessly and safely in a secure manner.

The Microsoft Cybersecurity Reference Architecture (MCRA) overviews Microsoft's cybersecurity capabilities. Throughout this chapter, you have read about how Microsoft security capabilities integrate with Microsoft platforms such as Microsoft 365, Microsoft Azure, and other third-party platforms.

In this chapter, you learned how to adopt Microsoft Cybersecurity Reference Architecture, convert business goals into security requirements, convert security requirements into technical capabilities, define security resiliency strategy, and develop governance strategy for Microsoft Azure.

## Exam Essentials

### Understand cloud computing and cybersecurity.
You should have a conceptual knowledge of cloud computing, Microsoft Azure, security policies, requirements, Zero Trust architecture, and management of hybrid environments. Developing security requirements based on business goals, applying Zero Trust strategies, and applying security policies are essential for the SC-100 exam.

### Develop integration points in an architecture.
The Microsoft Cybersecurity Reference Architecture describes Microsoft's cybersecurity abilities. The reference architectures define how Microsoft's security abilities integrate with Microsoft cloud services such as Azure and Microsoft 365, third-party apps such as ServiceNow and Salesforce, and third-party platforms such as Amazon Web Services (AWS) and Google Cloud Platform (GCP). The reference architectures are comprised of detailed technical, logical building blocks on Microsoft cybersecurity abilities, Zero Trust user access, security operations, operational technology (OT), multi-cloud and cross-platform abilities, attack chain coverage, Azure native security controls, and security organizational functions. A Microsoft Cybersecurity Architect must understand end-to-end MCRA.

### Develop security requirements based on business goals.
Cloud adoption can be time-consuming and costly, and a breach of your cloud solutions will be even more expensive. Successful transformation begins with the business goals. You can overcome this barrier using the Microsoft Cloud Adoption Framework; Microsoft has created a framework for helping customers identify business outcomes that drive observable results or changes in business performance.

### Translate security requirements into technical capabilities.
Several organizational transformations are occurring in many organizations at once. These internal transformations typically begin as nearly all external markets transform to meet customer preferences for mobile and cloud technology. It is common for organizations to be subject to the competitive threat of new startups and the digital transformation of traditional competitors who have the potential to disrupt the market. To overcome these challenges, translate the security requirements into Microsoft Azure capabilities. Understanding of each modernizing capability is essential.

### Design security for a resiliency strategy.
Security resiliency is focused on supporting the resiliency of your business. It has two main goals. Number one is to enable your business to innovate and adapt to the ever-changing business environment rapidly. Number two limits the impact and likelihood of disruptions before, during, and after active attacks on business operations.

### Design security strategy for hybrid and multi-tenant environments.
By deploying hybrid solutions, organizations can take advantage of the features and administrative control they already have on-premises. An organization can use a hybrid deployment to create a seamless
