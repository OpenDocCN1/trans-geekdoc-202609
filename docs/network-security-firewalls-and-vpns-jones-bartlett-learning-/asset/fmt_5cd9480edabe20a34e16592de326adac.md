
In [Table 8-1](#15_chapter08.xhtml#tab8-1), an example of this issue is the e-mail protocol `SMTP` operating over port `25`. By defining an allow-exception rule, you could create a loophole that threatens the internal communication on this same port. Reduce or eliminate this risk by using a very specific rule or by adding an additional Deny exception.

A very specific rule in this example would allow external communication over port `25` only if it originated from the internal e-mail server at `192.168.42.115`. With this rule defined, if any other internal host attempted an external `SMTP` communication on port `25`, it would not be allowed because the IP address would not match this specific rule. The communication would instead be blocked by the default deny.

**TABLE 8-1** A partial list of communications occurring on a network.

![Image](images/pg249.jpg)

If an allow-exception rule for external communications also applies to internal communications, you can add a specific deny-exception rule just prior to the Allow rule. The Deny exception can specifically block internal communications from crossing the network border, but still allow the subsequent Allow exception to grant access to the valid transactions.

After you complete a thorough inventory of network communications, you should determine which communications are mission-critical, important, optional, for personal recreational use, or actually malicious. Block any traffic you deem malicious or just unwanted, whether through an explicit Deny or via the catchall default deny.

Evaluate all other forms or types of traffic against several factors, including policy. If it’s not in support of the business, is it really needed? Are communications for personal entertainment or nonbusiness functions permitted by policy or considered a waste of resources? Are any communications duplicated or redundant? Is this a waste of resources, an expansion of the attack surface, a valid redundancy, or avoidance of a single point of failure? Are any of the communications no longer necessary? If so, should you disable or remove them?

Base your evaluation of the many other possible questions or issues on your organization’s policy statements, including mission and goals. Take the time to understand the communication needs of your network, then design the filtering rule set accordingly. Remember that the firewall is often the front sentry or the first line of defense against malicious communications originating from outside networks. Leaning toward caution and locking things down is a more effective security stance than leaving communications open and hoping detection mechanisms will notice malicious events.

### Traffic Inventory

A common, and free, network protocol analyzer (or sniffer) for doing a traffic inventory is `Wireshark` (*[www.wireshark.org](http://www.wireshark.org)*). `Wireshark` can be used in the absence of a firewall, with a firewall set to allow all traffic, or even in the presence of a firewall to inventory all traffic on the network. Traffic can then be partitioned into traffic that needs to cross the firewall and traffic that should not cross the firewall. Use of a sniffer tool in general, or `Wireshark` specifically, for traffic inventory is done to highlight all traffic and make sure that the firewall rules have a better chance of being accurate. During the traffic inventory, you can uncover a lot of previously hidden information about the network. You can find out which applications and users are the top consumers of bandwidth. You can find out which protocols are actually in use on the network. And you can surface malicious uses that you haven’t known about before. Some of the more advanced firewalls also have this functionality built-in.

While some exceptions to these suggestions will arise from your organization’s business model or strategies, the following items are commonly considered communications to block in most, if not all, circumstances:

![Image](images/bull1.jpg) All Internet control message protocol (`ICMP`) traffic originating from the Internet

![Image](images/bull1.jpg) Any traffic directed specifically to the firewall

![Image](images/bull1.jpg) Any traffic to known closed ports

![Image](images/bull1.jpg) Any traffic to known ports of known malware, such as `31337`, used by Back Orifice

![Image](images/bull1.jpg) Inbound Transmission Control Protocol (`TCP`) `53` to block external domain name system (`DNS`) zone transfer requests

![Image](images/bull1.jpg) Inbound User Datagram Protocol (`UDP`) `53` to block external `DNS` user queries

![Image](images/bull1.jpg) Any traffic from IP addresses on a blacklist

![Image](images/bull1.jpg) Any traffic from internal IP addresses that are not assigned

As an organization manages its security over time, especially as it reacts to intrusion attempts, experiences scanning, and becomes the target of hacking and flooding, it must create additional communication filtering rules to respond to real-world conditions. Security does not stand still. Hacker attacks are constantly changing. Thus, the filtering rules that work well today may be insufficient in the near future.

Networks can be very large and very complex. Be fully aware of the communications taking place across your network to know what to allow and what to block. In addition to this knowledge, having established a security strategy through a written security policy will direct and guide the deployment of firewall rules, as well as other aspects of your security infrastructure.

### Common Security Strategies for Firewall Deployments

A security strategy is a guideline, philosophy, or approach to using security for firewalls, as well as the entire organizational security infrastructure. Many different strategies are available. Some organizations focus on a single strategy, while others combine several strategies into a custom policy.

#### Security Through Obscurity

Security through obscurity is the idea of gaining protection by using abnormal configurations. This is both a positive security action and a poor one. It simply depends on the type of obscurity involved. A poor choice for security through obscurity would be to use alternative configurations for standard products.

With a network environment based on standard products, whether operating systems, network services, or security solution, just modifying basic configuration settings does not actually provide true security. For example, a service typically operating on one port that’s reconfigured to use a different port is not good security. Also, changing names, addresses, network size, subnetting, bandwidth consumption, or even spoofing banners, headers, or identity does not provide true security but may provide some protection against elementary attacks.

Some common mistaken examples of obscurity-based security include:

![Image](images/bull1.jpg) Hiding your front door key under a rock in a flower bed

![Image](images/bull1.jpg) Connecting to the Internet with the assumption that your system is one in 300 million and therefore won’t be noticed

![Image](images/bull1.jpg) Hiding money in a mattress

![Image](images/bull1.jpg) Keeping an encryption algorithm secret

![Image](images/bull1.jpg) Hiding your car keys behind your bumper while at the park or beach

![Image](images/bull1.jpg) Changing the default service port of a network service

![Image](images/bull1.jpg) Hiding your financial records among the audio files on your MP3 player

All attempts to provide network security based on hide-and-seek can be overcome or bypassed with basic network scanning techniques. When a hacker can discover or breach a host, service, or network just by looking hard enough, no real security exists. Hiding might work for keeping colored eggs and candy secure, but a security solution employed by bunnies has no place in a modern IT environment.
