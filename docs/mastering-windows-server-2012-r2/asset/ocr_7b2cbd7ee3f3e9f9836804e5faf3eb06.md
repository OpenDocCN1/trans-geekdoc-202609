+   First, unless they're starting fresh, people already have the PCs. Even though WBTs are a little less expensive than low-end PCs (not much, though), they're an added cost.

+   Second, not all applications work well in an RDS server environment. It's often best to run some applications on the RDS server and some locally.

Unless you're buying new hardware and don't anticipate any need to run applications locally, you're likely to have to wire with PCs for at least some of your terminal clients.
To work with Remote Desktop Services, the PCs must be wired to a Windows operating system, have RDP display protocol installed, and a live network connection using TCP/IP and a valid IP address.

# TABLETS

We're not surprised that tablets are so commonplace today, how handy they are. They're a substitute for a laptop—inexpensive, lightweight, and with their power so that travelers can use them during the entire flight without having to give up two hours takeoff.(You can also use one on a plane without worrying that the person in front of you will suddenly reclaim their seat and close your laptop's display) Usually, they run Windows or Android or Apple iOS. You can use wired or wireless connections to connect to an RDS server with VPN or without.
What a tablet looks like depends on who makes it. Some tablets look like a laptop's baby brother, like Microsoft Surface. Others fold into a little portfolio shape or are a flat table. Some are small pocket-sized deals that are too small to work on.—The ones we prefer—have keyboards; others have only styluses. What all this comes down to is a tablet isn't generally in a position to replace a desktop PC, although there are some exceptions the Microsoft Surface Pro, which is a tablet with a keyboard that has the power of a desktop. A tablet is usually used in cooperation with a primary machine which it's partnered in some way, using OneNote or SkyDrive, for example.

# Adding Remote Desktop Services

You can add the Remote Desktop Services to any domain-joined Windows Server 2012 R2 using Server Manager. Server Manager includes wizards that allow you to add many roles, and you've probably already used it.
When adding the RDS role, the Roles and Features Wizard first gives you a dedicated menu (see Figure 29.2). Then it will ask you for further RDS-specific questions.
The following sections provide the knowledge you need to answer these questions and successfully add the role. Topics related to an RD Session Host server installation include the following:

+   Additional Level services

+   Network Level Authentication

+   Licensing mode

+   Local Remote Desktop Users group membership

+   Adding applications