creating several images might be more work than it is worth. Having them specific to the subnet makes little practical sense. D is incorrect because a vulnerability scan is a good idea, but it does not address the ongoing practice of installing an image with several services running.

+   11. Which of the following are the method and purpose of a DNS sinkhole? (Choose two.)

+   A. Redirecting DNS queries away from a known-malicious server

+   B. Providing no DNS resolution responses

+   C. Logging DNS resolution requests to determine infected hosts

+   D. Logging DNS redirects to the infected domain

+   A and C are correct. The method of a DNS sinkhole is to redirect DNS queries by infected machines away from a known malware server. The purpose of a DNS sinkhole is to log DNS resolution requests to help identify what other machines are likely infected.

+   B and D are incorrect. B is incorrect because the DNS sinkhole does return DNS responses, but just to an internal server, one on which queries are logged. D is incorrect because the malicious domain is already known.

+   12. A company has a significant investment in intrusion detection systems, which are able to inspect traffic with significant speed and reasonable effectiveness. However, a recent incident reveals that employees used point-to-point encryption to mask data exfiltration. What would be the best recommendation for the IDS to the company?

+   A. Upgrade the IDS.

+   B. Employ endpoint security controls.

+   C. Prohibit all uses of encryption.

+   D. Replace the suspected employees.

+   B is correct. Endpoint security is a necessary complement to network security. In this case, endpoint security controls would allow inspection of network traffic before it is encrypted.

+   A, C, and D are incorrect. A is incorrect because an IPS will not be able to view and inspect encrypted traffic. C is incorrect because banning widespread use of encryption might cause more harm than good, knowing the full impact of such a ban. D is incorrect because employees cannot be terminated without just cause.

+   13. What type of network access control is being demonstrated in Figure 3-1?