Hypertext Markup Language (HTML) documents is to display a link in text where the actual target address is different from what is displayed. Another way to achieve this is the use of non-ASCII character sets (for instance, Unicode—ISO/IEC 10646:2012— characters) that closely resemble ASCII (i.e., Latin) characters to the user.58 This may become a popular technique with the popularization of internationalized domain names.

# Information Disclosure

Smaller corporate networks do not split naming zones (i.e., names of hosts that are accessible only from an intranet are visible from the Internet). Although knowing a server name will not enable anyone to access it, this knowledge can aid and facilitate preparation of a planned attack as it provides an attacker with valuable information on existing hosts (at least with regard to servers), network structure, and, for instance, details such as organizational structure or server operating systems (if the OS is part of the host name, etc.).

An organization should therefore operate split DNS zones wherever possible and refrain from using telling naming conventions for their machines. In addition, a domain registrar’s database of administrative and billing domain contacts (Whois database) can be an attractive target for information and email harvesting.

# Namespace-Related Risks

Besides the technical risks described, a number of other risks exist that, although not strictly security related, can lead to equivalent exposure.

# Session Hijack

Session hijacking is the act of unauthorized insertion of packets into a data stream. It is normally based on sequence number attacks, where sequence numbers are either guessed or intercepted. Different types of session hijacking exist:

+   - **IP Spoofing** — Based on a TCP sequence number attack, the attacker would insert packets with a faked sender IP address and a guessed sequence number into the stream. The attacker would not be able to see the response to any commands inserted.
+   - **Man-in-the-Middle Attack** — The attacker would sniff or intercept packets, removing legitimate packets from the data stream and replacing them with his own. In fact, both sides of a communication would then communicate with the attacker instead of each other.