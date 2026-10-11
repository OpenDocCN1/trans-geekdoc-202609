
The primary focus of firewalls historically has been on assets deployed to offer protection to a collection of systems on a network. While the importance of firewalls to achieve network segments persists, firewalls deployed on individual endpoints offer substantial and additional benefits. The most basic configuration performed on any firewall involves defining the trust levels associated with various networks. Historically, this meant trusting internal assets and treating all non-internal assets to be untrusted. Unfortunately, adversaries' increasing use of Lateral Movement (TA0008 within the MITRE ATT&CK® Enterprise Matrix [\[6\]](#Ch008_361-457_B9780443187346000064_2.xhtml#bb0035)) diminishes the efficacy of equating internal as trusted.

Thankfully, endpoint firewalls offer us a technically simple way to combat this overly generous internal zone of trust. Endpoint firewalls, sometimes referred to as desktop or host-based firewalls, operate as a piece of software installed on a single system. Only the system on which the endpoint firewall is installed needs to be implicitly trusted, which can allow greatly increased protection and detection capabilities in the face of an adversary launching attacks from the vantage point of a compromised internal asset.

## Fundamental Firewall Designs

Firewall design has evolved over the years, from simple and flat designs such as dual-homed host and screened host, to layered designs such as the screened subnet. While these terms are no longer commonly used, and flat designs have faded from use, it is important to understand fundamental firewall design. This evolution has incorporated network defense-in-depth, leading to the use of DMZ and more secure networks.

### Bastion Hosts

A `bastion host` is any host placed on the Internet that is not protected by another device (such as a firewall). Bastion hosts must protect themselves, and be hardened to withstand attack. Bastion hosts usually provide a specific service, and all other services should be disabled.

### Dual-Homed Host

A `dual-homed host` has two network interfaces: one connected to a trusted network and the other connected to an untrusted network, such as the Internet. The dual-homed host does not route: a user wishing to access the trusted network from the Internet, as shown in [Fig. 8.8](#Ch008_361-457_B9780443187346000064_1.xhtml#f0045), would log into the dual-homed host first, and then access the trusted network from there. This design was more common before the advent of modern firewalls in the 1990s, and is still sometimes used to access legacy networks.

![Fig. 8.8 Dual-homed host.](images/B9780443187346000064/f08-08-9780443187346.jpg)

[Fig. 8.8](#Ch008_361-457_B9780443187346000064_1.xhtml#B-f0045) Dual-homed host.

### Screened Host Architecture

`Screened host architecture` is an older flat network design using one router to filter external traffic to and from a `bastion host` via an access control list (ACL). The bastion host can reach other internal resources, but the router ACL forbids direct internal/external connectivity, as shown in [Fig. 8.9](#Ch008_361-457_B9780443187346000064_1.xhtml#f0050).

![Fig. 8.9 Screened host network.](images/B9780443187346000064/f08-09-9780443187346.jpg)

[Fig. 8.9](#Ch008_361-457_B9780443187346000064_1.xhtml#B-f0050) Screened host network.

The difference between dual-homed host and screened host design is that screened host uses a screening router, which filters Internet traffic to other internal systems. Screened host network design does not employ network defense-in-depth: a failure of the bastion host puts the entire trusted network at risk. Screened subnet architecture evolved as a result, using network defense-in-depth via the use of DMZ networks.

### DMZ Networks and Screened Subnet Architecture

A `DMZ` is a `Demilitarized Zone` network; the name is based on real-world military DMZ, such as the DMZ between North Korea and South Korea. A DMZ is a dangerous "no-man's land": this is true for both military and network DMZ.

Any server that receives traffic from an untrusted source such as the Internet is at risk of being compromised. We use defense-in-depth mitigation strategies to lower this risk, including patching, server hardening, and NIDS, but some risk always remains.

Network servers that receive traffic from untrusted networks such as the Internet should be placed on DMZ networks for this reason. A DMZ is designed with the assumption that any DMZ host may be compromised: the DMZ is designed to contain the compromise, and prevent it from extending into internal trusted networks. Any host on a DMZ should be hardened. Hardening should consider attacks from untrusted networks, as well as attacks from compromised DMZ hosts.

A "classic" DMZ uses two firewalls, as shown in [Fig. 8.10](#Ch008_361-457_B9780443187346000064_1.xhtml#f0055). This is called `screened subnet` dual firewall design: two firewalls screen the DMZ subnet.

![Fig. 8.10 Screened subnet dual firewall DMZ design.](images/B9780443187346000064/f08-10-9780443187346.jpg)

[Fig. 8.10](#Ch008_361-457_B9780443187346000064_1.xhtml#B-f0055) Screened subnet dual firewall DMZ design.

A single-firewall DMZ uses one firewall, as shown in [Fig. 8.11](#Ch008_361-457_B9780443187346000064_1.xhtml#f0060). This is sometimes called a "three-legged" DMZ.

![Fig. 8.11 Single firewall DMZ design.](images/B9780443187346000064/f08-11-9780443187346.jpg)

[Fig. 8.11](#Ch008_361-457_B9780443187346000064_1.xhtml#B-f0060) Single firewall DMZ design.

The single firewall design requires a firewall that can filter traffic on all interfaces: untrusted, trusted, and DMZ. Dual firewall designs are more complex, but considered more secure. In the event of compromise due to firewall failure, a dual firewall DMZ requires two firewall failures before the trusted network is exposed. Single firewall design requires one failure.

> **Note**
>
> The term "DMZ" alone implies a dual firewall DMZ.

## Web Application Firewall (WAF)

Not simply another type or generation of general-purpose network firewall, the Web Application Firewall (WAF) serves as an entirely separate and distinct control. Given the name, it should come as little surprise that the sole focus of the WAF is to improve an organization's security posture with respect to web applications, most commonly the organization's custom-developed web applications. The WAF will be deployed such that it can scrutinize application layer traffic to an organization-controlled web application. Firewall in the name makes clear that WAFs are typically intended for use as a preventive control. However, they can also provide substantial detective benefits even if configured not to actually block anything at all.

Organizations most commonly employ WAFs for public-facing applications, but they can also be used to bolster the security of internal-facing web applications. WAFs can be deployed in various ways including cloud-hosted, on-premises as a reverse proxy in front of web servers hosting the applications, or even as services running on web servers hosting the target application. These layer 7 controls must simply be deployed inline, so that the web application traffic flows through the WAF such that it can block overtly malicious traffic or alert on suspicious activity.

## Sandboxing

Signature-based approaches to prevention of malicious content have a major inherent weakness; the signatures fundamentally depend on prior knowledge for their creation. If your organization were the first to encounter a novel exploit or technique, signature-based approaches will necessarily fall short. Sandboxing attempts to help fill this gap by focusing on identification of suspicious behaviors rather than primarily depending on signatures.
