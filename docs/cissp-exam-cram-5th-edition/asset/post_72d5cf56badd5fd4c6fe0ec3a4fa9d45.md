
![](img/cd307d33c10f35ada49ea76811ef60ad_536_0.png)

FIGURE 7.2 Integer Overflow

Source: https://en.wikipedia.org/wiki/Integer_overflow#/media/File:Odometer_rollover.jpg

Testing should focus on more than just input and output data. It should also look at how an application passes data from system to system, subsystem to subsystem, or variable to variable. This is where interface testing comes in. This type of testing is used to verify whether all the interactions between various modules and components are working properly and whether errors are handled properly.

> **Note**
>
> Attackers are always trying to tamper with data. One way they do so is with data diddling attacks. This type of attack works by changing data as it is keyed in or processed by a computer. It can be done to cancel debts without proper authority or assign a large hourly pay increase to an individual. Trying to track down the problem is difficult, and it could be months before such an attack is uncovered. However, regular testing can help bring such attacks to light.

## Security Threats and Vulnerabilities

Now that we have examined some of the types of tests that an organization can perform, let’s turn our attention to some of the threats and vulnerabilities an organization might face. Knowing what threats and vulnerabilities exist allows an organization to build controls to address these specific issues. It is much cheaper to be proactive and build in good controls than it is to be reactive and figure out how to respond after an attack has occurred.

### Threat Actors

The people who threaten the security of your network can be divided into two main groups:

- **Insiders (often disgruntled employees)**: These are individuals who either currently work for the organization or have been fired or quit yet still have access. Insiders could be disgruntled employees or current or former contractors.
- **Outsiders**: These individuals have never worked for you—and you are probably lucky they haven’t. Outsiders can be segregated into several subgroups:
  - **Script kiddies**: These individuals cause harm with scripts, tools, and rootkits written by other, more skilled, individuals. Often, they don’t understand how the exploits they are using work.
  - **Hacktivists**: These hackers have an agenda in that their attacks are driven by the need to protest or make a statement. Hacktivist groups, such as LulzSec and Anonymous, might use distributed denial of service (DDoS) tools or search for and publish private or identifying information about a target; this is known as doxing. Hacktivist is a combination of the words hack and activist. Hacktivists like to refer to themselves as protesters in cyberspace.
  - **Corporate spies**: These individuals work for rival firms. Their goal is to steal your proprietary information or open-source intelligence for competitive advantage.
  - **Skilled hackers**: Although they’re not driven by corporate greed or the desire to advance agendas (as are hacktivists), these individuals do have motives. Maybe they are looking for ways to proclaim their advanced hacking skills, or they might be at odds with a stand or position your organization has taken.
  - **Hacker researchers**: These individuals may accidentally (or intentionally) discover vulnerabilities in a product or infrastructure and then attempt to communicate the issue to the responsible parties.
  - **Organized crime**: The primary motivation of organized crime is to make money. Organized crime activities might include creating and renting botnets, monetizing personally identifiable information (PII), and generating revenue from exploit kits aka crimeware kits and ransomware.
  - **Foreign government agents**: These individuals seek ways to advance the interests of their country, and your data might be the target. These agents may spend months or years crafting highly customized attacks to achieve their objectives.

> **Note**
>
> Being a hacker researcher is not without risk. A hacker known as Weev was part of a group that exposed a flaw in AT&T security, which allowed the email addresses of 114,000 iPad users, including those of celebrities, to be revealed. Weev was charged and found guilty of identity fraud and conspiracy to access a computer without authorization. While the original conviction was later overturned, Weev did serve more than a year of his original sentence.

So, which group represents the biggest threat? The distinction between insiders and outsiders isn’t always useful. Security professionals should not really trust anyone. This has advanced a security concept known as _zero trust_, which means that nothing is trusted by default. This concept is discussed in NIST 800-207.

