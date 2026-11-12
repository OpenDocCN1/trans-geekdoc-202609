
37. D. Segmentation can be used to separate systems and applications of different sensitivity levels. A breach of one segmented group should not automatically mean that the other groupings are in immediate danger. Application allow lists control what applications can be installed but do not introduce separation between systems and applications. Monitoring would allow visibility but does not meet the goal Rick has. Least privilege is an effective practice to ensure only the rights required are in place, but again this does not meet the goal.

38. B. This is vishing, or using voice calls for phishing. Spear phishing is targeting a small, specific group. War dialing is dialing numbers hoping a computer modem answers. Robocalling is used to place unsolicited telemarketing calls.

39. C. This is an example of a least privilege implementation where only the privileges required are issued. The checkout process is a modern addition to least privilege environments where even privileges needed are only issued temporarily, making least privilege even more secure. Segmentation and isolation are used to separate systems or environments, and configuration enforcement is used to ensure that configurations continue to be set as expected.

40. A. An insecure, unencrypted, unprotected wireless network will have all of its traffic exposed. If the network is not using WPA-2 or WPA-3, it is trivial to observe network traffic even if an old protocol like WEP was in use.

41. B. Zero-day exploits are new, and they are not in the virus definitions for the antivirus (AV) programs. This makes them difficult to detect, except by their behavior. Remote-access Trojans (RATs), worms, and rootkits are more likely to be detected by AV programs.

42. C. Brute force tries every possible combination with small changes each time. Dictionary attacks use a list of words that are believed to be likely passwords. A rainbow table is a pre-computed table of hashes. Session hijacking is when the attacker takes over an authenticated session.

43. C. A nation-state advanced persistent threat (APT) involves sophisticated (i.e., advanced) attacks over a period of time (i.e., persistent). A distributed denial-of-service (DDoS) could be a part of an APT, but in and of itself is unlikely to be an APT. Brute force attempts every possible random combination to get the password or encryption key. In a disassociation attack, the attacker attempts to force the victim into disassociating from a resource.

44. B. Phishing is not commonly used to acquire email addresses. Phishing emails target personal information and sensitive information like passwords and credit card numbers in most cases.

45. B. A keylogger is a software or hardware tool used to capture keystrokes. Keyloggers are often used by attackers to capture credentials and other sensitive information. A rootkit is used to obtain and maintain administrative rights on a system, and a worm is a self-spreading form of malware that frequently targets vulnerable services on a network to spread.

46. D. Acquisition via the gray market can lead to lack of vendor support, lack of warranty coverage, and the inability to validate where the devices came from. Nick should express concerns about the supply chain, and if his devices need to be from a trusted source or supplier with real support he may need to change his organization's acquisition practices.

47. B. A host-based firewall is an excellent first line of defense for systems that will be deployed to untrusted networks. EDR and XDR are useful for preventing malicious software installs like ransomware, but they do not directly protect against network-based attacks, and disk encryption is a confidentiality control, not a useful tool to prevent network-based attacks.

48. C. The marketing team has created a shadow IT solution—a solution put in place without central or formal IT support, typically done without IT's assistance or awareness. This creates a risk to the organization due to lack of support and may bring additional risks like licensing and compliance risks. The team did not intend to create an issue and is not actively working against the organization, meaning that they are not unskilled attackers, insider threats, or hacktivists.

49. A. Resource inaccessibility is a common symptom of a denial-of-service attack. Impossible travel is typically found in log events through correlation. Missing logs are frequently indicators of compromised accounts deleting logs, and blocked content is most likely due to reputation service usage.

50. B. Since the drives stored sensitive data and no mention of encryption was made, the drives should be physically destroyed to ensure that no data leakage can occur. It is not necessary to destroy the entire system to ensure this. Reformatting drives does not wipe data, and simply removing the system from inventory is typically part of the process but does not protect organizational data.

51. B. A security information and event management tool (SIEM) is designed to ingest and analyze large volumes of logs and then alert on issues and events. Centralized logging is useful but needs additional tools to alert on issues. An IPS is used to detect and potentially respond to network-based attacks, not to gather and analyze logs, and EDR tools are useful for monitoring endpoints, not for large-scale log ingestion and analysis.

52. C. Patrick knows that the first thing he should do is change the administrator password. Any further security changes, including updating firmware and disabling unnecessary services, can be made once the administrative account has been properly secured. Changing the default IP address does not necessarily improve security for the device.

53. B. Paul knows that SSH typically uses port 22, HTTP uses port 80, and HTTPS uses port 443. HTTP is the only unencrypted protocol from that list, and thus he should disable port 80.

54. C. An on-path attack redirects traffic to allow an attacker to see and potentially modify the traffic as shown in the graphic. SQL injection is accomplished by inserting SQL into web queries or application traffic, denial-of-service will target a service and no indication of that is shown, and a directory traversal attack will typically show directory manipulation like . . / . / .

55. B. While dated, NTLM was historically one of the most common targets of credential relay attacks. RDP, SQL, and TLS are less commonly associated with credential relay attacks. Modern protocols implement encryption, session, IDs, and one-time passwords to prevent this type of attack.

56. A. Encryption is the appropriate solution to prevent data loss if a system is stolen. A HIPS, disabling ports and protocols, and changing default passwords will not prevent data acquisition from a drive.

57. D. Derek knows that attacking a digital signature requires that hashes match for both an original document and a malicious document. He will modify the malicious document until he finds a way to convey the changes he needs while retaining the matching hash. This type of attack is why hashing algorithms needs to be resistant to birthday attacks.

58. A. Ashley’s organization was the target of a reflected (and amplified) DDoS where attackers took advantage of DNS queries to make small amounts of spoofed traffic into very large amounts of data sent to her servers. DNS floods, mirrored DDoSs, and supersized query attacks were made up for this question.

59. B. Collisions occur when two files have the same hash. Secure hashing solutions are collision resistant, meaning that collision-based hash attacks should be unlikely unless an insecure or outdated hash algorithm like MD5 is selected. Birthday attacks leverage the likelihood of collisions in a random set of attacks rather than by progressing linearly through the solution set. Bingo attacks and match-the-hash are both made up for this question.

60. C. Firmware is typically not encrypted, but it is commonly digitally signed. Using input validation and code review both help to keep firmware secure.

61. D. Annie’s company is facing a disinformation campaign. If users were simply getting facts wrong, this would be misinformation, but since bots are intentionally misstating information, it is disinformation. Pretexting would attempt to exploit human behaviors to explain why something needed to occur or why an attacker was asking for something. Impersonation occurs when an attacker pretends to be someone they are not.

62. B. In many cases, the best option to limit the attack surface of messaging applications is to use a trusted, internally managed organizational instance rather than public tools or instances. EDR, firewalls, and IPS are not as effective with messaging-based attacks.

63. C. End-of-life announcements typically mean that the equipment is no longer being produced or sold. The equipment will typically have a longer supported life, so Ana can continue to use it but should plan for what to do when end-of-support occurs. At that time, replacing it, isolating it, or purchasing third-party support are all possible solutions depending on Ana’s needs.

64. A. Removable devices like USB thumb drives, digital picture frames, and even keyboards and mice with onboard storage rely on autorun.inf files to automatically run software they provide. While that functionality typically focuses on printing, opening folders, or running media players, it can also be leveraged to automatically run malware. For this reason, many organizations ban removable drives or prohibit autorun from working. Open service ports are commonly associated with applications and services, and autorun doesn’t set up or run these, nor does it impact Wi-Fi. Watering hole attacks require attackers to compromise or gain access to a site that targets commonly visited so that they deliver malware to their targets.
