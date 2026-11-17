# # Dictionary Password Attacks

A dictionary password attack is a simple attack that relies on users making poor password choices. In a dictionary password attack, a simple password-cracker program takes all the words from a dictionary file and attempts to log on by entering each dictionary entry as a password.

Users often engage in the poor practice of selecting common words as passwords. A password policy that enforces complex passwords is the best defense against a dictionary password attack. Users should create passwords composed of a combination of letters and numbers, and the passwords should not include any personal information about the user.

# # IP Address Spoofing

Spoofing is a type of attack in which one person, program, or computer disguises itself as another person, program, or computer to gain access to some resource. A common spoofing attack involves presenting a false network address to pretend to be a different computer. An attacker may change a computer's network address to appear as an authorized computer in the target's network. If the administrator of the target's local router has not configured it to filter out external traffic with internal addresses, the attack may be successful. IP address spoofing can enable an attacker to access protected internal resources.

> > **NOTE**
> > A CERT advisory on IP spoofing reports that the CERT Coordination Center has received reports of attacks in which intruders create packets with spoofed source IP addresses. This exploit leads to user impersonation and escalated privilege access on the target system. This means that the intruder can take over logon connections and create havoc.

Address resolution protocol (ARP) poisoning is an example of a spoofing attack. In this attack, the attacker spoofs the MAC address of a targeted device, such as a server, by sending false ARP resolution responses with a different MAC address. This causes duplicate network traffic to be sent from the server. Another type of network-based attack is the Christmas (Xmas) attack. This type of attack sends advanced TCP packets with flags set to confuse IP routers and network border routers with TCP header bits set to 1, thus lighting up the IP router like a Christmas tree.

# # Hijacking

Hijacking is a type of attack in which the attacker takes control of a session between two machines and masquerades as one of them. There are a few types of hijacking:

+   - **Man-in-the-middle hijacking**—In this type of hijacking, discussed in more detail in a moment, the attacker uses a program to take control of a connection by masquerading as each end of the connection. For example, if Mary and Fred want to communicate, the attacker pretends to be Mary talking to Fred and pretends to be Fred when talking to Mary. Neither Mary nor Fred know they are talking to the attacker. The attacker can collect substantial information and can even alter data as they flow between Mary and Fred. This attack enables the attacker to either gain access to the messages or modify them before retransmitting. A man-in-the-middle attack can occur from an insider threat. An insider threat can occur from an employee, contractor, or trusted person within the organization.

+   - **Browser or URL hijacking**—In a browser or URL hijacking attack, the user is directed to a different website than what he or she requested, usually to a fake page that the attacker