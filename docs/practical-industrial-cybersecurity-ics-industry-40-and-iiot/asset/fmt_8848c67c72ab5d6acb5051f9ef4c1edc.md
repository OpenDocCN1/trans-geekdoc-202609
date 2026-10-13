
# Email attachments

# Infected flash drives

# Infected websites

# Watering hole—compromised websites

# Social media interactions

This is the first of three steps in the intrusion portion of the kill chain.

![FIGURE 5.11 Payload deliveries](images/c05f011.png)

**FIGURE 5.11** Payload deliveries

On the defensive side, this step in the chain represents the first opportunity for defenders to stop the intrusion. Ideally, this is the stage where a high percentage of attacks are stopped. The key to defense efforts at this level is to collect and analyze email and web logs for forensic analysis. In particular, you want to analyze the delivery system and determine what its role is in targeting the organization's resources.

## Exploitation

Exploitation can be aimed at hardware or software vulnerabilities, but often it is dependent on human vulnerabilities. This includes victim-triggered exploits such as opening email attachments or clicking website links that lead to a malware exploit.

A common `attack vector` for this type of exploitation involves executing malware, such as a weaponized remote access trojan (`RAT`), through vulnerabilities in the target's operating system or other applications to activate the exploit. Often, these `RATs` are used to create backdoors into the system to provide control over different tasks ranging from administrative tasks (such as adding users) to shutting down the host, recording keystrokes, and even turning on its webcam.

If you pay close attention to Microsoft updates, you'll notice many of them are security updates for Windows, as well as for Microsoft Office. Because many `RATs` are embedded into PDFs and Office files, closing vulnerabilities in Office products is of primary importance to Microsoft. Be sure to install those updates!

Other exploits commonly used in this phase include acting on a zero-day exploit and attacker-triggered exploits for server vulnerabilities. A zero-day vulnerability is one that has not yet been discovered by the software manufacturer or the general cybersecurity population. When attackers find these vulnerabilities, they are able to exploit them until the manufacturer produces a security patch for that vulnerability.

On the defensive side of the exploitation link in the kill chain, there are three general avenues to follow:

*   Personnel cybersecurity training. This extends to specific cyber training for administrators, management personnel, software and web developers, and employees.
*   Penetration testing with regular network vulnerability scanning.
*   Endpoint hardening efforts. Endpoint hardening tools and methods are described in detail in [Chapter 4](#c04.xhtml), "ICS Module and Element Hardening."

## Installation

Now that access has been gained, it becomes necessary to establish a persistent connection to the target. In the example from the previous section, after the `RAT` has been executed, the next step in the chain is to install a backdoor or implant on the target device so that attackers can maintain access to the compromised system. They may also create points of persistence by adding services to the system to aid in their persistence scheme. This is the final step in the intrusion portion of the kill chain, all of which typically takes only seconds to perform.

`RATs` can be executed in a number of ways, but the easiest example is creating a `RAT` that is packaged as an `.exe` file. Because Windows 7, by default, hides the file extension of known file types, appending `.doc` on the end of the file can make it appear to be a document file. Running the file actually executes the trojan.

Defensive measures at this stage of the process include installing host-based intrusion detection and prevention technologies to detect and alert/block common software installation paths. It is also necessary to audit endpoint processes to detect abnormal file creations. Endpoint auditing is covered in detail in [Chapter 10](#c10.xhtml), "ICS Security Monitoring and Incident Response."

## Command and Control

`Advanced persistent threat` (`APT`) malware usually requires an attacker to interact with the malware manually, whereas most malware is automated, sending information back to the attacker without requiring the attacker to do anything.

Because of this, `APT` malware must establish a two-way connection with a `command and control` (`C2`) `server` to establish what is referred to as a `C2 channel`. This `C2 channel` gives attackers the ability to directly interact with the compromised host, which can make the threat very dangerous because the attacker can respond to attempts to mitigate the threat.

With the `C2 channel` in place, the attacker can exfiltrate intellectual property from the target; compromise sensitive data such as confidential emails, company records, and employee information; or infiltrate and infect the entire network.

However, `APT` operations tend to be much more complicated to execute than other types of cyberattacks. They often begin with more common attacks such as SQL or cross-site (`VSS`) efforts to establish the initial infiltration into the target. Then trojans with backdoor shells are installed to create the persistent presence between the attacker and the target.

This link in the chain represents the defender's last chance to kill the attack by identifying and blocking the `C2 channel`. The channel is typically identified through malware analysis methods.

## Actions on Objectives

Once the previous steps have been accomplished, attackers can carry out various objectives such as collecting data and sending it back to the `C2 server`. In many of the attacks that we've talked about, this is one of the main goals of the attackers. The data is anything from credit card information to classified data from companies and governments.

At this point in the chain, the attack has been classified as an incident, and the organization's incident response plan (`IRP`) must be put into action. The progression of the `IRP` is as follows:

1.  Activate the incident response team (`IRT`) to identify and validate the nature of the incident.
2.  Take steps to contain the incident and limit exposure.
3.  Perform a root-cause analysis of the incident to determine the source of the event that caused the incident.
4.  Take steps to remediate the incident.
5.  Take steps to recover from the incident.
6.  Update the `IRP` with lessons-learned information to prevent similar exploits in the future.

This plan is discussed in detail in [Chapter 10](#c10.xhtml).

## Attack Methods

The terms `attack method` and `attack mode` are used to describe the manner or technique an attacker may use to assault an asset (network, computing device, program, or data). The following sections cover a number of different attack methods.

### Broadcast Storms

When `broadcast traffic` is rebroadcast by every network device, the continuous broadcast or `multicast traffic` can quickly overload switches and routers and overwhelm the network. This type of activity is referred to as a `broadcast storm` or a `network storm`, which is depicted in [Figure 5.12](#c05.xhtml#c05-fig-0012).

![FIGURE 5.12 Broadcast storm](images/c05f012.png)

**FIGURE 5.12** Broadcast storm

It is important to monitor networks for `broadcast storms`. However, it is also important to make sure the network is properly configured. If a network node communicates directly with more than one switch, then lookup tables may get confused, causing packets to be flooded between segments. This can represent a major weakness in many networks.

It also important to have hardware that is robust enough to move data quickly and learn routes fast enough to meet the organization's needs. As networks increase to gigabit and faster speeds, it is increasingly important that all network hardware is appropriate for that data rate.
