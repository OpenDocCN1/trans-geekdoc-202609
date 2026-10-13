
## The Discovery Phase

The discovery phase is made up of two parts. First, all network ports and services that fall within scope are identified to develop a list of potential targets. Other techniques might be used, such as dumpster diving, with the goal of gathering information and building a potential target list. These data collection steps fall under the category `target reconnaissance` and are the most time consuming but also the most valuable work. The more quality data that is discovered and collected about a target, the better the capability to identify potential targets to exploit. Some example tools you can use to conduct target reconnaissance are `NMAP` and `masscan` to perform port scanning; `Shodan` to research web-facing resources such as websites, web cameras, and network-enabled IoT devices; and searching social media sources such as `LinkedIn` and `Facebook` for details on people that work within the target network.

The second part of the discovery phase is analyzing the potential targets for vulnerabilities. Vulnerability analysis is commonly performed by comparing the services, applications, and operating systems for potential targets against a vulnerability database or using a tester's own knowledge of vulnerabilities. Tools such as `Metasploit` from `Rapid7` provide a database of known exploits, where you simply type in an identified vulnerability and find various weaponized exploits tied to the weakness. [Figure 6-7](#ch06.xhtml#ch06fig07) shows an example of searching for Apache Struts vulnerabilities within `Metasploit`. Notice how the number of available exploits expands beyond what can be displayed on the screen!

![FIGURE 6-7 Various Apache Struts Exploits in Metasploit](Images/06fig07.jpg)

**FIGURE 6-7** Various Apache Struts Exploits in Metasploit

### Phase 3: Attack

Once targets are confirmed, the actual exploitation occurs during the attack phase. Remember that exploitation does not necessarily mean something bad has already occurred. Exploitation can open the path for malicious actions such as pushing a remote-access tool (RAT), ransomware, or other forms of malware to the system. An example of exploitation could be running an `Armitage`/`Metasploit` weaponized attack against a system that is vulnerable to an exploitation of Struts, as shown in [Figure 6-8](#ch06.xhtml#ch06fig08). The example shows a system has an open shell, meaning the attacker has full access to the compromised system. From this point, the attacker can perform a number of actions, including using this compromised system as a gateway into the network to perform a new attack against internal systems. In the example, the attacker showcases his or her level of access by running the `whoami` command.

![FIGURE 6-8 Using Armitage to Exploit a Struts Vulnerability](Images/06fig08.jpg)

**FIGURE 6-8** Using Armitage to Exploit a Struts Vulnerability

In other cases, the action of exploitation causes negative results, such as exploitation of a website to take it offline, known as a denial-of-service attack. Another example could be overloading the memory of a switch to cause it to fall back into a hub-like state, allowing an attacker to view all traffic within that device. From a penetration testing viewpoint, using the `Cyber Kill Chain` is a good way to view the steps that would be involved with exploiting a target and delivering something, which are the same steps penetration testers and real attackers would use against a target. As a refresher from [Chapter 1](#ch01.xhtml#ch01), [Figure 6-9](#ch06.xhtml#ch06fig09) depicts the `Cyber Kill Chain`. The attack phase of the `NIST` penetration testing process corresponds to the Delivery, Exploitation, Installation, and Command and Control phases of the `Cyber Kill Chain`.

![FIGURE 6-9 Cyber Kill Chain Attack Lifecycle](Images/06fig09.jpg)

**FIGURE 6-9** Cyber Kill Chain Attack Lifecycle

> **Note**
>
> `Kali Linux` and `BackBox` are great free penetration operating system builds you can download and use for penetration testing efforts. `Metasploit` is a great resource you can test your attacks against in a free and legal manner.

### Phase 4: Reporting

The results of the attack phase are documented in the final phase, the reporting phase. Reporting should also include steps from the other phases so the entire penetration testing process is documented. The language used in a report is extremely important, meaning you must know your target audience and consider the impact that will result based on who reviews the report. I have seen people lose their jobs based on negative feedback about their work or how they were blamed for the results of the penetration testing exercise. I recommend at a minimum that your penetration testing report contain the following information:

*   **Vulnerabilities:** What was found during the penetration test? List all vulnerabilities along with details about what they are.
*   **Impact:** What is the potential negative impact that could occur if a real attacker were to take advantage of a vulnerability found during the penetration testing exercise?
*   **Likelihood:** How hard is it to exploit an identified vulnerability? Do you need root access or connectivity to the internal network, or can anybody from anywhere access and exploit the vulnerability?
*   **Risk evaluation:** How do the identified vulnerabilities impact the overall business?
*   **Recommendation:** What is recommended to reduce the risk of the identified vulnerabilities?
*   **References:** Who was involved in the penetration testing exercise?
*   **Additional details:** Make sure to include any appendices, glossary items, tools used, and other details that would help the reader follow the penetration test report.

> **Note**
>
> `SANS` offers great resources for templates for penetration testing reports, at [https://pen-testing.sans.org/resources/downloads](https://pen-testing.sans.org/resources/downloads).

[Figure 6-10](#ch06.xhtml#ch06fig10) shows a diagram of the `NIST SP 800-115` four-stage penetration testing methodology, which is a high-level view of performing a penetration testing exercise.

![FIGURE 6-10 NIST 800-115 Four-Stage Penetration Testing Methodology](Images/06fig10.jpg)

**FIGURE 6-10** NIST 800-115 Four-Stage Penetration Testing Methodology

#### Additional NIST SP 800-115 Guidance

`NIST SP 800-115` provides much more detail as you read further into the document. For example, the attack stage of the `NIST` four-stage penetration testing methodology is further broken down into four steps, as shown in [Figure 6-11](#ch06.xhtml#ch06fig11). The first step is to gain access to the target, also known as establishing a foothold. It is possible that the current privilege level will be limited based on how the access was accomplished, so the next step would be to attempt to escalate privileges to a higher level, such as administrator-level access. Once the highest level of system access is achieved, the third step is to browse the system to discover mechanisms to gain access to other systems. The final step represents the results of the exploit, which might be installing a backdoor, removing data (or documenting the potential to do so), or repeating the process against other internal systems. This cycle is repeated until enough results are generated that can be recorded during the reporting stage of the `NIST` penetration testing methodology.

![FIGURE 6-11 NIST 800-115 Attack Phase Details for Penetration Testing](Images/06fig11.jpg)

**FIGURE 6-11** NIST 800-115 Attack Phase Details for Penetration Testing

> **Note**
>
> There are many other penetration testing resources available, including popular certification programs that train and test on core penetration testing skills, such as the `Certified Ethical Hacker (CEH)` certification program offered by `EC-Council` and the `Offensive Security Certified Professional (OSCP)` certification program.
