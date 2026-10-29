# Proxy Servers

A proxy server is an application that can serve as an intermediary for connecting with other computers

# Why Attackers Use Proxy Servers?

+   1. To hide the actual source of a scan and evade certain IDS/firewall restrictions
+   2. To mask the actual source of an attack by impersonating the fake source address of the proxy
+   3. To remotely access intranets and other website resources that are normally restricted
+   4. To interrupt all requests sent by a user and transmit them to a third destination such that victims can only identify the proxy server address
+   5. To chain multiple proxy servers to avoid detection

Note: A search in Google will list thousands of free proxy servers

# Proxy Servers

A proxy server is an application that can serve as an intermediary for connecting with other computers.

A proxy server is used:

+   - As a firewall and to protect the local network from external attacks.
+   - As an IP address multiplexer that allows several computers to connect to the Internet when you have only one IP address (NAT/PAT).
+   - To anonymize web surfing (to some extent).
+   - To extract unwanted content, such as ads or “unsuitable” material (using specialized proxy servers).
+   - To provide some protection against hacking attacks.
+   - To save bandwidth.

# How does a proxy server work?

Initially, when you use a proxy to request a particular web page on an actual server, the proxy server receives it. The proxy server then sends your request to the actual server on your behalf. It mediates between you and the actual server to transmit and respond to the request, as shown in the figure below.