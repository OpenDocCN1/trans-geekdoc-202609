
# F. Baiardi et al. / Security and Resilience for a 4.0 Ship

Another example is an attack that as a side effect influences data integrity. If the attack successfully manipulates the inputs of the navigation system, the ship control may be lost [8].

Hence, the interconnection of previous systems implies that some threats for safety may differ from those for cybersecurity, a risk assessment methodology should be able to cover ICT and OT to guarantee an optimal coverage of risk due to safety and/or security. Essentially, this means any assessment should foresee that an attacker may reach his goal through a chain of attacks that starts in one onboard system, e.g. in the guest entertainment system, and then cross some other system and then, through later movements, acquires the control of a physical or logical resource in the power system. Researchers have discovered several of such chains in the automotive world [7] and will be exploited in the maritime one.

## 2.2. Modeling Attacks and Attackers

The ability to model and analyze all the results an attacker needs to to reach his/her goal is fundamental to accurately assess the resulting risk as well as to better detect and respond to adversary actions. As previously mentioned, the wide adoption of ICs in 4.0 ships increases the overall complexity of the assessment because an attacker has to execute several steps and reach some critical resource. To discover and anticipate the attacker behavior, Lockheed Martin the Cyber Kill Chain approach [10, 24] has gained popularity among defenders in IT and enterprise networks. The kill chain of an ICT attack aiming to control some resources and, eventually, infiltrate information includes the following:

- 1. Reconnaissance - Research, identification, and selection of targets
- 2. Weaponization - Coupling a remote access tool with an exploit into a deliverable payload.
- 3. Delivery - Transmission of the weapon to the target environment.
- 4. Exploitation - After delivering the weapon to victim host, this triggers intruders' actions
- 5. Installation - Installation of a remote access trojan or backdoor on the target to maintain persistence inside the environment.
- 6. Command and Control (C2)
- 7. Actions on Objectives

Usually, the second step implements the coupling through an automated tool, a weaponizer. The most prevalent delivery vectors for weaponized payloads are email attachments, websites, and USB removable media. The establishment of a C2 channel enables the attacker to access the target environment. According to the cyber kill chain model, after progressing through the first six phases, an attacker can take action to achieve his original objective. Typically, this is data exfiltration, i.e. collecting, encrypting and extracting information from the victim environment; violations of data integrity or availability are potential objectives as well. Alternatively, the intruders may only access to the initial victim box for use as a hop point to compromise admission systems and move laterally inside the network.

# F. Baiardi et al. / Security and Resilience for a 4.0 Ship

The first problem of this model is that it is not directly applicable to ICS-custom cyber-attacks. An ICS cyber-attack differs from a traditional IT cyber-attack because the underlying engineering shapes and configure ICS components in unique ways. Hence the attacker needs extensive knowledge to affect them in a meaningful and designed way. Only after acquiring this knowledge, an attacker can produce predictable effects on systems in a way that circumvents or impacts safety mechanisms. The knowledge is fundamental to implement a true cyber-physical attack rather than one characterized by espionage, ICS disruption or intellectual property theft. This implies an attacker has to implement a two-stage attack against an ICS. The first stage involves all the steps of the Cyber Kill Chain to gain access to the ICS. The connection of the ICS to the Internet simply simplifies this. In the second stage, the attacker uses the knowledge he has acquired in the first one to meaningfully attack the ICS. Unfortunately, the acquisition of partial information in Stage 1 operations may result in an unintended attack.

A weakness of the Cyber Kill Chain is that it cannot accurately model steps of an attack. As an example, in most attacks, the attacker may repeat the exploitation steps to handle the failure of an exploit. It may even adopt alternative options or targets for the same exploit to handle repeated failures. Furthermore, some steps of the chain, e.g. weaponization or the acquisition of information of some industrial process, are not important in a defensive perspective because it is almost impossible to prevent the attacker from executing these steps.

We believe the system defense should prevent the attacker from acquiring rights on the target system. How the attacker uses these rights and whether it owns the information to affect in a meaningful way the processes the ICS controls is of little interest for the defense. A successful attack against the system implies that at least one attacker owns anything it needs to result in an impact for the ICS owner.

A more interesting framework for our purpose is the MITRE Adversarial Tactics, Techniques, and Common Knowledge (ATT&CK) framework. The goal of this framework is tracking adversarial behavior over time [20]. ATT&CK builds on the Cyber Kill Chain, but rather than describe a single attack, it focuses on the indicators and tactics associated with specific adversaries. ATT&CK uses 11 different tactic categories to describe adversarial behavior:

- 1. Initial Access
- 2. Execution
- 3. Persistence
- 4. Privilege Escalation
- 5. Defense Evasion
- 6. Credential Access
- 7. Discovery
- 8. Lateral Movement
- 9. Collection
- 10. Exfiltration
- 11. Command and Control

Each of these categories includes the tactics, the techniques, and the procedures, TTPs the adversaries adopt and are useful to describe the adversarial's behavior. However, the framework focuses on discovering whether a system can resist specific attacker or an advanced persistent threat whose tactics, techniques, and procedures are known. Instead, both risk assessment and management require an evaluation of the risk due to system vulnerabilities and to the attacks they enable when these attacks are implemented by expedient adversaries.

As an alternative to the Cyber Kill Chain, we propose a solution based upon the discovery of the attack paths to a goal we offers to an attacker. As described in the following sections, a path is a chain of chains from the system attack surface to a goal. Alternatively, we may define a path as an attack chain that grants to an adversary the access rights to control the system resources in its goals.

# 3. The Haruspex Solution

We outline the main features of the Haruspex methodology and its advantages.

The main assumption under the methodology is that we can build models, like digital twins, of the target system and of each attacker. Then, we consider the attack surface of the target system and execute these models in an interactive way to discover and anticipate whether and how attacker reaches its goals. If the evolution is stochastic, we observe several distinct evolutions and populate a database with information collected in each execution. This database stores the synthetic data that replaces the historical databases that usually support a risk assessment. However, the Haruspex database may be richer than a historical one it may cover evolutions that never occurred in the past or with a very low probability by a large impact, i.e. the Haruspex database may describe black swans.

An alternative description of our approach is that the discovery of information to increase the robustness of the target system requires multiple executions of a penetration test. Only multiple executions enable an assessment to discover all the attack chains and to evaluate the effectiveness of countermeasures before deployment. Besides requiring a large human effort, multiple executions of a penetration test also result in a huge disturbance in the target system. The alternative approach we propose automate the penetration test, to minimize the human effort, and uses a model of the system to avoid any noise on the real system.

The proposed methodology naturally satisfies a security-by-design strategy as it can return information to support a risk assessment before deploying or building the target system because it only needs a model of the system and those of the attackers. This enables an assessment to adopt a ‘what if’ approach to discover alternative features of the attackers and of the system influence the overall risk.

## 3.1 Modeling a System and its Attackers

Haruspex adopts a modular model of the target system, seen as a series of interconnected modules. Each module performs some operations the other modules can invoke and it may have vulnerabilities that enable such attacks. The technology, e.g. IT or OT, does not affect the simulation of the attackers and it is not of interesting.
