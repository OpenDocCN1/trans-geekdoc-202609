# CHAPTER 2 INSTALLING AND UPGRADING TO WINDOWS SERVER 2012 R2

+   - If you are upgrading a production or other important server, then you should back it up before going further. If you're using a virtual machine, this is a lot easier. You can take a snapshot and revert to point in time if the upgrade fails. Check with your vendor for snapshot support in production environments.

+   - You should disable or uninstall your antivirus software on the server to be upgraded. Odds you will need to uninstall it because there is a good chance that it will interfere with the upgrade or even break the upgraded server. Ensure that you have a version of your antivirus software ready to deploy for Windows Server 2012 R2 once the upgrade is completed.

+   - If you are running a monitoring solution such as Center Operations Manager, you will want to disable monitoring for a few hours or remove the agent. Check with your vendor for supported scenarios.

+   - Finally, be prepared for Windows Firewall. It may block traffic destined to your upgraded servers. Know what ports you will need to configure in advance. You may require checking with the application vendor or using a tool like the Microsoft Network Monitor.

We cannot recommend enough that you try this upgrade process in a virtual lab. You can do this cheaply using TechNet or demonstration licenses and with one of a myriad of free virtualization solutions you can try. If you are testing Windows Server 2012 R2, then you can use the following:

+   - Microsoft's free Hyper-V Server 2012

+   - VMware Server, which will run on a Windows Server host

+   - VMware Workstation 9.0

+   
Hyper-V
Note that you will use a virtualization technology, such as those listed, that will support
64-bit virtual machines or guests when testing Windows Server 2012 R2.

# Using Hyper-V

You're learning about Windows Server 2012 R2, so to see it is logical to use Hyper-V. We strongly recommend reading Chapter 27, "Virtualization with Hyper-V," and Chapter 28, "Deploying Virtual Machines with Hyper-V," to learn how you can deploy a virtualization environment for your test lab.

All of the ways are out of the way, now let's take a look at an action in. You cannot perform an in-place upgrade if you boot your server from the DVD or USB device. This method allows only a clean installation. If you want to do an upgrade, then you will have to boot up your Windows Server and insert the DVD or USB or in the case of a virtual machine, mount your Windows Server 2012 R2 media ISO image. This allows the upgrade program to download updates from Microsoft and to properly scan your server before any changes are made.