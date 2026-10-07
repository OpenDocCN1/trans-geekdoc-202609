Option D is incorrect. Insecure Direct Object Reference (IDOR) vulnerabilities occur when an application allows access to objects based on user-supplied input. While the scenario involves accessing a file, it is the act of elevating privileges that is the primary concern.

Question 419. A school wants to prevent its students from accessing inappropriate websites during class hours. The IT department decides to implement a solution that blocks requests to specific domain names associated with inappropriate content. Which of the following security solutions would best address this need?

+   (A) Firewall filtering based on IP addresses
(B) Intrusion Detection System monitoring
(C) Virtual Private Network (VPN) enforcement
(D) DNS filtering with a blacklist

Explanation 419. Correct Answer: D. DNS filtering with a blacklist. DNS filtering is a technique that can be used to prevent users from accessing specific websites by blocking requests to certain domain names. A blacklist can be created to list the domain names associated with inappropriate content, and when users try to access these sites, the DNS filter will not resolve the domain name, thereby preventing access.

Option A is incorrect. While firewalls can block traffic based on IP addresses, this method is not as effective for blocking specific domain names, especially when a domain can have multiple IP addresses or if the IPs can change.