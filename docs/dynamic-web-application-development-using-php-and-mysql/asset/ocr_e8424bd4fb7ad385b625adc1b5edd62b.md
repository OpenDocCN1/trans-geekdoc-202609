IP addresses are expressed as four sets of dotted decimal numbers using the format nnn.nnn.nnn.nnn. Each of these numbers falls in the range 0–255, for example, 127.0.0.1.

| NOTE | IPv6 addresses are written as eight 4-digit hexadecimal numbers separated by colons. |

Given an IP address, one machine can connect to another as if they were on the same physical network. Some machines have fixed IP addresses, while others are temporarily allocated an IP address from a pool when they connect, a technique known as DHCP (Dynamic Host Configuration Protocol.) This pooling of IP addresses is more efficient in terms of being able to reuse the same address for different machines at different times. It also reduces the administration required to ensure that each machine has an appropriate address, particularly for systems that have to give Internet access to very large numbers of computers, such as commercial ISPs.

# Domain names

Most computers that host web sites use domain names rather than actual IP addresses. This means that users can, for example, visit www.w3.org rather than use the actual IP address of the World Wide Web Consortium site. The Domain Name System (DNS) enables a domain name to be converted into a valid IP address. Resolver programs query name servers for IP addresses and enable clients to be routed to the actual host machine. The DNS consists of a number of dedicated servers (a distributed database) that maintain naming information for different zones. A zone is a set of related domain names, '.com', '.org', etc. that appear at the same level of the DNS, which has a tree structure (see Figure 1.2).

Specific domains appear in a particular zone, for example the W3C domain is within the 'org' zone (w3.org). The highest level zone is known as the 'root domain' and under this comes the zone that encompasses all the top-level domains, including the country code domains. For each country, there is a zone that contains the various types of domain within that country, using zones such as 'co' for companies and 'ac' for academic institutions. Because of this tree structure, with layers of zones each managed separately, several different name servers may be involved in resolving a single domain name request. Domain names are controlled by the Internet Assigned Numbers Authority (IANA), which is administered by the Internet Corporation for Assigned Names and Numbers (ICANN). The number of domain types made available by these organisations has increased steadily

FIGURE 1.2 The DNS tree structure with some of the Internet zones and domains

![](bbox=[0.22, 0.9, 0.88, 0.95])