
## 11. Which of the following statements is true with respect to reverse proxy?

A. Reverse proxy cannot be used in conjunction with secured Web sites.

B. Reverse proxy can be used with tunnel mode IPSec VPNs.

C. Reverse proxy can only support SSL tunnels.

D. Reverse proxy caches client requests and archives them for load balancing purposes.

E. The reverse proxy server can act as the endpoint for a TLS tunnel.

## 12. Which of the following is *not* a true statement with regard to port forwarding?

A. Port forwarding services can be found on almost any service or device that supports NAT.

B. Port forwarding is an essential element in the Internet Connection Sharing (ICS) service of Windows.

C. Port forwarding is used in reverse proxy, but only for Web traffic.

D. Port forwarding supports caching, encryption endpoint, and load balancing.

E. Port forwarding is a variation or enhancement of NAT.

## 13. Which of the following is *not* considered a viable option as a bastion host OS?

A. UNIX

B. Linux

C. Android

D. Mac OS

E. Windows 7

## 14. You are selecting a new appliance firewall for deployment in the company network. You are concerned with OS flaws and exploits appearing not only on your hosts but also on the firewall. To minimize that risk, what bastion host OS should you choose?

A. Cisco IOS

B. Windows 7

C. UNIX

D. Mac OS

E. Linux

## 15. What is the most important aspect or feature of a bastion host OS?

A. Leveraging existing OS administrative knowledge

B. Ease of use

C. Remote administration

D. Resistance to attacks and compromise attempts

E. Support of a wide range of services

## 16. What is always the most important element within a firewall rule set?

A. Using specific addresses instead of ANY

B. Listing Deny exceptions after Allow exceptions

C. Listing inbound exceptions before outbound exceptions

D. Having a final rule of default-deny

E. Blocking every known malicious port

## 17. Which of the following examples of complete firewall rule sets is the most valid?

A.

![Image](images/pg273-1.jpg)

B.

![Image](images/pg273-2.jpg)

C.

![Image](images/pg273-3.jpg)

D.

![Image](images/pg273-4.jpg)

E.

![Image](images/pg273-5.jpg)

## 18. Which of the following guidelines is most important?

A. Include all specific denials for known malicious remote-control tools after explicit Allow rules.

B. Include every possible address and port in a rule within the set to ensure an explicit callout exists for every type of communication.

C. There should be more inbound rules than outbound rules.

D. Place explicit Deny rules for individual systems before explicit Allow rules for ranges that include those individual systems.

E. Place universal Allow rules before universal Deny rules.

## 19. When considering the security response triggered by a firewall detecting unwanted traffic, what is the main factor in choosing between a response that protects confidentiality and integrity and a response that protects availability?

A. Traffic load

B. Number of external clients

C. Port in use

D. Business mission and goals

E. Whether the breach takes place during non-business hours

## 20. When security mechanisms and business communications are at odds, what is the best and most secure response?

A. Disable security to allow the business communication.

B. Modify the security policy to protect the business communication.

C. Disable both security and the offending business communication.

D. Disable business communication to maintain security.

E. Do nothing.

# Chapter 9: Firewall Management and Security

**Firewall management** is about focusing on the essential security goals of the environment and making sure the deployed firewalls assist in fulfilling those goals. Following general best practices with care and due diligence will help ensure compliance. Realize that while a firewall is very important, even essential, firewalls are not the totality of security; you’ll need other security safeguards to create a complete solution.

When selecting a firewall, focus on the purpose and needs of your organization. Find a product that meets the real needs of your organization’s network environment, not the most popular or cheapest solution. Consider whether building your own firewall device rather than purchasing a ready-made appliance makes better sense.

But even with an appropriate, properly configured firewall, ongoing security concerns will invariably arise. Plan on the inevitable attacks, exploits, and threats to the security provided by a firewall. Hackers might attempt to use tunneling or virtual private network (VPN) services as a mechanism to bypass firewall filters. Be aware of these issues and be prepared to deal with them. Have an incident response plan in place.

Firewall management also includes testing, monitoring, and troubleshooting. Many excellent tools can help simplify or automate these processes. But even the best tools require solid information and a working knowledge of your environment. Detailed implementation plans can also be a significant benefit to maintaining reliable security.

## Chapter 9 Topics

This chapter covers the following topics and concepts:

- What best practices for firewall management are
- What some security measures in addition to a firewall are
- How to select the right firewall for your needs
- What the difference is between buying and building a firewall
- How to mitigate firewall threats and exploits
- What the concerns related to tunneling through or across a firewall are
- How to test a firewall’s security
- What some important tools are for managing and monitoring a firewall
- How to troubleshoot firewalls
- What the procedure is for proper firewall implementation
- How to respond to incidents

## Chapter 9 Goals

When you complete this chapter, you will be able to:

- Describe firewall management best practices
- Select the best firewall for a given network scenario
- Demonstrate the use of tools for managing and monitoring a firewall
- Troubleshoot common firewall problems
- Write a firewall installation plan

## Best Practices for Firewall Management

Firewall management best practices are recommendations, guidelines, or standard operating procedures for obtaining reliable firewall security on a real-world budget. Best practices are usually not specific recommendations for products or tools. Rather, they are recommendations for philosophies, stances, or concepts on how to proceed. The following items are suggested best practices. These might not apply to every environment, although you should consider each and adapt or adopt when appropriate.

A **written firewall policy** establishes a documentation trail that everyone in the organization can read, consider, and follow. To write a firewall policy, learn about and thoroughly examine every communication, transaction, and service within, across, and through the IT infrastructure. You can write a comprehensive and effective firewall policy only when you know and understand your operating environment.

> **NOTE**
>
> The foundation of every firewall implementation is to *have a plan*. There is no substitute for a written firewall policy. Any other method, process, or procedure for configuring, using, and managing a firewall will fail. Only a written firewall policy can guide you toward a successful and reliable firewall deployment.
