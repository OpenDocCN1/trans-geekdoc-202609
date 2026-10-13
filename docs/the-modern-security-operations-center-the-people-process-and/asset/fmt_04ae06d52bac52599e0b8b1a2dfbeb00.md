
The model shown in [Figure 9-1](#ch09.xhtml#ch09fig01) begins with identifying all assets within scope of being evaluated by the vulnerability management service. In other words, what is on the network? If you don’t know what’s on your network, you can’t properly assess everything that could be vulnerable. There is a whole segment of software products devoted to addressing the challenges of asset inventory for large organizations. Some of these offerings work well, while others have great marketing strategies but fail when it comes to finding assets on the network.

> **Note**
>
> One customer I was consulting was able to greatly reduce the licensing costs of several software packages after completing an asset inventory and discovery project, which identified that the organization had overestimated the number of active computer workstations in its environment. This is just one example of the many benefits obtained by running a strong asset inventory program.

Good asset inventory means you are profiling not only endpoints but also every single network connection (wired and wireless), because many devices, such as IoT devices, do not log into centralized management or authentication servers.

### Option 1: Automated Network Access Control

There are different ways you can enforce proper asset inventory practices. The industry standard for knowing who and what is on the network is to leverage network access control (NAC) based on popular guidelines such as NIST SP 800-53, *Security and Privacy Controls for Information Systems and Organizations*. By automating access control across your LAN, wireless, and VPN, you can have confidence that when a device connects to the network, you know about it. [Chapter 2](#ch02.xhtml#ch02), “[Developing a Security Operations Center](#ch02.xhtml#ch02),” covered how NAC can be related to asset management; this chapter delves further into automated NAC concepts in the section, “[Network Scanners and Network Access Control](#ch09.xhtml#ch09lev2sec15).”

The biggest challenge I find in NAC solutions when speaking with customers is what is missed when NAC is not enforced across all network ports; for example, using NAC only for the wireless network or not enabling every port to be monitored by a NAC solution. Any port that is not enabled for NAC will not be able to track assets, causing potential blind spots to your list of assets that need to be validated for vulnerabilities. This issue can cause a false sense of security awareness regarding what is connected to the network, which leads to problems with the vulnerability management program.

### Option 2: Manual Network Access Control

An alternative to using the automated benefits of NAC is to enforce security on a port-by-port basis, such as by using sticky MAC, and manually collect asset information from the network switch database. Sticky MAC allows a switch to collect the MAC address of a trusted system and dedicate a port to that system. If another system attempts to connect to that port, the port will shut down.

One major flaw in this approach is how validation is done by the port checking for the MAC address. If an attacker were able to spoof the MAC address of a trusted system, the attacker could bypass port security, tricking the switch into believing that a system on the whitelist has connected. Also, port security has the same “omission” flaw in its approach as NAC. Ports that are not enabled with port security will allow devices to connect and not be tracked, again creating blind spots in your asset collection strategy.

### Option 3: Network Scanners

Using network scanners is another option to collect information about devices on the network. A scanner can identify what is already on the network and develop an asset list. Challenges to this approach include how often the tool runs, if the tool has access across the entire network, and how the tool scans.

Combining network scanners with either a manual or automated NAC option is a recommended practice. This approach allows for a nice blend of collecting devices upon connection and validating that all devices have been accounted for using a periodic network scan. One of the most popular open-source tools used to identify what is on the network is Nmap ([https://nmap.org/](https://nmap.org/)). [Figure 9-2](#ch09.xhtml#ch09fig02) shows an example of Nmap scanning a network segment for assets.

![FIGURE 9-2 Nmap Scanning the Network for Assets](Images/09fig02.jpg)

**FIGURE 9-2** Nmap Scanning the Network for Assets

Nmap and other network mapping tools can be helpful; however, most modern vulnerability scanners include the capability to scan for new devices. It is common to find that NAC, NAC profiling, and network scanners are normally part of an overall strategy composed of multiple technologies and solutions for asset inventory. The larger and more geographically dispersed the network, the more complicated it will be for a complete and accurate asset inventory. Best practice dictates leveraging a NAC technology as well as network scanner and integrating what is collected into a vulnerability management technology. The section “[Network Scanners and Network Access Control](#ch09.xhtml#ch09lev2sec15),” later in the chapter, covers this concept in more detail.

## Phase 2: Information Management

The next phase of the vulnerability management model is information management. Information management consists of collecting information about all devices on the asset list that you have created from port scans and access control data. Information such as what applications are installed and running on a system, level of patches deployed, and other factors all allow the SOC to identify potential vulnerabilities in a system. A server might not be vulnerable, but an application installed could be unsecure and vulnerable to an attacker who could use the application to gain access to the patched server. I often see this with vulnerable Internet browser plugins that allow a server that is patched and running the latest Internet browsing software to be exploited.

Looking back at NAC concepts, most modern NAC solutions offer the capability to gather information about systems accessing the network. Some examples of this feature are the Cisco ISE Profiling capability, Fortinet’s FortiNAC Profiling feature, and Forescout’s eyeSight feature. For most NAC vendors, including Cisco, Fortinet, and Forescout, various protocols such as DHCP, DNS, ARP, and Linkup traps are used to fingerprint a device as it connects and uses the network. Most modern NAC solutions can also use agents or Java to scan deeper behind the host’s firewall, allowing full visibility of the system. Vulnerability scanners also have the capability of looking at ports and protocols to fingerprint devices. Many NAC systems incorporate their own scanners or provide integration with a major industry-recognized scanner. One popular example is, once again, using Nmap, but this time launching the `nmap -A target` command. This command will fingerprint a target as shown in [Figure 9-3](#ch09.xhtml#ch09fig03).

![FIGURE 9-3 Nmap Fingerprinting a Targeted System](Images/09fig03.jpg)

**FIGURE 9-3** Nmap Fingerprinting a Targeted System

Part of the information management phase is preparing for the next phase of the vulnerability management program, which is risk assessment, in which you identify potential risk. It is critical to understand both the details of an asset and how the data was collected. The most powerful inventory tracking includes operating system information down to the patch level that is installed, applications (including installed extensions), installed libraries, configured data within the operating system, and services running on the asset. Missing these details will lead to less accurate risk assessment results.
