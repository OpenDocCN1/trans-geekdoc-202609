appliances, generally cannot run agents. Also, agents may not be available for all of the organization's platforms.

# 40.4.1.2 Agentless Scanning.

An agentless scanning patch management technology has one or more servers that perform network scanning of each host to be patched and determine what patches each host needs. Generally, agentless scanning requires the servers to have administrative privileges on each host, so that they can return more accurate scanning results and they have the ability to install patches and implement state changes on the hosts (application restarts, OS reboots, etc.).

The main advantage of agentless scanning is that it doesn't require the installation and execution of an agent on each host.

One of the primary limitations of agentless scanning is that it omits hosts not on the local network, such as telecommuter laptops and mobile devices. Also, network security controls (e.g., host-based firewalls) and network technologies (e.g., network address translation) may inadvertently block scanning or otherwise negatively affect scanning results. Agentless scanning may also negatively impact operations by consuming excessive amounts of bandwidth. Finally, agentless scanning may not support all of the organization's platforms.

# 40.4.1.3 Passive Network Monitoring.

Passive network monitoring technologies for patch management monitor local network traffic to identify applications (and in some cases, operating systems) that are in need of patching.

These technologies can be effective at identifying hosts that are not being maintained by other patch management solutions (agent-based, agentless scanning). They do not require any privileges on the hosts to be monitored, so they can be used to monitor the patch status of hosts that the organization does not control (unmanaged systems, visitor systems, contractor systems, etc.).

The primary disadvantage of passive network monitoring is that it only works with software where you can identify the version based on its network traffic (assumed to be unencrypted). Also, of course, it only works with hosts on the local network.

# 40.4.2 Security Capabilities.

This section describes common security capabilities provided by patch management technologies, divided into three categories: inventory management, patch management, and other.

# 40.4.2.1 Inventory Management Capabilities.

Patch management technologies typically have capabilities for identifying which software and versions of software are installed on each host, or alternately, just identifying vulnerable versions of software that are installed. In addition, some products have features for installing new versions of software, installing or uninstalling software features, and uninstalling software.

# 40.4.2.2 Patch Management Capabilities.

Patch management technologies obviously provide a range of patch management capabilities. Common features include identifying which patches are needed, bundling and sequencing patches for distribution, allowing administrators to select which patches may or may not be deployed, and installing patches and verifying installation. Many patch management technologies also allow patches to be stored centrally (within the organization) or downloaded as needed from external sources.