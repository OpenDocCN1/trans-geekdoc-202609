
When considering internal user access to network resources, one should scrutinize all user accounts, because hackers can gain access to and remain resident on networks for years. Just because the activity is internal to the network does not mean it is any more secure or legitimate than activities initiated outside the network. Network security is an essential component of network design and management. One must understand the design and flow—both physical and logical—of a network to recognize if an event is a possible malware attack, or if the network has reached its capacity for data throughput, as both instances can result in similar behavior of the network.

## Intrusion Detection Systems and Intrusion Prevention Systems

Two security technologies available to secure networks are intrusion detection systems (IDSs) and intrusion prevention systems (IPSs). An IDS detects unauthorized user activities, attacks, and network compromises (**FIGURE 4-3**). IDSs come in two types: host-based and network-based.

![FIGURE 4-3 IDS detects an attack and alerts operators—manual intervention needed.](Images/9781284183658_CH04_FIGF03.png)

**FIGURE 4-3** IDS detects an attack and alerts operators—manual intervention needed.

### NOTE

IDS/IPS is used largely on Internet connections, because those connections typically present the largest threat to the network. You can also deploy IDS/IPS in strategic locations on the internal network. This is an excellent idea if your internal network has connections to third-party networks such as customers, vendors, or business partners.

An intrusion prevention system (IPS) is very similar to an IDS, except that in addition to detecting and alerting, an IPS can also take action to prevent a breach from occurring (**FIGURE 4-4**).

![FIGURE 4-4 IPS detects attack, alerts operators, and then modifies firewall and router configuration to address the attack.](Images/9781284183658_CH04_FIGF04.png)

**FIGURE 4-4** IPS detects attack, alerts operators, and then modifies firewall and router configuration to address the attack.

Two common deployment methods are used when placing an IDS/IPS for protecting a network from the Internet. Each has advantages and disadvantages.

An unfiltered IDS/IPS installation examines the raw Internet data stream before it crosses the firewall (**FIGURE 4-5**). This provides the highest amount of visibility to attacks, but it also means that a significantly higher volume of data will be monitored, with a higher possibility of false positives. During periods of high traffic, the IDS/IPS might not be able to process all the packets, and attacks can be missed. This placement often causes a bottleneck within the network, and users may notice the delay and complain about network performance.

![FIGURE 4-5 Placement of the intrusion detection system to get unfiltered traffic for analysis.](Images/9781284183658_CH04_FIGF05.png)

**FIGURE 4-5** Placement of the intrusion detection system to get unfiltered traffic for analysis.

A screened IDS/IPS solution monitors traffic that gets through the screening firewall (**FIGURE 4-6**). The advantage to this model is it dramatically reduces the amount of traffic monitored, reducing the chances of false positives and lost packets during high traffic volumes. A loss of visibility accompanies this model, as you cannot see attacks blocked by the screening firewall. Often you can learn where attacks are coming from by the packets dropped at the firewall. This placement does lessen the bottleneck possibilities on the network, as a smaller number of packets is assessed.

![FIGURE 4-6 An intrusion detection system deployed behind a screening firewall.](Images/9781284183658_CH04_FIGF06.png)

**FIGURE 4-6** An intrusion detection system deployed behind a screening firewall.

## Hardening Systems

Hardening systems focuses on improving security of hosts and nodes. Hardening is the process of reducing the [attack surface](#30_glossary.xhtml#gloss31) of a potential target by removing unnecessary components and adding in protections. Although each organization usually creates its own custom and internal hardening processes and procedures, most hardening guidelines have common elements and components.

When considering your network and systems, think of an attack surface as the candy coating on a popular button-shaped chocolate. The colorful outer shell is not supposed to melt easily and therefore protects the heat-sensitive inner contents (the chocolate). If the outer candy coating is misapplied, forms cracks due to pressure or dropping, or is exposed to air and heat through a manufacturing defect, the chocolate will begin to melt and leak out. To protect the inner contents, the outer shell must be free from defects and continuous with no gaps. The same is true for your network. Any weakness in the network exposes the entire network.

Some of the common recommendations to improve security or harden a host include:

*   Remove all unnecessary protocols.
*   Uninstall all unnecessary applications and services.
*   Define a complex password for all accounts; do not leave any account with a default password or a blank password.
*   Configure account lockout and define a logon warning banner.
*   Install all available final release updates, patches, fixes, service packs, and so on for the operating system and every remaining application and service.
*   Update all hardware device firmware or BIOS with the latest final release from the vendor.
*   Install the latest final releases of all device drivers.
*   Install and update antivirus and anti-malware scanners.
*   Configure communication encryption.
*   Install and configure a host firewall.
*   Use a file system that supports file level permissions and [auditing](#30_glossary.xhtml#gloss33), and set those permissions.
*   Configure system monitoring and auditing.
*   Synchronize the clock of all devices and systems across the network for ease in auditing.
*   Run vulnerability assessment tools against the host, such as `OpenVAS` and `Nessus`.
*   Configure regular backups, and test those backups to ensure that each works and data can be retrieved.
*   Impose any organization-specific security limitations, such as blocking USB drives or using whitelist execution management. This is often performed using a security template file.
*   In Windows, disable the guest account, and rename the Administrator account. In Unix, establish policies whereby the root account is never used directly, but administrators must use the `su` command to obtain root access (thus creating a log of their events).

In addition to these hardening suggestions, organizations should add additional steps to their securing procedures based on the purpose of the system, the criticality of the system, and the risk present in the environment.

Once you’ve hardened your system, you must maintain it over time. On a regular schedule, at least annually, reexamine every host against your organization’s hardening policies to ensure compliance. Remove from service any system out of compliance with hardening policies until you are able to bring it into compliance. Then, investigate the cause of the security noncompliance and take countermeasures to prevent a reoccurrence.

## Equipment Selection

Equipment selection is a commonly overlooked aspect of secure network design. The general belief that any hardware capable of performing an IT function is suitable for deployment is, unfortunately, not the case. Regardless of cost, all products may have well-known or not-yet-discovered security flaws.
