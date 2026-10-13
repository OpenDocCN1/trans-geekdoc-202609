
# Best Practices for Network Security Management

## Chapter 14

### Chapter 14 Topics

This chapter covers the following topics and concepts:

*   Essentials of network security management
*   Important network security management tools
*   Techniques for limiting network access and implementing encryption
*   Important elements of physical security
*   Techniques for preventing and deterring incidents, such as containment, honeypots, antivirus, and backup and recovery
*   What is included in incident response
*   Differences among fail-secure, fail-open, and fail-close options
*   The basics of security assessment
*   Why change management is important
*   What is included in compliance auditing
*   The basics of network security troubleshooting

### Chapter 14 Goals

When you complete this chapter, you will be able to:

*   List examples of network security best practices
*   Describe the importance of physical security
*   Compose a procedure for incident response
*   Enumerate key components of an effective network security installation
*   Describe the methods of network security assessment

### Essentials of Network Security Management

Security is fragile. Hackers need to discover only a single flaw in your defenses to mount an attack. Changes to the infrastructure, whether physical or logical, could open new holes in the network. Additionally, users and personnel may intentionally or accidentally breach security.

Network security management best practices are recommendations, guidelines, or standard operating procedures for obtaining reasonable security on a real-world budget. Best practices are usually not specific recommendations for products or tools; instead, these are recommendations for philosophies, stances, or concepts to use.

Focus on the core security services when designing security: confidentiality, integrity, and availability. Failure to properly and adequately address these essential security services will result in damage, data loss, and downtime. Confidentiality is the prevention of unauthorized access while supporting authorized access. Integrity is the protection against unauthorized modifications. Availability is the assurance that resources are accessible in a timely manner.

Consider designing security, especially physical security, around three central functions: deterrence, detection, and delay. **Deterrence** is the use of security to convince the potential attacker that the efforts to compromise a system are not worth it. The attack may be perceived as too hard or too complex, the attempt too easy to detect, and the consequences too severe. **Detection** is to watch for the attempts at breaching security so as to respond promptly. Delay is to slow down the attack so that even successful breaches give the defenders time to respond in order to apprehend the attacker or prevent further intrusion.

Another common trio of parameters for security design and implementation is prevention, detection, and response. **Prevention** is the use of safeguards to thwart exploitation or compromise. It is usually more efficient, easier, and cost effective to prevent intrusions and breaches than to react to them. Immediate detection of attempted and successful security breaches is important. The longer the time span between a malicious action and an authoritative response, the greater the likelihood the perpetrator will get away without consequence. **Response** means being prepared to contain damage, restrict further compromise, and effect repairs to return the system to normal.

The following collection of network security management best practices should serve as a starting point for the development of your effective security endeavors:

*   **Do not rely upon single or individual defenses**—Attempt to interlock and layer defenses. Implement defense in depth or a multiple-layered defense wherever possible (**Figure 14-1**). By following a defense-in-depth design concept, you will protect each asset with numerous safeguards. As one defense tool interlocks with another, there is overlap—like medieval armor plates—which improves the overall security. The strengths and benefits of one countermeasure can supplement or compensate for the weaknesses and limitations of another. Even if the layered defenses are weak, this strategy can still provide enough of a delay for malicious activity to be noticed and stopped, or it may act as a deterrent so a hacker moves to exploit a less time-consuming target.

*   **Know the limitations of security products**—Each security mechanism addresses a single or small set of issues within a specific context. The presence of security in one location does not cause a magical blanket of security to exist in other locations. Be sure specific and relevant security solutions are in place where necessary. For example, use of Internet Protocol Security (`IPSec`) for network encryption does not imply that data stored on clients is encrypted.

*   **Assume programs are inherently insecure**—Security is not often a priority or a requirement in programming. When possible, use secure programming quality assurance.

## Review Questions

### 4. Use anti-malware scanning

### 5. Part of troubleshooting is identifying open ports. Which of the following tools aids in scanning if ports are open or closed?

1.  `Fport`
2.  `Netstat`
3.  `Nmap`
4.  `Wireshark`

### 6. Which of the following tools is primarily used for network vulnerability assessments?

1.  `Fport`
2.  `Nessus`
3.  `Netcat`
4.  `Snort`

### 7. Which of the following is *not* a firewall management best practice?

1.  Develop a checklist
2.  Build a written policy
3.  Secure physical access
4.  Use vendor default configuration

### 8. Which of the following *is* a firewall management best practice?

1.  Install the first generation or first release of a firewall product.
2.  Upon firewall installation, install available updates from the vendor.
3.  Install pre-release patches on production firewalls as soon as they are available.
4.  Because firewall vendors test code for quality assurance, an administrator does not need to duplicate testing efforts before installing code on a firewall.

### 9. Which of the following is the best, first tool to use when troubleshooting firewalls?

1.  Crimping tools
2.  Fuzzing tools
3.  Information
4.  Source code

### 10. When a firewall breach is detected, what is the first step that should be taken?

1.  Enable firewall alerts
2.  Document the incident
3.  Disable the firewall
4.  Install a new firewall
