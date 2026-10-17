Just as you take steps to harden your servers (such as patching the operating system and shutting down unneeded services), you should also harden your router. The specifics of what needs to be done will be contingent on your particular router manufacturer and model, but a few general rules should be followed:

+   - **Use good passwords:** All routers are configurable. They can be programmed. Therefore, you must obey the same password policies on a router that you would use on any server, including minimum password length and complexity, age of password, and password history. If your router allows you to encrypt the password (as Cisco and other vendors do), then do it.
+   - **Use logging:** Most routers allow for logging. You should turn this on and monitor it just as you would monitor server logs.
+   - **Security rules:** Some basic router security rules should also be followed:
+     - Do not answer to Address Resolution Protocol (ARP) requests for hosts that are not on the user local area network (LAN).
+     - If no applications on your network use a given port, that port should be also shut down on the router.
+     - Packets not originating from inside your LAN should not be forwarded.

These rules are simply a beginning. You will need to consult your vendor’s documentation for additional recommendations. You must absolutely pay as much attention to securing your router as you do to securing your servers. The following links might be helpful:

+   - **Router security:** [www.mavetju.org/networking/security.php](http://www.mavetju.org/networking/security.php)
+   - **Cisco router hardening:** [www.sans.org/rr/whitepapers/firewalls/794.php](http://www.sans.org/rr/whitepapers/firewalls/794.php)

# Scanning Your Network

The only way to be sure your network is secure is to actually check for vulnerabilities and flaws. In this section, we will look at some commonly used vulnerability scanners. These tools can be an invaluable asset for any network administrator.