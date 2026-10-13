
# Implementing Network Security

Implementing network security is about both the big picture and the granular details. Infrastructure design, topology, and redundancy are all important big-picture items. But do not overlook the details that need attention on a node-by-node basis. Node security focuses on the tasks necessary for each type of networking device to improve its security. Node security or node hardening takes the generic recommendations of system hardening and expands those with additional node/host-specific improvements.

## Clients

Clients are the devices directly controlled by people. Thus, clients must protect the network from the user and vice versa. Thinking of clients as two-way interfaces can assist in proper security design and implementation for this essential IT infrastructure component.

Every client needs the following security elements:

*   Antivirus and anti-malware scanners
*   Host firewall
*   Secured Internet client software such as browser, email, file transfer, and chat
*   Password-protected screen saver with auto timeout
*   Ability to encrypt network communications
*   Ability to encrypt storage devices
*   Auditing of all user activity
*   An integrity checking system that monitors for unauthorized file changes using hash value comparison
*   Configuration integrity management that either alerts when configuration changes are made or locks down configurations that do not allow for alteration

Clients should be subject to `NAC` procedures to prevent an insecure client from compromising the rest of the network. Use multifactor authentication whenever possible to minimize the risk of an unauthorized person gaining access to the client and hence the entire network. Allow certain necessary functions—such as secure `FTP`—based on the needs of the client; if there is no legitimate business need for a service, the ability to conduct those actions should be removed.

Another recent shift for some organizations is to allow, even encourage, employees and contractors to **Bring Your Own Device (BYOD)**. The use of an individual’s personal cell phone, tablet, laptop, or similar device lowers the cost to the organization, but it also raises many different security questions, ranging from policy to implementation. For instance, who is responsible for the applications that are run on the device and the security of each? Who owns and is responsible for the content and protection of the files created on the device? What if the specific device is incapable of running specific organization-decreed security software, such as antivirus or even `VPN` software? What if the owner of the device doesn’t want to allow a security scan or to run certain software? `BYOD` exposes an organization to an array of security problems—problems that are growing in importance each day, especially because the population of `BYODs` is increasing and because the devices are wireless.

To address `BYOD` security concerns, first consider if `BYOD` makes sense for your organization. Lowered costs can mean lowered control and access for business purposes. If your organization has legitimate reasons for allowing `BYOD`, ensure that there are specific policies in place that detail acceptable use and the classification of business data as an asset belonging to the organization. Employ remote-wiping tools to remove data from devices if an employee leaves the organization or is found to have accessed or is in possession of data for which they have no legitimate business need. This is also a handy feature in the event the device is lost or stolen. Ask all employees to sign a release and accept this security measure, and ask the organization’s legal counsel to review all corporate policies.

## Servers

Servers are the backbone of any IT infrastructure. Whether a file server, database host, email server, proxy server, or authentication server, a server is usually supporting an essential or mission-critical function for the organization. Servers need protection against downtime. This can include redundancy in terms of `RAID`, duplicate servers, and/or clustering.

Employing duplicate servers means having two identically configured systems running at the same time, but only one is performing services live for the network. The second system is acting as a backup and receives all data changes as those changes occur. In the event of the primary server failure, the secondary server can take over supporting the services for the network. These servers can be located side-by-side in the same facility or in different states connected by a telephone line or the Internet. Some companies rely on a local server and a duplicate server hosted in the cloud to save on operating two physical systems.

Clustering is having two or more identically configured systems running as a collective. All of the systems share in supporting the live service to the network. If any member of the cluster goes offline, the remaining members continue to support the service. Clustering makes it possible for a service to be available consistently while still allowing for scheduled maintenance and occasional individual server downtime. There are additional resources, including auditing costs, when using clustering.

Servers need strong multifactor authentication to ensure that only administrators have the ability to log in from the keyboard. You should sequester servers in a dedicated room or vault to prevent casual or intentional access by unauthorized users. Lock and monitor the server room at all times.

## Routers

Routers are an essential traffic-management device of any network. Network router security is primarily about preventing unauthorized access. First and foremost, a router should be physically inaccessible to any nonadministrator. All router configuration and management interfaces must require strong authentication. Some environments have elected to eliminate local accounts on the routers and rely upon **Terminal Access Controller Access-Control System Plus (TACACS+)** for router authentication and access. Limit management interface access to a direct console or to a terminal cable connection only, rather than allowing in-network access. Require that all management interface communications and router-to-router communications be encrypted.

If a password is stored in a configuration file for the router, be sure to use an encoding scheme that is not easily cracked or reverse engineered. For example, the `Cisco IOS` password 7 hashing method uses a weak reversible algorithm and can be easily cracked, using software tools dating back to 1997. Unfortunately, that easily hacked method is still in use today. Be sure to update any configurations to the latest and most secure option available on the device, or consider changing the router to a newer model with better security.

Generally, configure the following on the router:

*   Block all directed IP broadcasts.
*   Drop all packets from the Internet using an `RFC 1918` source address or any other internal address.
*   Disable the `TCP` and `UDP` small services of echo, chargen, discard, and daytime.
*   Enable a warning banner for all attempted connections to the router, especially to the management interface.

Try to limit the use of a router as a filtering device. Keep the router table focused on traffic routing, and implement firewalls to provide content filtering and blocking of suspicious or malicious traffic. Protect any router considered a border router with a firewall.

## Switches

Switch security is similar to that of router security. Maintain control over who can physically reach the switch. Limit access to management consoles and require strong authentication to access the management interface. If a password is stored in a configuration file for the switch, be sure to use an encoding scheme not easily cracked or reverse engineered.
