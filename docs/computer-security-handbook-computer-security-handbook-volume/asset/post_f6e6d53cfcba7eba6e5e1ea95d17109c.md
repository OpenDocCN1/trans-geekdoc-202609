
For example, some services, such as anonymous File Transfer Protocol (FTP), may be enabled on some systems and not on others. Even actions that are normally viewed as hostile, such as attempts to bypass access controls to gain entry into a privileged account, may be authorized in special circumstances, such as during an approved test of system security or in the use of a “back door” during development. System owners or their administrators make the determination of what actions they consider authorized for their systems by establishing a security policy.29 Here are the definitions for authorized and unauthorized.

**Authorized**—approved by the owner or administrator.
**Unauthorized**—not approved by the owner or administrator.

The steps *action* and *target* in Exhibit 8.1 are the two parts of an event as discussed in Section 8.4.1. The following sections discuss the other steps: *tool*, *vulnerability*, and *unauthorized result*.

### 8.4.2.1 Tool.

The first step in the sequence that leads attackers to their unauthorized results is the *tool* used in the attack. A tool is some means that can be used to exploit a vulnerability in a computer or network. Sometimes a tool is simple, such as a user command or a physical attack. Other tools can be very sophisticated and elaborate, such as a Trojan horse program, computer virus, or distributed tool. We define *tool* in this way.

**Tool**—means of exploiting a computer or network vulnerability.

The term “tool” is difficult to define more specifically because of the wide variety of methods available to exploit vulnerabilities in computers and networks. When authors make lists of methods of attack, often they are actually making lists of tools. Based on our experience, these categories of tools are currently an exhaustive list. (See Exhibit 8.3)

- **Physical attack**—means of physically stealing or damaging a computer, network, its components, or its supporting systems (e.g., air conditioning, electric power, etc.).
- **Information exchange**—means of obtaining information either from other attackers (e.g., through an electronic bulletin board) or from the people being attacked (commonly called social engineering).
- **User command**—means of exploiting a vulnerability by entering commands to a process through direct user input at the process interface. An example is entering UNIX commands through a telnet connection or commands at a protocol’s port.
- **Script or program**—means of exploiting a vulnerability by entering commands to a process through the execution of a file of commands (script) or a program at the process interface. Examples are a shell script to exploit a software bug, a Trojan horse log-in program, or a password-cracking program.
- **Autonomous agent**—means of exploiting a vulnerability by using a program or program fragment that operates independently from the user. Examples are computer viruses or worms.

Denial of service—intentional degradation or blocking of computer or network resources.

Theft of resources—unauthorized use of computer or network resources.

## 8.4.3 Full Incident Information Taxonomy.

Often attacks on computers and networks occur in a distinctive group that we would classify as being part of one incident. What makes these attacks a distinctive group is a combination of three factors, each of which we may only have partial information about.

- 1. There may be one attacker, or there may be several attackers who are related in some way.
- 2. The attacker(s) may use similar attacks, or they may be trying to achieve a distinct or similar objective.
- 3. The sites involved in the attacks and the timing of the attacks may be the same or may be related.

Here is the definition of incident:

Incident—group of attacks that can be distinguished from other attacks because of the distinctiveness of the attackers, attacks, objectives, sites, and timing.

The three parts of an incident are shown in simplified form in Exhibit 8.4, which shows that an attacker, or group of attackers, achieves objectives by performing attacks. An incident may comprise one single attack or multiple attacks, as illustrated by the return loop in the figure.

Exhibit 8.5 shows the full incident information taxonomy. It shows the relationship of events to attacks and attacks to incidents, and suggests that preventing attackers from achieving objectives could be accomplished by ensuring that an attacker cannot make any complete connections through the seven steps depicted. For example, investigations could be conducted of suspected terrorist attackers, systems could be searched periodically for attacker tools, system vulnerabilities could be patched, access controls could be strengthened to prevent actions by an attacker to access a targeted account, files could be encrypted so as not to result in disclosure, and a public education program could be initiated to prevent terrorists from achieving an objective of political gain.

### 8.4.3.1 Attackers and Their Objectives.

