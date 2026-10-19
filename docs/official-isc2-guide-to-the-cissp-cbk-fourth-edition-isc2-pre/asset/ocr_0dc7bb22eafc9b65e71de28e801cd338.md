![](bbox=[0.13, 0.01, 0.9, 0.2])

+   1. User's request goes to the proxy server.
+   2. Proxy server forwards the request to the untrusted host. To the untrusted host it will appear as if the request originated from the proxy server.
+   3. The untrusted host responds to the proxy server.
+   4. The proxy server forwards the response to the user.

Figure 4.11 – Accessing a server through a proxy

To the user, it appears that he or she is communicating directly with the untrusted server. Proxy servers are often placed at Internet gateways to hide the internal network behind one IP address and to prevent direct communication between internal and external hosts.

# Circuit-Level Proxy

A circuit-level proxy creates a conduit through which a trusted host can communicate with an untrusted one. This type of proxy does not inspect any of the traffic that it forwards, which adds very little overhead to the communication between the user and untrusted server. The lack of application awareness also allows circuit-level proxies to forward any traffic to any TCP and UDP port. The disadvantage is that traffic will not be analyzed for malicious content.

# Application-Level Proxy

An application-level proxy relays the traffic from a trusted end point running a specific application to an untrusted end point. The most significant advantage of application-level proxies is that they analyze the traffic that they forward for protocol manipulation and various sorts of common attacks such as buffer overflows. Application-level proxies add