
Once you properly plan your vulnerability management infrastructure and scanning strategy, it is time to start evaluating assets for vulnerabilities. Best practice is to automate the scanning process using a vulnerability management tool or orchestration tool that can manage the scanning schedule as well as which type of scanning templates are being used. You learned earlier how different scanning templates can be used and tuned to business requirements. An example is using a less aggressive scanning template during business hours and using a more aggressive template when the network is not heavily utilized. Using a centralized system allows estimation for completion because all tasks can be accounted for along with any interruptions.

When launching vulnerability scanning, you want to schedule scanning against the most critical systems or systems that have a high exposure rate first and work your way down the priority list. Using your vulnerability management tool, you can build an automated scanning schedule based on multiple tasks that make up your current network-wide evaluation.

The following are factors that would increase the priority for scanning as you develop the order of what is scanned:

*   The criticality of the asset to the organization in terms of confidentiality, integrity, and availability.
*   Whether the asset is in scope for a required standard such as `PCI DSS`.
*   The number of other systems that are dependent upon that system, such as `Active Directory`, which is used to manage multiple other systems.
*   Whether if by exploiting the asset, other high value assets become visible and put at risk for attack.
*   Whether certain compensating controls like encryption are in place and need to be accounted for.
*   Whether there is a need to log in to the system and, if so, whether you are authorized to do so.
*   How difficult is it to deal with potential disruptions that are associated with scanning the targeted system(s) or network(s). For example, scanning a gateway router could pose the risk of taking it out, leading to a network outage.

## Scanning Best Practice

When scanning, you should first target automation of scanning tasks that disrupt as few people as possible. This means scanning systems that are less likely to be impacted by being scanned, systems that don't require special permissions from the asset owners, and systems that are easy to access. [Figure 9-25](#ch09.xhtml#ch09fig25) shows an example of Rapid7's Nexpose vulnerability scanner Automated Actions configuration screen. For this example, I can choose the scanner to act when a new asset is identified. A common action would be to launch a specific scanning template, such as a less aggressive one during business hours when scanning a network subnet containing user desktops. Also notice there is a calendar allowing scheduling of actions to occur only during specific times. One possible configuration for scanning during business hours is to scan only new assets that haven't been previously identified and scanned. Automated scanning actions allow for the accommodation of these types of scenarios.

![FIGURE 9-25 Rapid7 Nexpose Automated Actions Configuration Example](Images/09fig25.jpg)

**FIGURE 9-25** Rapid7 Nexpose Automated Actions Configuration Example

Another scanning best practice is to group scans together based on required logins, if user login is needed. Network scanning that does not require host scanning should be separated from host scanning that requires a login process using a read-only account. If different read-only accounts are needed, it is recommended to separate those scans to simplify troubleshooting situations in which a login fails. You should also include asset owner contact information with asset lists and pull such information within any ticket created when a scan fails to access the system. This will allow the `SOC` to track down the asset owner and troubleshoot why the scanner was unable to log into the asset. The most common reasons are either the asset wasn't available or the password is incorrect.

Scanning will likely identify systems that are not part of your asset list. Most enterprise vulnerability scanners include the ability to identify and discover services on new systems based on scanning a network subnet for anything connected. The discovery phase uses a high-speed ping system to identify systems; however, the discovery of a new system will require more time as the scanner attempts to connect to various ports. Some attributes will require configuration, which the scanner can be tuned to accommodate. The goal is to accurately identify as much as possible about the new asset so a proper vulnerability analysis can be performed. [Figure 9-26](#ch09.xhtml#ch09fig26) shows an example of Rapid7's Nexpose asset dashboard. Notice systems are broken down by discovery, operating system, and type of potential risk. Using a dashboard such as this allows a security engineer to quickly identify any device that is not part of the original asset list.

![FIGURE 9-26 Nexpose Asset Dashboard](Images/09fig26.jpg)

**FIGURE 9-26** Nexpose Asset Dashboard

### Step 4: Choose Corrective Actions or Accept Risk

Once scanning results show up in your vulnerability management solution, you will have a list of results as well as tickets for scans that did not complete or execute properly. Tickets regarding scans that did not complete must be addressed. Failure to complete could be caused by any of several factors, including unpredicted network interference, not having the correct host login credentials, or changes in the environment. The remaining tickets will be related to identified vulnerabilities.

A dedicated ticketing system is critical for ensuring that all scanning is launched and completed properly as well as for tracking how any found vulnerability is mitigated. Certain systems have predefined timeframes for remediation based on the risk of the vulnerability to the organization. A ticketing system can be set up to prioritize tickets associated with high risk systems. Best practice is to use a ticketing system that does not simply create a ticket per vulnerability instance, or you will quickly be overloaded with too many tickets. Ticketing systems need to create tickets based on vulnerability grouping, which means identifying the same vulnerability within multiple systems and approximating the patch or mitigation for all associated system types. This will allow a more realistic understanding of how many systems are impacted by a vulnerability and the required steps for system-wide mitigation.

As you view tickets, you will need to decide which action to take. Should you attempt to mitigate the risk or does the mitigation process require too much effort to deem it worth doing? This decision merits much further discussion, which leads us to the next section, which is dedicated to responding to vulnerabilities.

## Vulnerability Response

As covered in the previous section, the fourth step for delivering a vulnerability management practice is focused on the `SOC`'s response to an identified vulnerability. All vulnerabilities should not and will not be remediated. If remediation outweighs the risk of leaving the asset vulnerable, then no action should be taken. If the risk of the vulnerability is extremely high, a different approach to remediation needs to be considered that does not put the organization at risk. I will cover these concepts in this section, but first I will cover how to confirm the true risk associated with an identified vulnerability.

### Vulnerability Accuracy
