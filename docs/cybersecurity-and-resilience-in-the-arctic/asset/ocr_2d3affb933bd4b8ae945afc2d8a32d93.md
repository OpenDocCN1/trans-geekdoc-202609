# F. Baiardi et al. / Security and Resilience for a 4.0 Ship

Another example is an attack that as a side effect influences data integrity. If the attack successfully manipulates the inputs of the navigation system, the ship control may be lost [8].

Hence, the interconnection of previous systems implies that some threats for safety may differ from those for cybersecurity, a risk assessment methodology should be able to cover ICT and OT to guarantee an optimal coverage of risk due to safety and/or security. Essentially, this means any assessment should foresee that an attacker may reach his goal through a chain of attacks that starts in one onboard system, e.g. in the guest entertainment system, and then cross some other system and then, through later movements, acquires the control of a physical or logical resource in the power system. Researchers have discovered several of such chains in the automotive world [7] and will be exploited in the maritime one.

# 2.2. Modeling Attacks and Attackers

The ability to model and analyze all the results an attacker needs to reach his/her goal is fundamental to accurately assess the resulting risk as well as to better detect and respond to adversary actions. As previously mentioned, the wide adoption of ICs in 4.0 ships increases the overall complexity of the assessment because an attacker has to execute several steps and reach some critical resource. To discover and anticipate the attacker behavior, Lockheed Martin the Cyber Kill Chain approach [10, 24] has gained popularity among defenders in IT and enterprise networks. The kill chain of an ICT attack aiming to control some resources and, eventually, infiltrate information includes the following:

+   1. Reconnaissance - Research, identification, and selection of targets
2. Weaponization - Coupling a remote access tool with an exploit into a deliverable payload.
3. Delivery - Transmission of the weapon to the target environment.
4. Exploitation - After delivering the weapon to victim host, this triggers intruders' actions
5. Installation - Installation of a remote access trojan or backdoor on the target to maintain persistence inside the environment.
6. Command and Control (C2)
7. Actions on Objectives

Usually, the second step implements the coupling through an automated tool, a weaponizer. The most prevalent delivery vectors for weaponized payloads are email attachments, websites, and USB removable media. The establishment of a C2 channel enables the attacker to access the target environment. According to the cyber kill chain model, after progressing through the first six phases, an attacker can take action to achieve his original objective. Typically, this is data exfiltration, i.e. collecting, encrypting and extracting information from the victim environment; violations of data integrity or availability are potential objectives as well. Alternatively, the intruders may only access to the initial victim box for use as a hop point to compromise admission systems and move laterally inside the network.