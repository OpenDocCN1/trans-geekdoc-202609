# Virtual Private Cloud

You can think of Google Cloud VPC as a virtual network, which is very similar to a physical environment but more powerful due to its software-defined nature. At a high level, VPC is responsible for providing underlying connectivity to your Google Cloud services, such as Compute Engine (virtual machines), Google Kubernetes Engine (GKE), Google App Engine (GAE), and any other Google Cloud services are built on top of these services. VPC natively provides load balancing and proxy services, which help distribute traffic to backend services, and provides the capability to connect your Google Cloud to either your on-premises data center or other cloud service providers.

Let's understand some of the key features that VPC offers, as it will help you understand what capabilities are offered and how to use them in your network design:

+   A VPC is a global resource, including its components, such as the routes and the firewall rules. We will look at global/regional/zonal resources in the Google Cloud regions and zones section.

+   With VPC, you have the ability to enable IPv4-based subnets. These subnets are regional. IPv6 is also supported, where you can enable IPv6 on supported subnets; the only exception is that auto-mode VPC cannot have IPv6, but if you add a custom subnet to the auto mode VPC, you can enable IPv6 on that subnet. The important thing to note here is auto mode VPC networks do not support dual-stack subnets.

+   Firewall rules are used to control the traffic from the instances. When you create firewall rules for the network, they control the traffic, these rules are in fact applied the VM interface. This then lets you control which VMs communicate with each other on which ports. We will cover firewall rules in more detail in the Micro-segmentation section of this chapter.

+   When you create a VPC network, all the resources inside the network with IPv4 addressing communicate with each other without the need for any additional rules. Some restrictions may apply if you create firewall rules to control the traffic inside the VPC network.

+   VM instances are created inside the VPC network and have a private IPv4 address communicate with Google APIs and services. Google Cloud has private access, which we will cover later in this chapter, that instances communicate with Google APIs and services even if they don't have an external IP address.

+   Fine-grained identity and access management policies are available for network administration. You can create custom rules to give the relevant privileges to your network team to manage VPC and its associated components.

+   Shared VPC is a deployment model that can be used to centralize network functions in a common host project. Other services' projects can consume network services from the shared VPC host project, such as IP address, subnet, and hybrid connectivity, as long as they are part of the same organization.