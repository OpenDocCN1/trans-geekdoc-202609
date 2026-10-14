+   **VoIP**
+   
+   - Highly sensitive to latency, jitter, packet loss, and reduced bandwidth
+   - Users are extremely intolerant of downtime
+   - VoIP generates extensive traffic that can overload a network
+   
+   **Eavesdropping**
+   
+   **Denial-of-Service Attacks**
+   
+   - Even small increases in latency and jitter can be highly disruptive
+   
+   **Caller Impersonation**
+   
+   - Useful in social engineering
+   - Attacker can appear to be the president based on a falsified source address
+   
+   **Hacking and Malware Attacks**
+   
+   - Compromised clients can send attacks
+   - Compromised servers can do disruptive signaling
+   
+   **Toll Fraud**
+   
+   - Attacker uses corporate VoIP network to place free calls
+   
+   **Spam over IP Telephony (SPIT)**
+   
+   - Especially disruptive because it interrupts the called party in real time
+   
+   **New Threats Appear Constantly**
+   
+   - Injecting the attacker’s voice into a conversation

# Figure 8–31

VoIP Threats (Study Figure)

VoIP traffic is especially sensitive to latency. If latency rises to only 150 ms to 250 ms, turn-taking in calls becomes almost impossible. Just when you think that the other person has stopped talking and you begin to talk, more of their voice comes through, interrupting you.

# Caller Impersonation

On the telephone, a caller can claim to be someone they are not. On the PSTN, caller ID reduces this risk somewhat by giving you the actual number of a caller. **Caller impersonation** is also possible with IP telephones and soft phones. In fact, it can be more effective. If call identification in VoIP gives a person’s name or organizational position as well as their IP telephone number, impersonation will seem even more legitimate. If the president of the company or the chief of security calls you, you are likely to do what they tell you to do.

# Hacking and Malware Attacks

If an attacker hacks a VoIP telephone or VoIP server or successfully places malware on one, he or she will “own” the device. Additional attacks using the compromised device become trivial. For instance, the attacker can send SIP BYE commands to many phones, causing conversations to terminate.

# Toll Fraud

So far, we have been looking at sophisticated attacks aimed at large malicious goals. A smaller but still important threat is **toll fraud**—breaking into a corporate VoIP system in order to place free long-distance and international telephone calls. Although this may seem like a trivial threat, a break-in followed by the sharing of the exploit with many attackers can lead to substantial dollar losses.