they can't connect. The Network Policy Server (NPS) service that you installed earlier is for
they policies are managed in Windows Server 2012 R2.

NPS can be used to create and enforce network access policies throughout an organization.
Although this focuses on remote access, NPS can be used to create advanced policies
to check any computers, including those in an internal network. Computers that don't meet the
predefined conditions set by the administrator can be quarantined, and network access can be
denied.

Policies are configured within the NPS console, and the NPS console can be accessed
from two different methods. However, the console has different capabilities when accessed
differently.

**Launch from Routing and Remote Access** Inside the Routing and Remote Access snap-in,
y you can click-right Remote Access Logging & Policies and Select NPS. When launched
this way, NPS shows only the options that are directed to RRAS. The top console in
Figure 21.7 was launched from RAS and is the focus in this chapter.

# FIGURE 21-7
Network Policy
Server consoles
when launchedrom RRAS
(top) and when launchedrom Administrative
Tools (bottom)

![](bbox=[0.29, 0.377, 0.86, 0.706])

**Launch via the Tools Menu** When launched by selecting Server Manager ➤ Tools
Network Policy Server, many additional tools are available. The bottom console shown in
Figure 21.7 was launched from the Tools menu.

NPS includes two default policies in the Network Policies. Each of these is set to
Deny Access when created but can be changed. The two policies are as follows:

**Connections to Microsoft Routing and Remote Access Server Policy** This includes a single
condition that the RADIUS client must be a Microsoft client (specified as MS-RAS
Vendor 3111). This applies only to RADIUS clients.