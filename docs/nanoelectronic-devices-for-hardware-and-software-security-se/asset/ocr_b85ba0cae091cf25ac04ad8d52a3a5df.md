# 7 • Physical Unclonable Functions 143

# 7.3 A SUMMARY OF ATTACKS

Before moving to the next section under fundamental principles and the working of PUF circuits and their properties, it is imperative first to understand the various kinds of attacks and threats that need to be defended against. Prepared with this information about PUFs, it will be clearer to enforce specific security measures and why it is essential to implement particular measures. There are various forms of attack to which an IoT device, a hardware chip, or a computer system may be exposed, and some of which will be covered in this section. The insights into these attacks' tactics help us outline the steps crucial to secure hardware devices and network systems.

# 7.3.1 Replay Attacks

A resourceful intruder can quickly attack a communication channel link to obtain unauthorized access to classified information and therefore be able influence transmitted data. A legitimate transmission of the data is repeated or delayed maliciously or fraudently in a playback attack (replay attacks) without the customers' knowledge [6, 11].

# 7.3.2 Programming Attacks and Machine Learning Attacks

These attacks target the computing device's software and maliciously modify it or install programs that exploit a vulnerability in design and cause a system failure. An adversary may gain remote entry to a computer device when it is connected to public networks. Machine learning attacks are those techniques that attempt to fail hardware models or computing devices by supplying deceptive inputs. The most common reason for a programming attack is to cause a malfunction in IoT devices or hardware systems.

# 7.3.3 Hardware Incidents

These attacks, in theory, can occur at any point throughout the life span of IC chips. When chips are transferred to a foundry for production, attacks can occur there (see Figure 7.3). The noteworthy aspect of hardware attacks related to the security of embedded systems and portable hardware is extremely

| Hardware Trojan insertion | Life Cycle of an IC |
|---|---|
| HT insertion in IP | Third Party IPs and Tools |
| HT insertion in Design | Design House |
| HT insertion by Reverse Engineering | Foundry |
| | Testing |
| | Deployment |

FIGURE 7.3 Hardware Trojan attack during the IC lifecycle.