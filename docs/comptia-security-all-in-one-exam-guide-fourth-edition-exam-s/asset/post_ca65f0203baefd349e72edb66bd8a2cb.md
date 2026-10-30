
## Answers

1. **B.** Adware is the term used to describe software that typically is free of charge but contains embedded advertisements or the ability to display advertisements while the software is being used. Often, the advertising function can be removed by purchasing the software.

2. **C.** The Xmas attack uses packets with the URG, PUSH, and FIN flags set. Different devices will respond differently to Xmas attacks. Some systems will slow down, some will reboot or crash, and some will drop the packets completely.

3. **D.** If an attacker is able to insert himself into the middle of an encrypted conversation and have each victim believe they are still talking to their original parties in the conversation, then the attacker has successfully executed a man-in-the-middle attack. A man-in-the-middle attack can only succeed if the attacker can impersonate both endpoints in the conversation successfully.

4. **B.** Trojans are malicious programs that often appear to be or do one thing while performing undesirable actions without user approval. Trojan software is named after the Trojan horse from the Trojan War.

5. **A.** Your friend’s computer has been infected with ransomware, software designed to block access to a system until a “ransom” is paid.

6. **D.** If a malicious action takes place at a certain time or date or when specific conditions occur, it is most likely the work of a logic bomb. Logic bombs are malware designed to run undetected until certain conditions are met—a specific time, a specific date, a certain number of mouse clicks, and so on. When those conditions are met, the logic bomb executes its “payload,” which is often something designed to damage, disrupt, or destroy the infected system.

7. **A.** The Smurf attack is one of the very first examples of a DDoS (distributed denial-of-service) attack. In a Smurf attack, the attacker spoofs an ICMP echo request packet from the target’s address and sends it to one or more network addresses. Each host that receives the packet will respond to the target address with an echo reply packet. The attacker is able to distribute the attack among multiple sources and overwhelm the target with traffic.

8. **A.** If you have a piece of malware that is extremely difficult to eradicate no matter how many times you update antivirus signatures, you are most likely facing polymorphic malware. Polymorphic malware is designed to constantly change and make itself increasingly more difficult to detect or remove. The malware “evolves” through techniques like filename changes, compression techniques, variable key encryption, and so on.

9. **D.** A replay attack is a network attack that repeats or delays valid data transmissions. In most replay attack scenarios, an attacker captures a valid traffic stream (such as the submission of login credentials) and “replays” the traffic at a later date.

10. B. www.whitehouse.com is a famous example of typo squatting. Typo squatting involves setting up a website using common misspellings, typos, or errors that occur when users are attempting to reach legitimate sites. For example, users wishing to reach www.whitehouse.gov might mistakenly type “.com” instead of “.gov” and be directed to a completely different website than they intended to visit.

11. A. This is an example of a spear phishing attack. Spear phishing uses fraudulent e-mails targeted at a specific organization or group within an organization. The attack is much more selective and targeted than a phishing attack.

12. C. Your organization is most likely under a DNS poisoning attack. In a DNS poisoning attack, the attacker attempts to corrupt DNS servers or DNS caches in a way that returns an incorrect IP address when DNS resolution takes place. This type of attack is commonly used to divert traffic to one of the attacker’s systems.

13. B. Tricking AV software into believing the malware is located in one location when it’s actually located in another is a common technique used by an armored virus. Armored viruses are designed to be more resistant to detection, reverse engineering, and removal.

14. C. If you are allowed to do something you were previously not allowed to do before running a program (like install software), then the program most likely performed a privilege escalation attack. A privilege escalation attack exploits a bug, flaw, or misconfiguration that allows elevated access to resources and actions that are normally not available to the average user.

15. B. If you are able to access a system on an uncommon port and bypass normal authentication mechanisms, you have most likely discovered a backdoor.

## Social Engineering

In this chapter, you will

- Define basic terminology associated with social engineering
- Identify common user actions that may put an organization’s information at risk
- Recognize methods attackers may use to gain information about an organization
- Examine risks associated with virtualization and cloud environments

Social engineering is the process of convincing an authorized individual to provide confidential information or access to an unauthorized individual. It is a technique in which the attacker uses various deceptive practices to convince the targeted person to divulge information they normally would not divulge or to convince the target of the attack to do something they normally wouldn’t do.

## Social Engineering Methods

Social engineering is an attack against a user, and typically involves some form of social interaction. The weakness that is being exploited in the attack is not necessarily one of technical knowledge, or even security awareness. Social engineering at its heart involves manipulating the very social nature of interpersonal relationships. It in essence preys on several characteristics that we tend to desire. The willingness to help, for instance, is a characteristic one would like to see in a team environment. We want employees who help each other, and we tend to reward those who are helpful and punish those who are not.

If our work culture is built around collaboration and teamwork, then how can this be exploited? It is not simple, but it can be accomplished through a series of subtle ruses. One is built around the concept of developing a sense of familiarity—making it seem as if you belong to the group. For example, by injecting yourself into a conversation or encounter, armed with the right words and the correct information, you can make it seem as if you belong. Through careful name dropping and aligning your story with current events and expectations, you can just slip in unnoticed. Another example is by arriving at a door at the same time as a person with an ID card, carrying something in both your hands, you probably can get them to open and hold the door for you. An even more successful technique is to have a conversation on the way to the door over something that makes you fit in. People want to help, and this tactic empowers the person to help you.

A second method involves creating a hostile situation. People tend to want to avoid hostility, so if you are engaged in a heated argument with someone as you enter the group you wish to join—making sure not only that you are losing the argument, but that it also seems totally unfair—you instantly can build a connection to anyone who has been similarly mistreated. Play on sympathy, their desire for compassion, and use that moment to bypass the connection moment.

A good social engineer understands how to use body language to influence others—how to smile at the right time, how to mirror movements, how to influence others not through words but through body language cues. Any woman that has used body language to get a man to do something without directly asking him to do it understands this game. Men understand as well, and they play because they are attempting to get something as well. When someone has the key information you need for a project, a proposal, or any other important thing, trading a quid pro quo is an unspoken ritual. And if you do this with someone who has malicious intent, then remember the saying, “Beware of Greeks bearing gifts.”

The best defense against social engineering attacks is a comprehensive training and awareness program that includes social engineering, but this does not mean that employees should be trained to be stubborn and unhelpful. Rather, training should emphasize the value of being helpful and working as a team, but doing so in an environment where trust is verified and is a ritual without social stigma. No one will get past TSA employees with social engineering techniques when checking in at an airport, because they dispassionately enforce and follow set procedures, but they frequently do so with kindness, politeness, and helpfulness while also ensuring that the screening procedures are always completed.

![](img/922567202a944c5e8d3ba0168d2ad3a5_279_0.png)

> > **EXAM TIP** For the exam, be familiar with all of the various social engineering attacks and the associated effectiveness of each attack.

## Shoulder Surfing

Shoulder surfing does not necessarily involve direct contact with the target, but instead involves the attacker directly observing the individual entering sensitive information on a form, keypad, or keyboard. The attacker may simply look over the shoulder of the user at work, for example, or may set up a camera or use binoculars to view the user entering sensitive data. The attacker can attempt to obtain information such as a personal identification number (PIN) at an automated teller machine (ATM), an access control entry code at a secure gate or door, or a calling card or credit card number. Many locations now use a small shield to surround a keypad so that it is difficult to observe somebody as they enter information. More sophisticated systems can actually scramble the location of the numbers so that the top row at one time includes the numbers 1, 2, and 3 and the next time includes 4, 8, and 0. While this makes it a bit slower for the user to enter information, it thwarts an attacker’s attempt to observe what numbers are
