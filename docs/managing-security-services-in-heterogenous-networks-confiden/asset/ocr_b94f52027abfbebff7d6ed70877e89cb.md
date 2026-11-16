# ## 7.6 Threats in Bluetooth

Threat taxonomy is designed to create a point of reference for threats met, while providing a possibility to shuffle, arrange, amend, and detail threat definitions. Attempts to profile and classify the attackers have been done by R. Brooks et al. [17] and M. Wolf et al. (2005)], where models of attack scenarios have been defined. We reproduce in Figure 7.2 the model proposed by [17], derived from the attack taxonomy used by the CERT [18–20] and adapted to an automotive context. Moreover, in order to gain more knowledge about the attackers, Verendel et al. [21,22] considered the deployment of honeypots in in-vehicle networks, gathering attack data as the attackers have been done in [17] and where models of attack scenarios have been defined.

# ## 7.7 Bluetooth Attack Classification

A comprehensible threat taxonomy is needed for all the security stakeholders, ranging from security experts to novice users of security. The Bluetooth comprehensible taxonomy is needed for its design, development, and implementation.

# ### 7.7.1 Attack Classification Based on Threats

+   - **Denial Of Service** – Battery exhaustion, signal jamming, BlueSYN, Blueper, BlueJacking, vCard Blaster – _Medium_: Main purpose is to deny resources to a target by saturating the communication channel.
+   - **Fuzzer** – BluePass, Bluetooth Stack Smasher, BlueSmack, Tanya, BlueStab–_Medium_: Main purpose is to submit non-standard input to get different results.
+   - **Malware** – BlueBag, Caribe, CommWarrior - _Medium_: Main purpose is to carry out attacks typically using self-replicating form of software.
+   - **Man In The Middle** – BT-SSP-Printer-MITM, BlueSpoof, bthidproxy –_High_: Main purpose is to place a device between