# FIGURE 5.1 MegaPing IP Scanner

![](bbox=[0.14, 0.13, 0.84, 0.525])

**Hands-on Activity**

Download a copy of MegaPing from the Magento Software website. Run a ping sweep using the IP Scanner. Make sure to identify the MAC addresses for all of the systems.

The ping sweep may be telling, but it’s only a start. It may be used just to get a sense of the number of hosts that you may need to think about testing. The ping sweep will give you only a limited amount of information. Just knowing a host is up (and the information that a host isn’t up may be unreliable) doesn’t tell you a lot. Ultimately, you want to know what services are running on the host. A ping sweep will give you an idea of what systems may be targetable. Depending on how you are approaching your testing and where you are, this may be valuable. You may also consider just moving directly to a port scan, especially since port scanners will often do a ping ahead of the port scan to make sure the system is up before bothering to send port probes.