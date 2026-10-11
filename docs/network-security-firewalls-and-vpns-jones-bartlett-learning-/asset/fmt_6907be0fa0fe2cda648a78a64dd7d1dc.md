
# 1. Preparation
Select and train security incident response team (SIRT) members, allocate resources.

# 2. Detection
Confirm actual breaches.

# 3. Containment
Restrain further escalation.

# 4. Eradication
Resolve the compromise.

# 5. Recovery
Return to normal operation.

# 6. Follow-up
Review the process and improve future responses.

An incident response plan is an important element of network security management.

# Trapping Intruders and Violators

Security often aims at prevention and deterrence. When an intrusion or security violation takes place in spite of the precautions, the next stage or level of security must respond. The next stage of security is detection. Knowing if and when a security violation occurs is essential to a timely and adequate response to a breach.

Once you detect a breach, you must immediately initiate a response. The first stage of response is containment. The goal of containment is to prevent further spread of a known malicious event. Containment is a mindset, a plan of action, and an element of design. As a mindset, containment is the focus of first responders or members of the SIRT. Their goal is to prevent any expansion or spread of the compromise to other systems.

## Why Containment Is Important

Containment can be as simple as unplugging a network cable from a compromised system. This effectively cuts off any communication to and from the suspect host. You can also impose containment by disabling user accounts, stopping services, adding entries to filtering devices, and so on. Whatever the vector or source of the malicious event, its source or target should be cut off from causing continued harm.

The act of containment should interrupt or interfere with the continued spread or operation of the unwanted event. This type of initial response is often effective against malicious code, remote access, backdoor control, a compromised user account, social engineering, and many other forms of network or system compromise.

Containment is often considered a form of response. Containment is the action taken by a first responder. However, even before you experience a security breach, you can employ another preventative measure similar to containment known as compartmentalization.

## Imposing Compartmentalization

Compartmentalization is the element of infrastructure design that takes into account the likelihood of a security breach by malicious code or some other intruder. Compartmentalization distinctly separates a network into areas or zones of access. Often, these zones are around departments or entities that commonly interact over the network. Any entity that does not commonly interact is separated by default using network security access control devices such as routers, switches, and firewalls.

The purpose of compartmentalization is to create small collectives of systems that support work tasks while minimizing risk. The typical risk is that if one system is compromised, the breach can quickly lead to other systems being compromised. This is especially true of malicious code, which distributes rapidly. But it can also apply to remote hacker intrusion as the hacker attempts to leap from system to system, searching out valuable resources.

Network compartmentalization is similar to the bulkheads on ships. In the event of a hull leak, the bulkhead doors of the affected compartment close and seal. This prevents the entire ship from being sunk by a single breach. The same is true for computer network compartmentalization. When you detect a breach, you can sever the links between network compartments to prevent any further malicious communication to or from the affected sections.

## Using Honeypots, Honeynets, and Padded Cells

Another specific intruder trap you can add to a security infrastructure is a honeypot. A honeypot is a hacker or intruder trap. A honeypot is a system or network that appears to contain valuable information, and appears to be part of a legitimate organizational network, but in fact is a specially designed trap. The purpose of a honeypot is to trap hackers/intruders, detect new attacks, or simply serve as a decoy to deflect attacks from reaching the actual primary network.

A honeypot can be a single system or a network of many systems constructed to look, act, and operate like a real network environment, containing seemingly attractive but actually fake resources. For a honeypot to be effective, it must look and act just like a real target. Otherwise, hackers will quickly uncover that it is fake and search harder to find the real targets. A honeypot often includes extensive focus auditing and recording capabilities to thoroughly capture all activities that take place within it.

Honeypots can be single systems or multiple networked systems. A network of honeypots is sometimes called a `honeynet`. Both honeypots and honeynets are decoy systems that are always operating in the hopes of attracting would-be hackers and intruders. Another form of honeypot is the `padded cell`. The padded cell is turned on only after you detect an intruder; you then lure the intruder into entering the padded cell.

Configure and situate honeypots so that they do not interfere with authorized users performing authorized activities. However, you need to position them along common pathways of access that an outsider or intruder might take, in much the same way a hunter will hide along a game trail in the forest. A honeypot should be attractive and interesting enough to persuade a hacker to attack it, but not too attractive as to trigger that voice in the back of the hacker’s mind that says, “It’s a trap.”

A honeypot has value in two primary circumstances. First, if the organization’s primary goal is to learn about new hacking exploits, then a honeypot can serve as a laboratory for that purpose. Second, if the organization’s primary goal is to prosecute criminals, then a honeypot may assist in the discovery, identification, and apprehension of suspects. However, if neither of these two purposes is a primary goal of the organization, then deploying a honeypot is generally not a worthwhile endeavor.

# Essential Host Security Controls

Every host needs protections from its users as well as from the network it communicates with. There are always risks, even within a private network, from authorized users. Precautions include equipping host devices with reasonable defenses against known potential avenues of compromise.

Every host needs an antivirus scanner. While malicious code is not as serious a threat in some operating systems as in others, hackers create malware for every platform. You can no longer safely claim immunity based on your operating system selection alone.

An antivirus scanner needs to be current. The scanner engine, the core mechanisms for malware detection, should be less than a year old. Typically, a deployed antivirus should have the current year in its name or as its build date. Any antivirus scanner more than a year old is too out of date with new and current scanning technologies, malicious embedding techniques, and cleanup and removal procedures.

An antivirus scanner needs to have its database of definitions updated at least once per day. This should be an automated process so that as soon as the vendor releases a new update, it is downloaded and applied. Using a scanner with an old database is just as bad as using an old scanner. An antivirus product provides protection only against known threats, so don’t allow your antivirus software to develop amnesia from delayed updates.
