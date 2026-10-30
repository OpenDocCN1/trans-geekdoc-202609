# # Secure Network Administration

In this chapter, you will

+   - Apply secure network administration principles
+   - Learn about rule-based management systems, including firewalls and switches
+   - Examine network protection mechanisms

This chapter examines network security mechanisms, including network devices such as routers, switches, firewalls, and security appliances. Discussion of security mechanisms such as access control lists, port security, 802.1x, flood guards, loop protection, and network separation is included as well because they form the foundational methods used in secure network administration.

# ## Secure Network Administration Principles

Networks are composed of a combination of hardware and software, operated under policies and procedures that define desired operating conditions. The principles of secure network administration include properly configuring hardware and software and properly performing operations and maintenance. All of these elements need to be done with security in mind, from planning, to design, to operation.

# ### Rule-based Management

Rule-based management is a common methodology for configuring systems. Desired operational states are defined in such manner that they can be represented as rules, and a control enforces the rules in operation. This methodology is used for firewalls, proxies, switches, routers, anti-malware, IDS/IPS, and more. As each packet is presented to the control device, the set of rules is applied and interpreted. This is an efficient manner of translating policy objectives into operational use.

# ### Firewall Rules

Firewalls operate by enforcing a set of rules on the traffic attempting to pass. This set of rules, the firewall ruleset, is a mirror of the policy constraints at a particular point in