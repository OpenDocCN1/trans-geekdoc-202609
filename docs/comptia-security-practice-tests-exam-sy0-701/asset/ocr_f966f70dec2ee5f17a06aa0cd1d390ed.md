What type of control should Chuck recommend for his company to help prevent future issues like this?

+   - A. Use containment techniques on the impacted phones.
+   - B. Deploy a DLP system.
+   - C. Deploy an MDM system.
+   - D. Isolate the impacted phones.

79. Charles wants to ensure that the forensic work that he is doing cannot be repudiated. How can he validate his attestations and documentation to ensure nonrepudiation?

+   - A. Encrypt all forensic output.
+   - B. Digitally sign the records.
+   - C. Create a MD5 checksum of all images.
+   - D. All of the above.

80. Megan needs to conduct a forensic investigation of a virtual machine (VM) hosted in a VMware environment as part of an incident response effort. What is the best way for her to collect the VM?

+   - A. As a snapshot using the VMware built-in tools
+   - B. By using dd to copy the VM to an external drive
+   - C. By using dd to copy the VM to an internal drive
+   - D. By using a forensic imaging device after removing the server's drives

81. Which of the following groups is not typically part of an incident response team?

+   - A. Law enforcement
+   - B. Security analysts
+   - C. Management
+   - D. Communications staff

82. Bob needs to block Secure Shell (SSH) traffic between two security zones. Which of the following Linux iptables firewall rules will block that traffic from the 10.0.10.0/24 network to the system the rule is running on?

+   - A. `iptables -A INPUT -p tcp --dport 22 -i eth0 -s 10.0.10.0/24 -j DROP`
+   - B. `iptables -D OUTPUT -p udp -dport 21 -i eth0 -s 10.0.10.255 -j DROP`
+   - C. `iptables -A OUTPUT -p udp --dport 22 -i eth0 -s 10.0.10.255 -j BLOCK`
+   - D. `iptables -D INPUT -p udp --dport 21 -I eth0 -s 10.0.10.0/24 -j DROP`