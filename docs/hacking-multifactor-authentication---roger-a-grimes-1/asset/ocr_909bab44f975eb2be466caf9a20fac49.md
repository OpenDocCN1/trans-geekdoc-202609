# 378 Hacking Multifactor Authentication

namespaces are still in use today, including Abstract Syntax Notation One (ASN.1), Active Directory (AD), and Lightweight Directory Access Protocol (LDAP). Any filesystem by an operating system can also be thought of as a namespace. Other naming conventions, services, and protocols that could be constructed as a namespace of sorts NetBIOS, Internet Protocol (IP) addresses, and AppleTalk, among others. The commonality is that the identities and other components named in the namespace are used by other participants in the namespace to locate each other. DNS is the most popular namespace and the one familiar to people. Many toddlers can rattle off their DNS addresses before they are three years old. Examples of DNS addresses are rogerg@knowledge4.com, www.knowledge4.com, and www.knowledge4.com/resources.

In the entire world, Microsoft's Active Directory namespace is popular. An example (Distinguished Name) AD name like CN=Roger, OU=Users, US=PRDept, DC=knowledge4,DC=com. Namespaces can hold only objects, but also assertions, and attributes of objects. Namespaces can be attacked to circumvent MFA solutions. I covered a related attack in Chapter 10, "Subject Hijack Attacks." That one involved Microsoft's AD mandates, and revealed one of the few attacks in this book, for as I know, were not used in a single real-world attack.

Attacks against DNS are the polar opposite. Attacks against DNS occurs thousands of times a day and are routinely used to bypass authentication defenses. There have been some other types of namespaces. I'll cover a handful of them in this chapter.

Someone using MFA would likely not be able to prevent the vast majority of namespace attacks. This should not be surprising. If I can hack a dependency, I can often hack or bypass the thing that relies on the dependency. It's fairly difficult to stop an attack against a namespace dependency, and I'll cover some possible defenses later in this chapter.

# DNS

We'll cover a few types of namespaces and attacks in this chapter, but certainly attacks against DNS are the most important and popular. DNS (along IP addresses) is the backbone of our Internet, and the majority of organizational networks use it to work.

DNS converts the "common names" you type in or click, such as www.google.com, to officially registered IP (version 4 or 6) host addresses (e.g., 104.117.113.180, 16A7:F1ED:10B2:51:8, etc.) by Internet routers before the senses to transmit intended communications. Each computer or device accessible directly from or to the Internet must have a unique (fully qualified) DNS name and associated (public) IP address. the same DNS name or IP address.

> NOTE Directly contactable Internet devices must have "public" IP addresses, but one private, non-unique, addressable IP devices using a protocol known as Network Address Translation (NAT). But public IP addresses can be routed to and from directly on the Internet. There are millions of private IP addresses that anyone can use on their private networks as long as they don't try to connect them directly to the Internet.