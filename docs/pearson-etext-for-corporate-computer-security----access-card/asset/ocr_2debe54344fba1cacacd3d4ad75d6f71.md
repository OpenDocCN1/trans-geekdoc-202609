When the computer first connects, the port is in an *unauthorized* state (5). It will not permit the user to communicate over the network. The port remains unauthorized until the computer authenticates itself. After authentication, the port changes to the *authorized* state, and the computer has unimpeded access to the network.

Although the switch port is the primary point of control, the switch is not burdened with having to do heavy authentication work. For that, the switches rely on a **central authentication server** (4). This server has credentials-checking authentication data and the processing power needed to check passwords, biometrics scans, and other access credentials.

There are three advantages in using a central authentication server instead of having each workgroup switch do all the work:

**COST SAVINGS** First, as just noted, this reduces the *cost* of each workgroup switch. If a firm has many workgroup switches spread throughout the building, not having to do heavy authentication processing and not having to maintain an authentication database on each switch is very important.

**CONSISTENCY** Second, using a central authentication server brings *consistency* in authentication. Credential checking is always done the same way, no matter what workgroup switch the attacker connects to. The attacker cannot try different workgroup switches until he or she finds a switch with an incorrect authentication database that allows the attacker in.

**IMMEDIATE CHANGES** Third, central authentication servers bring immediate access control *changes*. For instance, if you fire an employee, you can immediately suspend his or her access to the network on the central authentication server instead of having to reconfigure credential checking on all workgroup switches.

In 802.1X, there are three devices involved in authentication. The computer seeking access obviously is the supplicant (2), but what device is the verifier? Is it the workgroup switch or the central authentication server? Obviously, the verification function is spread across the two devices. Rather than calling either device the verifier, 802.1X calls the workgroup switch the **authenticator** (3). The central authentication server is simply called the central authentication server (4).

# Test Your Understanding

+   11. a. Why is 802.1X called Port-based Access Control?
+       b. Where is the heavy authentication work done?
+       c. What are the three benefits of using a central authentication server?
+       d. Which device is the verifier? Explain. (Tricky question.)
+       e. Which device is called the authenticator?

# The Extensible Authentication Protocol (EAP)

Figure 4-19 shows that 802.1X relies on another protocol, the **Extensible Authentication Protocol (EAP)**, to govern the specifics of authentication interactions. The figure shows a simple authentication dialogue using EAP.

**EAP OPERATION** Ethernet switches can sense when a host connects to one of its ports. When a switch senses a connection, it sends an *EAP Start* message to the RADIUS server (Step 1). This begins the EAP session.