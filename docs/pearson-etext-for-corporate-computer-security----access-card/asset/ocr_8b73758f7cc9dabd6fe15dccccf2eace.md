# Figure 4-5 Fixing and Updating Bots

![](bbox=[0.3, 0.095, 0.89, 0.41])

2018, researchers estimate that it costs about $13.50 to buy a single bot. But leasing an entire botnet for a short period of time can be more cost-effective. A bot net costs about $20 to $50 per hour to rent depending on the size of the attack required.⁸

Handlers Managing thousands of bots can be difficult. Handlers are an additional layer of compromised hosts that are used to manage large groups of bots (Figure 4-6) (Step 1). Handlers, sometimes known as command-and-control servers, make coordinating an attack easier and less conspicuous. The additional layer also makes it difficult to track an attack back to the original attacker (Step 2).

Figure 4-6 also shows that handlers can direct bots to send a variety of different packets depending on the service being targeted. Attackers can target Internet, transport, and well-known application layer services including HTTP, IRC (chat), SMTP (spam), FTP, DNS, and so on (Step 3). Victims can even be overwhelmed with a combination of different types of packets (Step 4).

# Test Your Understanding

+   3. a. What is the difference between a direct and indirect DoS attack?
+      b. What is backscatter?
+      c. What types of packets can be sent as part of a DoS attack?
+      d. Describe a SYN flood.
+      e. How does a DDoS attack work?
+      f. What does a handler do?

⁸ Denis Makrushin, “The Cost of Launching a DDoS Attack,” Kaspersky Lab, March 23, 2017. https://securelist.com/the-cost-of-launching-a-ddos-attack/77784.