Insiders typically have the means, access, and opportunity to commit crimes. All they may lack is motive. Outsiders, on the other hand, are not trusted with access, and being outside the organization’s structure could leave them with little opportunity or means to launch an attack. However, outsiders can be driven by motivations like money, prestige, or national interests. Figure 7.3 shows examples of threat actors and sample attacks.

![](img/cd307d33c10f35ada49ea76811ef60ad_539_0.png)

Example Attack Techniques

FIGURE 7.3 Threat Actors and Attacks

> **Note**
>
> Early hackers, known as *phreakers*, focused on analog phone and telecommunication attacks in the 1980s. Some of these individuals would reverse engineer the specific tones used by telecommunications systems to route long-distance/international calls for free.

### Attack Methodologies

Attacks typically target one or more items that are tied to the security triad: confidentiality, integrity, or availability. Whereas confidentiality and integrity attacks actually give the attacker access to your data, availability attacks do not. Availability attacks usually result in denial of service.

Hackers target a variety of devices, but their modus operandi remain fairly constant. Their methodology of attack generally proceeds as follows:

1. **Footprinting**: The attackers identify potential targets, looking for information in places such as the organization’s website, public databases, WHOIS, NSLOOKUP, Google groups, and EDGAR financial records.
2. **Scanning**: The attackers move beyond passive information gathering and use a variety of tools to scan for open ports and processes.
3. **Enumeration**: Somewhat similar to scanning, this step involves obtaining more detailed information about target devices, such as operating system identification. Attackers are likely to probe for poorly protected network shares and weak passwords during this phase.
4. **Penetration**: What makes this phase different from the previous one is that the hacker is attacking the network with the goal of gaining access. If access is not possible, the attacker might decide to launch a DoS attack.
5. **Escalation**: Many times the initial level of access gained by an attacker is not root or administrator. During the escalation phase, a hacker attempts to escalate privilege, pilfer data, and gain access to restricted information.
6. **Expanding access**: The attacker does not stop with access to just one system. Typically, attackers attempt lateral movement to expand their reach.
7. **Covering tracks**: When they’re in control of the system, most hackers seek to destroy evidence of their activities. They are likely to attempt to plant tools and rootkits on the compromised system to further extend their stay. Rootkits typically serve the purpose of leaving backdoors so the attackers can come and go as they please.

> **Note**
>
> Escalation of privilege is required because some computer operations require special privileges to complete their tasks or can be run only from root, system, or administrative accounts. With horizontal privilege escalation, an attacker moves from one user account to another user account that has the same level of access. Vertical privilege escalation occurs when an attacker moves from an account with lower privileges to one with higher privileges.

## Network Security Threats and Attack Techniques

Many threats to network security exist. Many attackers are opportunistic and typically take the path of least resistance, choosing the most convenient route and exploiting the most well-known flaws. Others, such as government spies and corporate hackers, might go to great lengths to gain access to the data or information they desire. In these instances, the attackers or advanced persistent threats (APTs) may spend large amounts of time and money to gain access to resources they covet. As discussed in the following sections, threats to network security can include session hijacking, sniffing, wiretapping, DoS and DDoS attacks, and botnets.

### Session Hijacking

A session hijacking attack allows an attacker to take over an existing connection between two hosts that are communicating. It is an effective type of attack because most TCP services perform authentication only at the beginning of the session. In such a case, the attacker simply waits until authentication is complete and then jumps in and takes control of the session. Session hijacking can be performed at the host-to-host layer or the application layer. Protocols like FTP and Telnet can be targeted through prediction of sequence and acknowledgment numbers, and applications can be targeted at the application layer. You may have noticed that some sites log you in using HTTPS, but they use HTTP for the remainder of the connection. In such situations, the session ID and variable are passed via a plaintext cookie over port 80 instead of port 443.

Preventive measures include limiting incoming connections and using encryption provided by tools like Kerberos or IPsec. Plaintext protocols like
