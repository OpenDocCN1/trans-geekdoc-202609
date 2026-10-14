Checking error logs allows systems administrators to see who is attacking their servers and what type of attack they might be using.

# WEBSERVER-SPECIFIC APPLICATION PROXY FIREWALLS

One protection is to use an application proxy firewall for a webserver. This firewall sits between the webserver and the rest of the network. It checks incoming request messages for signs of buffer overflow attacks and other problems. It also stops outgoing response messages that are inappropriate.

# Test Your Understanding

+   10.
+     a. What software must be patched on an e-commerce server?
+     b. What three other webserver protections are mentioned in the text?
+     c. Where is an application proxy firewall placed relative to the webserver?

# Controlling Deployment

It is also critical to control the deployment of new server-side applications. As Figure 8-18 shows, firms with rigorous deployment policies use three types of servers: development servers, testing servers, and production servers.

# DEVELOPMENT SERVERS

Server-side programs should be created on development servers dedicated to that purpose. Developers need extensive permissions on these servers.

# TESTING SERVERS

After development, the program is moved to a testing server for testing. Developers should have no access permissions on this server. Only testers should have access permissions to make changes so that developers do not slip in backdoors and make last-minute changes. ("It's just a few lines of code.")

# PRODUCTION SERVERS

After a program has been fully tested on the staging server, it should be moved to the production server that will provide services to users.

# Figure 8-18 Development, Testing, and Production Servers

![](bbox=[0.3, 0.71, 0.9, 0.96])