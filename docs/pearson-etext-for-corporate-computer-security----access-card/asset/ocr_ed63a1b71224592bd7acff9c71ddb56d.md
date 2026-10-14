# Chapter 6

# Firewalls

# Learning Objectives

# Chapter Outline

*After studying this chapter, you should be able to:*

+   6.1  Define firewalls in general (basic operation, architecture, and the problem of overload).
+   6.2  Describe how static packet filtering works.
+   6.3  Explain stateful packet inspection (SPI) for main border firewalls.
+   6.4  Describe how network address translation (NAT) works.
+   6.5  Explain application proxy firewalls and content filtering in SPI firewalls.
+   6.6  Distinguish between intrusion detection systems (IDSs) and intrusion prevention systems (IPSs).
+   6.7  Describe antivirus filtering.
+   6.8  Define firewall architectures.
+   6.9  Describe firewall management (defining policies, implementing policies, reading log files).
+   6.10  Describe some difficult problems associated with firewalls.

+   6.1  Introduction
+   6.2  Static Packet Filtering
+   6.3  Stateful Packet Inspection
+   6.4  Network Address Translation
+   6.5  Application Proxy Firewalls and Content Filtering
+   6.6  Intrusion Detection Systems and Intrusion Prevention Systems
+   6.7  Antivirus Filtering and Unified Threat Management
+   6.8  Firewall Architectures
+   6.9  Firewall Management
+   6.10  Firewall Filtering Problems
+   6.11  Conclusion

# 6.1 Introduction

**6.1**  **Define firewalls in general (basic operation, architecture, and the problem of overload).**

# Basic Firewall Operation

Figure 6-1 shows that a firewall examines each packet passing through it. If the packet is a **provable attack packet**, the firewall drops the packet. If the packet is *not* a provable attack packet, the firewall passes the packet on to its destination. In firewalls, this is called a **pass/deny decision**.

Note that a firewall passes all packets that are not provable attack packets. This means that it will pass any true attack packet that is not a *provable* attack packet. This will allow attack packets to get through to their targets. Consequently, it is