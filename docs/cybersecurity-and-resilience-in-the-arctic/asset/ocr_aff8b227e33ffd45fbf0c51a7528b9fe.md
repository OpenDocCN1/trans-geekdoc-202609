# F. Baairi et al. / Security and Resilience for a c-lo Ship

The first problem of this model is that it is not directly applicable to ICS-custom cyber-attacks. An ICS cyber-attack differs from a traditional IT cyber-attack because the underlying engineering shapes and configure ICS components in unique ways. Hence the attacker needs extensive knowledge to affect them in a meaningful and designed way. Only after acquiring this knowledge, an attacker can produce predictable effects on systems in a way that circumvents or impacts safety mechanisms. The knowledge is fundamental to implement a true cyber-physical attack rather than one characterized by espionage, ICS disruption or intellectual property theft. This implies an attacker has to implement a two-stage attack against an ICS. The first stage involves all the steps of the Cyber Kill Chain to gain access to the ICS. The connection of the ICS to the Internet simply simplifies this. In the second stage, the attacker uses the knowledge he has acquired in the first one to meanfully attack the ICS. Unfortunately, the acquisition of partial information in Stage 1 operations may result in an unintended attack.

A weakness of the Cyber Chain is that it cannot accurately model steps of an attack. As an example, in most attacks, the attacker may repeat the exploitation steps to handle the failure of an exploit. It may even adopt alternative options or targets for the same exploit to handle repeated failures. Furthermore, some steps of the chain, e.g. weaponization or the acquisition of information of some industrial process, are not important in a defensive perspective because it is almost impossible to prevent the attacker from executing these steps.

We believe the system defense should prevent the attacker from acquiring rights on the target system. How the attacker uses these rights and whether it owns the information to affect in a meaningful way the processes the ICS controls is of little interest for the defense. A successful attack against the system implies that at least one attacker owns anything it needs to result in an impact for the ICS owner.

A more interesting framework for our purpose is the MITRE Adversarial Tactics, Techniques, and Common Knowledge (ATT&CK) framework. The goal of this framework is tracking adversarial behavior over time [20]. ATT&CK builds on the Cyber Kill Chain, but rather than describe a single attack, it focuses on the indicators and tactics associated with specific adversaries. ATT&CK uses 11 different tactic categories to describe adversarial behavior:

+   1. Initial Access
2. Execution
3. Persistence
4. Privilege Escalation
5. Defense Evasion
6. Credential Access
7. Discovery
8. Lateral Movement
9. Collection
10. Exfiltration
11. Command and Control

Each of these categories includes the tactics, the techniques, and the procedures, TTPs the adversaries adopt and are useful to describe the adversarial's behavior. However, the framework focuses on discovering whether a system can resist specific