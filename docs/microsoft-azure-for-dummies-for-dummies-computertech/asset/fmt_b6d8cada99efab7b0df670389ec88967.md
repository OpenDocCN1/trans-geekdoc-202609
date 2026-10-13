
# Deploying and configuring virtual networks

# Connecting virtual networks

People at Microsoft told me a couple of years ago that networking was the number-one support request in Azure. This makes sense to me for at least a couple of reasons:

*   Ethernet and TCP/IP internetworking is a complicated subject that’s deep enough to build an entire career on.
*   Software-defined networking in the Azure cloud is vastly different from on-premises hardware networking.
*   The costs and consequences of making a mistake with Azure networking are high.

In this chapter, I lay the groundwork for Azure networking. I talk about the virtual network, which forms the boundary in which you place your virtual machine (VM) and potentially other Azure services.

## Understanding Virtual Network Components

The *virtual network* (VNet) is a strong isolation and communications boundary in Azure. A common beginner’s mistake is placing VMs on separate VNets and expecting communication between them to be possible by default — because, say, the VNets are in the same Azure region and subscription.

Not true! Although VMs within a single VNet can communicate just fine by default (barring firewall deny rules, naturally), no direct communication is possible between VNets without additional administrative intervention.

For now, I’ll start the VNet discussion by explaining the various components of such a network.

### Address space

The *address space* is the top-level private IPv4 (Internet Protocol version 4) address range that you define for your VNet. Microsoft’s best-practice guidance here is to ensure you have no IP address overlap among your VNets or your on-premises networks.

All network communications within a VNet take place only in Azure; thus, your address space must come from the private, nonroutable IPv4 address ranges defined in Request for Comments (RFC) 1918:

*   `10.0.0.0–10.255.255.255` (/8 prefix)
*   `172.16.0.0–172.31.255.255` (/12 prefix)
*   `192.168.0.0–192.168.255.255` (/16 prefix)

![Technical stuff](images/technicalstuff.png) To learn more about the private IP address ranges, read the RFC 1918 source document at [`https://tools.ietf.org/html/rfc1918`](https://tools.ietf.org/html/rfc1918).

### Subnets

Your VNet address space is worthless unless and until you define one or more subnets. What’s cool about subnets is that Azure system routing takes care of directing traffic among the subnets of a single VNet. No router is required.

The most common architectural pattern places each application tier in its own subnet — perhaps one subnet for the web front-end tier, one for the business logic tier, and one for the data tier. This way, you can sculpt your traffic rules more easily because the VMs on each subnet have the same network traffic requirements.

Azure always reserves five IP addresses from each subnet for its own use. Suppose that you create a subnet that uses the address `192.168.10.0/24`. Here’s what happens:

*   `192.168.10.0` is reserved because it’s the subnet’s network ID.
*   `192.168.10.1` through `192.168.10.3` are reserved for Azure’s private use.
*   `192.168.10.4` is the first usable IP address in the subnet and is distributed by Azure’s Dynamic Host Configuration Protocol.
*   `192.168.10.255` is reserved for protocol conformance.

![Warning](images/warning.png) Azure is a metered service, and every service has a predefined capacity limit. In a single subscription in a single region, you can define up to 1,000 VNets and 3,000 subnets per virtual network. Those capacities seem to be absurdly high at first blush. The day will come when you’ll run into one of these service limits, however, and I don’t want you to be surprised. For more details, visit the Azure docs article “Azure subscription and service limits, quotas, and constraints” at [`https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits`](https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits).

## Creating a Virtual Network

[Figure 4-1](#c04.xhtml#c04-fig-0001) shows the environment deployed in this chapter.

![FIGURE 4-1: The Azure virtual network infrastructure used in this chapter.](images/9781119612148-fg0401.png)

[FIGURE 4-1:](#c04.xhtml#rc04-fig-0001) The Azure virtual network infrastructure used in this chapter.

The topology has the following notable features:

*   The VNet is divided into two subnets to reflect common application tiers.
*   Each VNet is protected by a single network security group (NSG).
*   A service endpoint links a storage account to a VNet.
*   VNet peering logically connects VNet1 and VNet2.

### Deploying with the Azure portal

When you’re signed into the Azure portal with your administrative account, follow these steps to deploy your first Azure virtual network:

1.  **Either create a new resource group or add to an existing resource group.**
2.  **Use the global Search bar in the Azure portal to browse to the Virtual Networks blade.**
3.  **Click Add.**
4.  **Fill out the Create Virtual Network Configuration blade, and click Create to submit the deployment.**

    For practice, use the following values:

    *   *Name:* `VNet1`
    *   *Address Space:* `10.2.0.0/16`
    *   *Subscription:* `[your subscription]`
    *   *Resource Group:* `Wiley`
    *   *Location:* Whichever Azure region is closest to you. (These examples use East US 2.)
    *   *Subnet Name:* `web1` (Azure always names the default subnet “default”; you’re changing its name to make it more descriptive.)
    *   *Subnet Address Range:* `10.2.1.0/24`
    *   *DDoS Protection:* Basic
    *   *Service Endpoints:* Disabled
    *   *Firewall:* Disabled

You can see my completed configuration blade in [Figure 4-2](#c04.xhtml#c04-fig-0002).

After Azure deploys the new VNet, you need to revisit its configuration settings to define the second subnet. Follow these steps to accomplish that goal:

1.  **Navigate to the VNet1 Configuration blade.**
2.  **In the VNet’s Settings list, select Subnets; then click the Subnet button.**
3.  **Fill out the form on the Add Subnet blade, and then click Create to complete the configuration.**

    Use the following values:

    *   *Name:* `app1`
    *   *Address Range:* `10.1.2.0/24`
    *   *Network Security Group:* None
    *   *Route Table:* None
    *   *Service Endpoints Services*: 0 selected
    *   *Delegate Subnet to a Service:* None

![FIGURE 4-2: The completed virtual network configuration.](images/9781119612148-fg0402.png)

[FIGURE 4-2:](#c04.xhtml#rc04-fig-0002) The completed virtual network configuration.

Software-defined networking can become abstract and difficult to envision. In the VNet1 Settings list, click Diagram, as shown in [Figure 4-3](#c04.xhtml#c04-fig-0003). Azure creates a vector diagram that depicts your virtual network; clicking an element in the graphic takes you to that resource’s settings.

I find these diagrams invaluable for figuring out how my VNets are laid out. What’s even cooler is that you can

*   As I mentioned earlier, click any of the diagram shapes in the Azure portal to go to their configuration blades.
*   Click Download Topology to download a scalable vector graphics (SVG) format image for use in your architectural documentation.

![Tip](images/tip.png) If you don’t own a Microsoft Visio license, consider getting one. Visio makes creating Azure diagrams simple. I highly recommend that anyone with work that involves Azure invest in Visio so they can make visualizing cloud-based resources easier.

![FIGURE 4-3: Azure generates nifty network diagrams for you.](images/9781119612148-fg0403.png)

[FIGURE 4-3:](#c04.xhtml#rc04-fig-0003) Azure generates nifty network diagrams for you.
