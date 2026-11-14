telnet server.① The “telnet –l /bin/sh” argument starts the telnet server on the default port and binds it to the “/bin/sh” shell. The nmap scan shows that port 23 is now open.② After connecting to telnet, you will note that the user is root.③ Although this has been done on emulated firmware, the same can be accomplished on the actual firmware. At this point, the attacker has root access on the device and can potentially use the device as a launching point for other attacks on the network.

# Summary

This chapter demonstrated vulnerability analysis, both from a static and dynamic point of view. It also demonstrated exploiting a command-injection attack both from a dynamic and emulated point of view. In the latter case, you learned that vulnerabilities can be discovered and proof-of-concept exploits can be developed without even purchasing the hardware equipment. Using these techniques, it is hoped that ethical hackers will find security vulnerabilities in embedded devices and disclose them in an ethical manner, thus making us all more secure.

# Further Reading

+   - ARP spoofing https://en.wikipedia.org/wiki/ARP_spoofing
+   - Busybox https://busybox.net
+   - Craig Heffner’s Binwalk GitHub, https://github.com/ReFirmLabs/binwalk.
+   - Craig Heffner’s blog (creator of binwalk) http://www.devttys0.com/blog/
+   - Craig Heffner’s Firmware Mod Kit GitHub, https://github.com/rampageX/firmware-mod-kit.
+   - Ettercap https://ettercap.github.io/ettercap
+   - Firmadyne GitHub https://github.com/firmadyne/firmadyne
+   - Firmware Mod Kit Prerequisites https://github.com/rampageX/firmware-mod-kit/wiki
+   - IDA Pro Hex-Rays, https://www.hex-rays.com/products/ida

# References

+   1. Bruce Schneier, “Security Risks of Embedded Systems,” Schneier on Security, January 9, 2014, https://www.schneier.com/blog/archives/2014/01/security_risks_9.html.
+   2. Craig Heffner, “Hacking the Linksys WMB54G, Using tftp to Upload a Binary,” /DEV/TTYS0, July 12, 2012, www.devttys0.com/2012/07/hacking-the-linksys-wmb54g/.
+   3. Dominic Chen, FIRMADYNE, https://github.com/firmadyne/firmadyne.