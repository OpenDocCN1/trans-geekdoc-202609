# Client Protections

As noted earlier, many firms use application proxy firewalls to protect internal clients from malicious external servers. For HTTP, proxy programs can do several types of filtering. We will only list three:

+   - The proxy can inspect the URL and compare it with a table of black-listed URLs that are known phishing sites, pornography sites, or recreational sites.
+   - The proxy can inspect *scripts* in downloaded webpages and drop these webpages if the scripts appear to be malicious or if policies prohibit either certain types of scripts or all scripts.
+   - The proxy can inspect the *MIME type* in an HTTP response message. The MIME type describes the type of file downloaded in the message. Certain MIME types of files might be allowed or dropped by policy.

The HTTP proxy can also examine outgoing packets from the internal client to the external webserver to detect client misbehavior. For example, the proxy can inspect the method in the URL header. The HTTP GET method is generally safe because it is used to retrieve files. However, the POST method can send files out of the firm. Many firms drop any HTTP request message that uses the POST method in order to provide *extrusion prevention*.

# Server Protections

For servers, the HTTP proxy program attempts to protect the server from malicious clients.

+   - As just noted, the proxy can inspect the method in the URL header. The POST method will allow clients to upload files to the webserver. This might be disallowed by policy to prevent clients from uploading malware, pornography, or any other type of unimproved content.
+   - The HTTP proxy might also filter out HTTP request messages that appear to contain SQL injection attacks. (We will learn about this type of attack in a later chapter.)

# Other Protections

In addition to filtering the content of the application layer message, there are three other protections that application proxy firewalls offer.

+   - *Internal IP address hiding*—Like NAT, application proxy firewalls hide the IP addresses of internal hosts. Packets that leave the firm have as their source IP address the IP address of the application proxy firewall, not the IP addresses of the internal hosts. This can thwart packet sniffers and network mapping.
+   - *Header destruction*—Recall that when a packet arrives at an application proxy firewall, the proxy program examines the application layer message. To do this, the proxy program decapsulates the application message. In doing so, it discards the internet and transport layer headers in the arriving packet. If the attacker has manipulated the fields in the internet or transport layer headers to cause problems, header destruction automatically defeats these attack methods. If the application proxy firewall passes the application layer message, it places the message in a new transport message and a new internet packet. The attacker has no way of affecting the contents of fields in these new headers.
+   - *Protocol fidelity*—In operation, the application proxy program acts like a server to the client and like a client to the server. Suppose the client and the server attempt to get around firewalls by using Port 80—the well-known port for HTTP—to handle a different program, such as an instant messaging program that the company has forbidden. In such cases, the connections to the