People attack computers. They do so through a variety of methods and for a variety of objectives. What distinguishes the categories of attackers is a combination of who they are and their objectives (what they want to accomplish).

Attacker—individual who attempts one or more attacks in order to achieve an objective.

Objective—purpose or end goal of an incident.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_286_0.png)

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_287_0.png)

### Exhibit 8.5 Computer and Network Incident Information Taxonomy

Based on their objectives, we have divided attackers into a number of categories:

- **Hackers**—attackers who attack computers for challenge, status, or the thrill of obtaining access. (Note: We have elected to use the term “hacker” because it is common and widely understood. We realize that the term’s more positive connotation was once more widely accepted.)
- **Spies**—attackers who attack computers for information to be used for political gain.
- **Terrorists**—attackers who attack computers to cause fear, for political gain.
- **Corporate raiders**—employees (attackers) who attack competitors’ computers for financial gain.
- **Professional criminals**—attackers who attack computers for personal financial gain.
- **Vandals**—attackers who attack computers to cause damage.
- **Voyeurs**—attackers who attack computers for the thrill of obtaining sensitive information.

These seven categories of attackers and their four categories of objectives as shown in the leftmost and rightmost blocks of Exhibit 8.5 are fundamental to the difference between incidents and attacks. This difference is summed up in the phrase “attackers use attacks to achieve objectives.”

## 8.5 ADDITIONAL INCIDENT INFORMATION TERMS.

The taxonomy of the last section presented all of the terms in the common language for computer security that describe how attackers achieve objectives during an incident. However, some other, more general terms are required to fully describe an incident. The next sections discuss these terms.

### 8.5.1 Information release

An example would be to replace a site name, such as the fictitious widgets.com, with numbers and the upper-level domain name, such as 123.com.

Response teams often use incident numbers to track incidents and to identify incident information.

Incident number—reference number used to track an incident or identify incident information.

The last term we found to be of use is corrective action, which indicates those actions taken in the aftermath of an incident. These actions could include changing passwords, reloading systems files, talking to the intruders, or even criminal prosecution. Information on corrective actions taken during or after an incident is difficult to obtain for incident response teams, since response team involvement generally is limited to the early stages of an incident. CERT/CC records indicate that the variety of corrective actions is extensive, and a taxonomy of corrective actions may be a desirable future expansion of the common language.

Corrective action—action taken during or after an incident to prevent further attacks, repair damage, or punish offenders.

## 8.6 HOW TO USE THE COMMON LANGUAGE.

Two things are important to emphasize about using the common language for computer security incident information. First, the common language really is a high-level set of terms. As such, it will not settle all the disputes about everything discussed concerning computer security incidents. For example, the common language includes “autonomous agent” as a term (a category of tool). Autonomous agents include computer viruses, worms, and the like, regardless of how those specific terms might be defined. In other words, the common language does not try to settle disputes on what should or should not be considered a computer virus but rather deals at a higher level of abstraction (“autonomous agent”) where, it is hoped, there can be more agreement and standardization. Stated another way, participants in the Common Language Project workshops anticipated that individuals and organizations would continue to use their own terms, which may be more specific in both meaning and use. The common language has been designed to enable these lower-level terms to be classified within the common language structure.

The second point to emphasize is that the common language, even though it presents a taxonomy, does not classify an incident (or individual attacks) as any one thing. Classifying computer security attacks or incidents is difficult because attacks and incidents are a series of steps that an attacker must take. In other words, attacks and incidents are not just one thing but rather a series of things. That is why I say the common language provides a taxonomy for computer security incident information.

An example of the problem is found in the popular and simple taxonomies often used to attempt to classify incidents. They appear as a list of single, defined terms. The following terms from Icove, Seger, and VonStorch provide an example.34

- Covert channels
- Denial of service
- Excess privileges
- Logic bombs
- Salamis
- Software piracy
- Trap doors
- Unauthorized data copying
- Data diddling
- Dumpster diving
- Harassment
- Masquerading
- Scanning
- Timing attacks
- Trojan horses
- Viruses and worms
- Degradation of service
- Eavesdropping on emanations
- IP spoofing
- Password sniffing
- Session hijacking
- Traffic analysis
- Tunneling
- Wiretapping
