
## FALSE POSITIVES (FALSE ALARMS)

We will look at IDSs in more detail in Chapter 10. Our focus in this chapter is two serious limitations of IDSs. The first is that, like many home and car alarms, IDSs tend to generate far too many false alarms, which, in IDS-speak, are false positives. Like the little boy who cried wolf too many times, IDSs tend to be ignored after exhausted security staff members receive too many false alarms.

It is possible to tune IDSs to reduce the number of false positives to a bearable degree. Many rules make no sense in a particular organization. For instance, if a rule identifies a packet that would be dangerous if sent to a specific type of Unix server, and if an organization has no Unix servers of that type, the rule can be deleted to eliminate the alarms it would generate. However, tuning requires a great deal of labor.

IDSs log all suspicious activity but only create alarms for some suspicious activities. In addition to removing nonsensical rules, tuning may reduce the number of attack signatures that generate alarms. However, while this reduces alarms, it also creates greater urgency for security administrators to read log files regularly to catch attacks that are no longer alarmed.

There are many rules, and each must be considered very carefully. Consequently, tuning is so expensive and resource-draining that few organizations implement it fully.

- **Perspective**
- Growing processing power made stateful packet inspection possible
- Now, growing processing power is making a new firewall filtering method attractive: intrusion prevention systems (IPSs)
- **Intrusion Detection Systems (IDSs)**
- Firewalls drop provable attack packets only
- Intrusion detection systems (IDSs) look for suspicious traffic
- Cannot drop because the packet is merely suspicious
- Sends an alarm message if the attack appears to be serious
- Problem: Too many false positives (false alarms)
- Alarms are ignored or the system is discontinued
- Can reduce false positives by tuning the IDSs
- Eliminate inapplicable rules, such as a Unix rule in an all-Windows company
- Reduce the number of rules allowed to generate alarms
- Most alarms will still be false alarms
- Problem: Heavy processing requirements because of sophisticated filtering
- Deep packet inspection
- Looks at application content and transport and internet headers
- Packet stream analysis
- Looks at patterns across a series of packets
- Often, patterns cannot be seen unless many packets are examined
- **Intrusion Prevention Systems (IPSs)**
- Use IDS filtering mechanisms
- Application-specific integrated circuits (ASICs) provide the needed processing power
- Attack confidence identification spectrum
- Somewhat likely,
- Very likely,
- Provable
- Allowed to stop traffic at the high end of the attack confidence spectrum
- Firm decides which attacks to stop
- **Possible Actions**
- Drop packets
- Risky for suspicious traffic even with high confidence
- Bandwidth limitation for certain types of traffic
- Limit to a certain percentage of all traffic
- Less risky than dropping packets
- Useful when confidence is lower

Figure 6-17 Intrusion Detection Systems (IDSs) and Intrusion Prevention Systems (IPSs) (Study Figure)

## HEAVY PROCESSING REQUIREMENTS

Another problem is that IDS methodologies are highly processing-intensive. This limits the traffic volume that IDSs can filter.

### Deep Packet Inspection.

One reason for IDSs' processing intensiveness is that IDSs do not merely look at a few fields in a packet. They use deep packet inspection, which looks at all fields in the packet, including the IP header, the TCP or UDP header, and the application message. Many attacks cannot be stopped if a firewall only looks at application content or only at internet and transport layer headers.

### Packet Stream Analysis.

IDSs also need to filter packet streams, rather than individual packets. Many attacks are not apparent from individual packets. For instance, a single ICMP echo message is not very diagnostic, but a stream of ICMP echo messages trying different IP addresses is a very strong sign that the company is experiencing a systematic scan. More subtly, application content will be spread over quite a few packets. To analyze application content, an IDS will have to reassemble original application messages—sometimes, a succession of application messages. Examining packet streams instead of just individual packets for dangerous patterns is very processing-intensive.

## Test Your Understanding

- 17. a. Distinguish between firewalls and IDSs.
- b. Why are IDS alarms often a problem?
- c. What is a false positive?
- d. What two types of filtering do IDSs use?
- e. Why is deep packet inspection important?
- f. Why is deep packet inspection processing-intensive?
- g. Why is packet stream analysis important?
- h. Why does packet stream analysis place a heavy load on IDSs?

## Intrusion Prevention Systems

As just noted, intrusion prevention systems grew out of IDS processing. Although intrusion prevention systems (IPSs) use IDS filtering methods, they actually stop some kinds of attacks instead of merely identifying them and generating alarms, as IDSs do. This is why they are called intrusion prevention systems.

> Although IPSs use IDS filtering methods, they actually stop some kinds of attacks instead of merely identifying them and generating alarms, as IDSs do.

## ASICS FOR FASTER PROCESSING

Also as noted earlier, IDS/IPS filtering is very processing-intensive. The most important development leading to IPSs has been the emergence of **application-specific integrated circuits (ASICs)**, which can do filtering in hardware. Hardware filtering is much faster than software filtering, allowing IPSs to be used even when traffic volume is high.

## THE ATTACK IDENTIFICATION CONFIDENCE SPECTRUM

When experienced security professionals who have worked with IDSs hear about IPSs, they usually cringe at first. Given the number of false positives that IDSs generate, the thought of allowing these unreliable filtering mechanisms to actually stop traffic is deeply disturbing.

In practice, however, there always is a spectrum of **attack identification confidence** in intrusion detection. Some attacks, especially DoS attacks, can be identified with a very high degree of confidence. In fact, many border firewalls today *already* identify and stop DoS attacks regardless of their main filtering technology. Other attacks cannot be identified with such high confidence.

## Test Your Understanding

- 18. a. Distinguish between IDSs and IPSs.
- b. Why is the attack identification confidence spectrum important in deciding whether to allow IPSs to stop specific attacks?

## IPS Actions

What do IPSs do when they detect suspicious traffic at the high end of the attack identification confidence spectrum?

### DROPPING PACKETS

In many cases, the IPS will drop attack packets, acting like a traditional firewall. This is dangerous but highly effective.

### LIMITING TRAFFIC

In other cases, the IPS limits suspicious traffic to a certain percentage of the total bandwidth. **Bandwidth limitation** can ensure that even if peer-to-peer file sharing traffic and other illegitimate traffic cannot be identified with precision and dropped, this undesirable traffic at least will not result in an overloaded network.

## Test Your Understanding

- 19. a. What two actions can IPSs take when they identify an attack?
- b. Which can be the most effective?
- c. Which can do the most damage?

## 6.7 Antivirus Filtering and Unified Threat Management

### 6.7 Describe antivirus filtering.

Firewalls normally do not do antivirus filtering. However, firewalls and antivirus filtering servers work together closely. All major firewall vendors have protocols for working with antivirus servers. Figure 6-18 illustrates this dynamic.
