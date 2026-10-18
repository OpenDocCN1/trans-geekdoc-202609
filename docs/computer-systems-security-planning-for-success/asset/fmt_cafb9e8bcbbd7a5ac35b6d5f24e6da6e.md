
Unfortunately it may be impossible to roll back some assets to a previously uncompromised state, in which case they may need to be restored from a backup or failing that rebuilt from the ground up. Backups make recovery much simpler and companies that do not have a backup plan typically implement them after their first incident. That being said, malware may have also found its way into the backups if given enough time on the system. In that case the asset is typically destroyed and a new one is built. While this can take a long time, it is one of the few ways to know for sure that the asset isn’t compromised.

### 9.4.5. Remediation

Remediation is focused on making sure that an incident can’t happen again. Remediation may entail patches, firewall changes, IoC database updates, or even adding more layers of security. The goal is to ensure that all assets are safe.

### 9.4.6. Reporting

Reporting is a critical step. It is important to collect timestamped logs as well as accounts of how the incident plans were rolled out. This can help you determine if the plans should be changed and can help you know what to look for in the future. In the best case scenario good reporting lets you catch future precursors before they become incidents.

Disclosure is also an important aspect of the reporting phase. Both compliance and basic ethics mandate that customers be made aware of any data lost. By disclosing the details of an incident you can also other companies aware of what types of attacks are occurring "in the wild."

## 9.5. MITRE ATT&CK Framework

In the [Malware](#index.xhtml#_malware) chapter we covered Lockheed Martin’s Cyber Killchain attack analysis framework. Cyber killchain is not the only analysis framework available, a popular alternative is the [MITRE ATT&CK framework](https://attack.mitre.org). ATT&CK has 14 sections that cover adversarial tactics, techniques, and common knowledge. Each section is separated into different matrices that have their own sub-techniques.

Developed in 2013, the ATT&CK framework is a modern way of looking at an incident that can help drive decision making regarding response and continuity.

### 9.5.1. Reconnaissance

Reconnaissance is the act of collecting information about a target. This typically involves vulnerability scanning, network mapping, and phishing. Attackers are generally looking for weak links and a way in to the company. Understanding how reconnaissance is performed can help a security team pick up on the precursors to an incident.

### 9.5.2. Resource Development

Resource development involves acquiring infrastructure from which to deploy an attack. This may involve impersonation or custom tailoring exploits based on the results of the previous reconnaissance. In the resource development phase, all the actions needed to set the stage for an attack are performed.

### 9.5.3. Initial Access

Initial access refers to the first breach of security. There are many ways for this to occur, but some common ones are phishing, someone clicks on a link in an email, or through a compromised accounts. Attackers may find it easier to exploit the underlying software a corporation uses as is the case in a supply chain attack. There are even instances of attackers leaving rogue flash drives in common areas or attacking WiFi networks from nearby cars.

However it is performed, initial access is the first real compromise in an attack.

### 9.5.4. Execution

Execution involves running the commands or scripts needed to perform the rest of the attack. Much of this may be automated through `PowerShell` or `BASH` scripts. These scripts will exploit vulnerability, setup tasks to run, download and install software, and possibly even give attackers a foothold for internal spearphishing.

### 9.5.5. Persistence

Persistence is the act of setting up a system or systems to continue to run the malware that has been implanted. This may involve autostart execution of scripts, init scripts on a Linux system, creating new accounts, scheduling tasks to run, or even implanting the code within or in place of another executable or macro-enabled document. With persistence, the attacker can be sure that even if the machine is restarted or not fully wiped the malicious code will run again.

### 9.5.6. Privilege Escalation

Once an attacker has a foothold on the internal network they will typically work to elevate privilege. This may be done locally, through an exploit, by tricking the user into elevating the privileges of a running script, by stealing credentials over-the-wire, or by leveraging running system processes.

The key in this phase is that the security of the machine has been breached, but if the attacker does not have an admin account on the machine the actual extend of the damage may not be that bad. By elevating the privilege to an admin the attacker can fully control the asset.

### 9.5.7. Defense Evasion

It is important to note that while this is occurring, malware scanners, endpoint management software, and possibly even members of the SOC will be actively working to detect and remove malware. An attacker will take steps, typically automated, to make it had to detect their presence. This may involve disabling malware scanners, clearing logs, deploying in a container, running within an already running process, and other methods of obfuscation. Defense evasion makes the job of the security team that much harder.

### 9.5.8. Credential Access

With malware running on at least one machine, an attacker may attempt to steal credentials. This could involve logging key strokes, performing MitM attacks n the local network, brute force programs, cracking locally stored hashes, or exploiting password managers. Credentials give an attacker a means to log in to other machines on the network and expand their assets.

### 9.5.9. Discovery

A malicious actor will try to collect as much information as possible about the environment in which they are operating. Knowing about available accounts, types of network traffic, running services, stored passwords, and security countermeasures help them make informed decisions regarding next steps. Internal policies can also be helpful, it’s much easier to guess passwords when you know the company password policy. Expect that at some point after initial access, an attacker will try to gain more information.

### 9.5.10. Lateral Movement

Lateral movement refers to moving across internal systems without any major change in privilege. This may refer to a compromised user account being used to compromise other user accounts. The more accounts an attacker has access to, the more effectively they can learn about the environment. Having access to multiple accounts also gives the attacker more options for persistence, credential access, and internal spearphishing.

### 9.5.11. Collection

Data can be collected from workstation keyboards, as well as laptop cameras and microphones. Local system data, shared drive data, and removable media data can all be harvested as well. Emails can be skimmed and stored and in some instances screen recordings may also be employed. Much like in Discovery an attacker is often after as much data as they can possibly collect.

### 9.5.12. Command and Control

Command and Control (`C2` or `C&C`) refers to the process of setting up a channel between the compromised internal systems and an external system. This channel can be used to get data off the compromised machines and/or for putting malware on the machines. A `C2` channel allows the operator to send interact with the compromised machines and even automate much of the work.
