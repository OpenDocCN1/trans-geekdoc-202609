# # Chapter 31

#  Patch Management

Patch management has been the process of minimizing your organization's threat and vulnerability surface by managing and deploying software updates, but over time it has moved to support feature updates and overall product updates. Updates can be deployed and managed by a number of different products and tools; an example of this is System Center Configuration Manager. In this chapter we will focus on the toolkit built out of the box. Software updates demeaning the Windows Server 2012 R2 framework is an everyday task in today's online and collaborative world. The frequency at which you deploy and validate updates can mean the difference between having compromised or damaged computers or enjoying the weekend with your family and friends.

Software updates seem like a never-ending cycle, and unless you enjoy walking around to install every update, you need tools to help you do the job. You need to know whether each update is deapplicable to computers on your network, whether it is compatible with your existing applications, and how urgent it is to deploy this update.

In this chapter we walk through install and configuration of the Windows Server 2012 R2 Windows Update Services role and what you need to consider when you are deploying this patch-management process. After, we analyze security updates and then take a detailed look at Windows Server Update Services (WSUS), which is now integrated into the operating system as a server role. We then cover how to migrate from Windows Server 2008 R2 WSUS to Windows Server 2012 R2 WSUS, and finally we present an overview of the available PowerShell cmdlets. In this chapter, you will learn to:

+   * Use Windows Automatic Updates to check for new updates on a computer running Windows 8
* Use the Windows Update Standalone Installer to silently install a security update
* Identify the four phases of patch

# ## What's New in Windows Server 2012 R2 Windows Update Services

Windows Server Update Services (WSUS) is now integrated into Windows Server 2012 R2. This new role allows administrators to use the Server Management tool to configure and manage