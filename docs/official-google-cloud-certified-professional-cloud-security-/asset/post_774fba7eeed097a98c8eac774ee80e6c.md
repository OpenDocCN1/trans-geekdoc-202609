
-   Only direct peering is supported; you cannot translate transit peers.
-   Tags and service accounts cannot be used across the peering networks.
-   Internal DNS names for compute engines are not accessible across the peering networks.
-   Firewall rules are not exchanged across the peering networks, and you need to create rules to allow ingress firewall traffic from compute instances. The default behavior is to block the ingress traffic to VMs by applying an ingress deny firewall rule.
- Furthermore, you need to create firewall rules to restrict the access of your VMs to the services they shouldn't be able to access.
-   If you are using an internal load balancer and need to restrict access, then you need to create ingress firewall rules that apply to the load balancer's backend VMs.
-   Peering is permitted when establishing a peer with a Shared VPC network.

Next, we will look at how to configure a VPC peer:

1. Navigate to the VPC Network peering and click **Create connection**. Then, click **Continue**.
Look at Figure 7.14 for the fields that you need to complete in order to create a VPC network peer.

2. First, we will fill in **Name**; we will use the name *peer-from-starship*.

3. Next, we will select the network that is available under **Your VPC network**. Select a network you want to peer; in our example, we have selected starshipnw.

4. Now specify the network you want to peer with. This can be a network in your existing project, or it can be a network in a different project. If it is in another project, when you select that option, you must specify the project ID and the network name in that project. For our example and simplicity, we will select an existing project and then select the *default* network.

# Virtual Private Cloud

5. You also have the option to import or export custom routes. To do that, you can choose one of both the following options. In our example, we will not import/export custom routes:

   I. Use Import custom routes to import custom routes exported by the other network.

   II. Use Export custom routes to export custom routes to the other network. The other network must import the routes to see them.

![](img/f681dfc12450e3a4c257352b70dbdbca_180_0.png)

Figure 7.14 – Create peering connection

6. If your network or the partner network uses privately used public IP ranges, these routes are exported by default not imported. Choose Import subnet routes with public IP to import privately used public subnet routes exported by the other network.

7. Click Create.

The peer configuration is only complete once you configure the peering on both sides. You can modify the peer orders or delete them as needed. The list of all VPC peers is found under the VPC Peering page on the Google Cloud console. Access to on-premises connection can be done using Cloud VPN. We will look at Cloud VPN in the Hybrid connectivity options section in the chapter.

| Shared VPC | VPC Peering | Cloud VPN |
|---|---|---|---|
| Network services management | Central management of shared network resources | Clear network and security administrative boundaries | Clear network and security administrative boundaries |
| Transitivity | N/A | Non-transitive | Transitive |
| Scale | 1000 service projects or more, depending on multiple factors | Up to 25 peered networks | Approximately 1000 connected projects |
| Pricing | General network network pricing | General network pricing | General network pricing, excluding intra-zone traffic, which is billed as interzone |
| Performance implication | None | None | Throughput limited based on number of tunnels (1.5 to 3 Gbps per tunnel) |

Figure 7.15 – Cross-project communication options comparison

Figure 7.15 gives a quick snapshot of the default options available for cross-project communication across different dimensions, such as management, scale, pricing, and performance. You can use this to understand what options are available and, more importantly, which options align with your network architecture requirements.

We will now look how micro-segmentation allows you to logically partition your network to have better control of traffic and security.

# Micro-segmentation

In this section, we will look at some micro-segmentation techniques. We will cover topics such as how to create subnets, define custom routing, and firewall rules that can help in creating segmentation in your network.

# Subnets

Creating subnets is a key strategy. In this section, we will look at types of subnets and how to create them. Regardless of what type you create, using either auto mode or custom mode. Let us look at Figure 16:

| Configuration | Primary | Secondary |
|---|---|---|
| Used for | Mandatory | Optional |
| Extendable | Yes | No |

![](img/f681dfc12450e3a4c257352b70dbceca_182_0.png)

The primary range is mandatory; secondary range is optional. In this section, we will look at types of subnets and how to create them.

# Custom routing

You can also use custom routing to restrict access. Custom routing is a combination of both static and dynamic. In this section, we will look at types of routes and how to apply them to network. Let us look at Figure 7.15:

| Route | Type | Created by | Next Hop | Restrictions |
|---|---|---|---|---|
| Subnet route | System | System | VPC peering | Automatic |
| Static route | Custom | User | Cloud VPN | Flag controlled |
| Dynamic route | Custom | Cloud router (BGP) | BGP peer | Flag controlled |

Figure 7.15 – Custom routes

Google Cloud supports three route types: system-generated routes, static routes, and dynamic routes. System-generated routes are created by the system and cannot be deleted. These include routes added to subnets via VPC peering.

Static routes are added by the user manually and are called custom routes. Using static routes, you can define a next hop, such as a load balancer or Cloud VPN.

Dynamic routes are also classified as custom routes and are dynamically updated, such as creating a Border Gateway Protocol (BGP) peer. The next hop is always a BGP peer.

# Firewall rules

Firewall rules are one of the most important parts of network security. In this section, we will look at how firewall rules work, the evaluation criteria, the different types of firewall rules you can create (ingress/egress), 5-tuple rules, and tag-service-account based firewall rules.

| Target | Ingress rule | Source |
|---|---|---|
| Network | ✓ Service account | Allow/Deny IP range/CIDR instances by tag or service account |
| VM | Ingress rule ✓ Target tag | |
| | Ingress rule ✓ All instances in network |
| | Egress rule ✓ Service account | Allow/Deny IP range/CIDR |
| | Egress rule ✓ Target tag | |
| | Egress rule ✓ All instances in network | |

Figure 7.18 – VPC firewall rules

Let us look at some of the firewall rule features shown in Figure 7.18:

- Firewall rules are stately in nature and are applied to a network inside a project. This means, for example, if you create an ingress deny on port 22, you don't need to configure an egress deny rule.
- Enforcement is done on the host level, which means there is a negligible performance penalty.
- The control paths that you can manage using firewall rules are VM to VM, VM to the internet, and VM to on-premises.
- For every VPC, two implied rules for ingress/egress are created, which cannot be deleted: a rule to block all incoming connections and another rule to allow all outgoing connections.
