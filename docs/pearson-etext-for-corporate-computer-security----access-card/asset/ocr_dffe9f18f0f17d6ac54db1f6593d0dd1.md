# Figure 6-4 Main Border Firewall and Screening Router That Uses Static Packet Filtering

![](bbox=[0.3, 0.11, 0.89, 0.27])

+   - Most importantly, many main border firewalls use static packet filtering as a secondary filtering mechanism because of its ability to stop some specific attacks that are more difficult and therefore more expensive to stop in other ways.
+   - In addition, Figure 6-4 shows that some firms turn their border routers into static packet filtering firewalls by adding software (and sometimes RAM). These filtering routers can stop many high-volume but simple incoming attacks in order to lighten the load on the main border firewall. These filtering routers can also ensure that outgoing ICMP echo reply messages and other probe responses do not get out to people probing the network.

# Test Your Understanding

+   4. a. What are the two limitations of static packet filtering? Explain why each limitation is bad.
+      b. For what two reasons do companies not use static packet filtering as the main filtering mechanism in border firewalls today?
+      c. In what two secondary ways do corporations sometimes use static packet filtering?

# 6.3 Stateful Packet Inspection

6.3 Explain stateful packet inspection (SPI) for main border firewalls.

# Basic Operation

We have just seen that static packet filtering is not used as a main border firewall filtering mechanism. By contrast, nearly all corporate border firewalls today use the stateful packet inspection (SPI) filtering method. Consequently, we will look at SPI filtering in the most depth in this chapter.

CONNECTIONS SPI focuses on connections, which are persistent conversations between different programs on different computers. To give an analogy, a connection is like a telephone call between two people.

STATES When you call someone on the telephone, there are implicit rules of conduct that should be observed in different periods of the conversation. When a called party answers, it is polite to ask if they are free to talk. At the end of the conversation, it is rude to merely hang up. During the main phase of the conversation, it is rude to monopolize the conversation.