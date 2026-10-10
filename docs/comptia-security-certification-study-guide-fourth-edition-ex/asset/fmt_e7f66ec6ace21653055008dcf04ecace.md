
# SDN

**SDN** Software-defined networking is a feature that can be configured within your virtualization environment that allows you to create virtual networks and segment network traffic.

## Business Connectivity Considerations

When looking at enterprise security for your organization, you also want to take into account geographical considerations of your business locations, as the location of your offices can affect the types of natural disasters you can expect and response time of emergency personnel.

You should also consider incident response procedures and the types of recovery controls that your business will rely on in case of a security incident. You will learn more about disaster recovery and business connectivity in [Chapter 18](#ch18.xhtml#ch18), whereas [Chapter 21](#ch21.xhtml#ch21) discusses incident response.

## Placement of Security Devices and Network Appliances

When you’re designing the network, it is important to place the different security devices and network appliances at the right locations. The following list identifies key security devices and network appliances as well as where they should be placed:

- **Sensors** Sensors should be placed on each network segment so that they can capture network traffic for that network segment and send it to a collector or analysis engine.
- **Collectors** You can place a single collector on any network segment and have each of the sensors send captured traffic to that collector.
- **Correlation engines** The correlation engine should be running on a system that has access to the data on the collector, and it should be placed on a secure network segment.
- **Filters** These components filter different types of traffic and should be placed on the edge of the network. For example, you can use URL filters on your proxy server to block specific sites from users. The proxy server is placed between the Internet connection and your users so that it can review each web site being visited and filter out web sites that have been disallowed.
- **Proxy servers** A forward proxy is a device that is placed on the edge of the network between your Internet connection and the users. All requests from the users to Internet resources are passed through the proxy so that it can filter out any unauthorized content. A reverse proxy is placed in the DMZ and is used to publish servers within the network (such as a web server) out to the Internet. When a system on the Internet tries to access your server, it first contacts the reverse proxy (which has the DNS name assigned to it), and then the reverse proxy sends the traffic to the internal system.
- **Jump servers** A jump server is a system that is used to access or manage devices in another security zone. The jump server is hardened and configured for secure communication protocols such as SSH, and it’s placed in the zone that contains devices that need to be accessed. The firewalls have strict rules on what protocols and systems can be used to communicate with the jump server.
- **Firewalls** Firewalls should be placed at the edge of the network to protect the network from unauthorized traffic coming in from the Internet. You can also place a firewall between different network segments to control traffic between segments.
- **VPN aggregators** The VPN aggregator is placed at the edge of the network as well, but behind the firewall so that the firewall can block malicious traffic that may be headed toward the VPN aggregator. The firewall will need to open ports to allow VPN traffic to reach the VPN aggregator.
- **SSL accelerators** SSL accelerators can be placed inside any system or server that performs a large number of cryptographic functions.
- **Load balancers** Load balancers are typically placed in the DMZ and are generally used to load-balance requests to web applications. You can also place load balancers inside the network for network services that may require multiple servers to split the load.
- **DDoS mitigator** The DDoS mitigator is placed between the Internet and your public Internet resources, such as web sites and e-mail servers, so that it can protect those resources from DDoS attacks.
- **Taps and port mirror** You can place a network tap device on each network segment so that it sends a copy of all data to your monitoring system. The monitoring system is connected to the port mirror and runs software to monitor network traffic.

## Configuration Management

Part of creating a secure network infrastructure is ensuring that your company has a configuration management policy in place that dictates the change management process that needs to be followed in order for changes to be implemented on the network. This includes deploying the change in a test environment before making the change in production.

Change management also involves having up-to-date network `diagrams` of the network environment and ensuring that there is a `baseline configuration` that can be applied to new devices. The baseline configuration is a tool that is used to ensure consistent configuration across all devices, thus preventing configuration errors from occurring. You should also ensure standardized naming conventions are used for systems and devices on the network to aid in the understanding of what the names of devices are. You should also document the Internet Protocol (IP) address scheme that is used on the network, especially if you are using multiple network segments with different IP blocks on each segment.

## CERTIFICATION OBJECTIVE 8.04

## Securing Devices

The last topic in this chapter reviews some common practices for securing network devices. Over the last few chapters, you have read that common steps should be taken to secure systems and devices. Let’s review some of these points as they relate to network devices:

- **Privilege escalation** Be sure to keep up to date on how someone connecting to a system or device can raise their privileges on the system and gain administrative access to it. This typically happens due to a vulnerability in the product, so be sure to apply updates to the system or device. Applying updates to a device involves upgrading the firmware on the device as revisions to the firmware come out.
- **Weak passwords** I cannot believe how many administrators are still using weak, obvious passwords. During an assessment on a company’s Cisco router, I viewed the running configuration and noticed that the company administrator configured Telnet access to the router with a password of `telnet`. I also gained administrative access to the router by typing a password of `cisco`. Not only are these not strong passwords, they are also common passwords that a hacker would attempt to use to gain access. Another security issue in this example is that I should not have been able to view the passwords because they should have been encrypted in the configuration. With Cisco devices, you can use the `service password-encryption` command to encrypt passwords in the configuration files.
- **Back doors** Review network devices for potential back doors. A good example that I find is that network administrators configure passwords on the console port of a router but do not set a password on the auxiliary port of a router (if one is present). The auxiliary port is like another console port, and someone who has physical access to the router can connect to it to administer the device. Be sure to password-protect all ports on these devices!
- **Default accounts** Watch out for default accounts that exist on a system or device, and be sure to guard those accounts with strong passwords. If at all possible, you should rename the default accounts to something that’s not so obvious.
