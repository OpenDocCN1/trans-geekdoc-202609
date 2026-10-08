you’re looking for, but searching for anomalies in a packet capture looking for the proverbial “needle in a haystack.” D is incorrect because spatial trend analysis deals with correlating between different geographical areas.

+   7. Based on your assumptions, how will you likely discover the malware?

+   A. The packet trace will reveal a port famous for malware.

+   B. The IDS log will show a matched signature.

+   C. Your experience will guide your analysis.

+   D. The long-term degradation in availability.

+   C is correct. Heuristic analysis can't rely on a signature or known behavior. Instead, experience best guides your analysis.

+   A, B, and D are incorrect. A and B are incorrect because the answer suggests a known signature (famous malware port or an IDS signature). D is incorrect because although trend analysis might point out symptomatic differences, it will not discover and identify the malware.

+   8. Select the most valuable data sources in this analysis. (Choose two).

+   A. IDS/IPS

+   B. Router logs

+   C. Security logs of affected servers

+   D. Next-Generation Firewall

+   A and D are correct. The intrusion detection/prevention system very likely logged information relevant for your analysis. Similarly, the firewall might show if or malicious traffic passed through to the affected systems.

+   B and C are incorrect. The router log is unlikely to reveal any information specific to the suspected malware. The security logs of affected systems might yield valuable information. However, if the system is compromised, you cannot trust its logs as complete or accurate.

+   9. Which of the following would be the most valued SIEM tool in this scenario?

+   A. Bro

+   B. Snort

+   C. Splunk

+   D. ELK

+   A is correct. Bro is both signature- and anomaly-based. Bro will watch sessions, monitoring for strange behavior. Bro is also able to extract executables from network traffic, retaining them for forensic analysis.