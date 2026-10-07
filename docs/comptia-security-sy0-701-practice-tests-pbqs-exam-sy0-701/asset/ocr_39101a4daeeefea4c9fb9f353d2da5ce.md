Option A is incorrect. While an IDS can provide alerts on malicious activities based on specific signatures or heuristics, it does not provide detailed flow data analysis like NetFlow.

Option B is incorrect. A Syslog server is mainly used for collecting and storing log data from various devices. It does not focus on detailed network traffic flow like NetFlow.

Option D is incorrect. SNMP traps are for sending unsolicited alert messages from a device to a management station regarding specific events. They don’t provide traffic flow analysis.

Question 378. A large financial institution recently experienced a security breach where an attacker was able to bypass its intrusion detection system (IDS). Upon investigation, the security team found out that the attacker utilized a zero-day exploit. In the aftermath, what should the institution do to enhance the capability of its IDS?

+   (A) Switch from a signature-based IDS to a behavior-based IDS

+   (B) Disable the IDS and rely solely on firewall rules

+   (C) Update the IDS with the latest threat intelligence feeds and signatures

+   (D) Reduce the frequency of IDS signature updates

Explanation 378. **Correct Answer: A. Switch from a signature-based IDS to a behavior-based IDS.** Behavior-based IDS (or anomaly-based IDS) monitors network traffic and compares it against an established baseline, allowing it to potentially detect zero-day exploits and other novel attacks that signature-based systems might miss.