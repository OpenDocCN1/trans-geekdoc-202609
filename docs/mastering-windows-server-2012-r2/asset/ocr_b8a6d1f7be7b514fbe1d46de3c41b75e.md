# CHAPTER 18 CONNECTING WINDOWS AND MAC CLIENTS

+   - Chapter 8, "Creating and Managing User Accounts," shows you how to set up user accounts and computer accounts.

+   - Chapter 29, "Installing, Using, and Administering Remote Desktop Services," covers connecting to domain resources using Remote Desktop.

If you've read these chapters or are generally familiar with the concepts, then read on to learn more about the client networking stack and about the kinds of accounts you'll need. Throughout this chapter, we'll connect to the same server, on the same domain, and with the same user account:

+   - The username is kevbin (if acting as a regular user) or bigadmin (if acting as a domain administrator).

+   - The domain name is bigfirm.com.

+   - There is a Windows Server 2012 domain controller on the network bfl.bigfirm.com.
- There are several client machines on the network, representing the client operating systems we will deal with in this chapter. Their names are:

+   - WIN8CLIENT

+   - WIN7CLIENT

# Understanding Client-side Software Requirements

In the past, each client would have to configure three basic software components: a driver for the network interface card (NIC), a network protocol, and a network client. The good news is that, nowadays, everything you need is built in except on a rare occasion you will need to install an NIC driver.

So that you will have a clear understanding of the underlying technology that makes all of this work, we will review these three basic components.

The NIC driver allows the operating system to communicate with the NIC. Before loading any network protocol or client, the operating system must recognize the network card and load the appropriate driver. By the advancement of Universal Plug and Play (UPnP) and built-in drivers, most of the client systems can automatically detect the NIC and load a driver included with the OS. If the driver is not included with or if your client system fails to detect the network card, you must use the driver and installation media, which are provided by the manufacturer.

The network protocol, built into the operating system, allows nodes on the same network to communicate with each other. To communicate, the nodes must use all the same protocols. TCP/IP is the facto standard for Microsoft networks today. Since most networks use IPv4, we will use that version throughout this chapter. Having a good understanding of IPv6 is becoming much more relevant in today's networks and we recommend that you become knowledgeable on this subject.