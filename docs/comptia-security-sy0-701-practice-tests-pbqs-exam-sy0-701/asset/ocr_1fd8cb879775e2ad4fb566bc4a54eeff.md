While it ensures the integrity and confidentiality of the email content, it does not validate the sender’s domain to the recipient.

**Question 363.** After a security incident, a forensic investigation revealed that a compromised internal workstation was communicating with a known malicious IP address. To prevent further communication, the security team decided to take immediate action. Which of the following is the BEST immediate action to ensure the workstation cannot communicate with that IP?

+   (A)** Implement a block rule on the web filter for the IP address
**(B)** Disable the network port of the compromised workstation
**(C)** Use a honeypot to divert the traffic from the malicious
**(D)** Update the firewall’s firmware

**Explanation 363.** **Correct Answer: A. Implement a block rule on the web filter for the IP address.** By implementing a block rule specifically for the known malicious IP address on the web filter, any attempt to communicate with that IP would be stopped, effectively preventing further malicious communications.

**Option B is incorrect.** Disabling the network port of the compromised workstation would disconnect the machine from the network, but it wouldn’t specifically prevent communication with the malicious IP if the port were to be re-enabled.