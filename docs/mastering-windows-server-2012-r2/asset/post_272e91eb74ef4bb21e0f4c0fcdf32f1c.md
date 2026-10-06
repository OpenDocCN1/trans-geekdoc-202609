
# Active Directory Upgrade Strategies

There are a few different scenarios for upgrading Active Directory. You cannot do a direct upgrade from 32-bit Windows 2008 to Windows Server 2012 R2. You can do an in-place upgrade from Windows 2008 R2 to Windows Server 2012 R2 because both versions are x64.
The Following are some Active Directory upgrade scenarios from Windows 2008:

- *When you want to decommission old domain controllers:*
  1. Prepare the forest.
  2. Prepare the domain.
  3. Install Windows 2012 R2 member servers and promote them to be domain controllers.
  4. Decommission old domain controllers.

- *When all old domain controllers are x64:*
  1. Prepare the forest.
  2. Prepare the domain.
  3. Upgrade x64 domain controllers to Windows 2012 R2.

- *When there is a mix of new and old hardware and a mix of x86 and x64 domain controllers:*
  1. Prepare the forest.
  2. Prepare the domain.
  3. Upgrade newer domain controllers to Windows 2012 R2.
  4. Install new Windows 2012 R2 member servers and promote them to be domain controllers. These will replace older Windows domain controllers.
  5. Decommission old domain controllers.

All of these scenarios have a pair of steps in common. A tool adprep is used to upgrade the forest schema, in order to, prepare the forest. This is done by a user who is a Schema Admin, Enterprise Admin, and Domain Admin in the domain that contains the Schema Master forest-wide FSMO role. The same tool is also used to prepare any domain that will contain Windows 2008 domain controllers. This will be done by a user who is a domain administrator of that domain.

The side-by-side approach of upgrading from Windows Server 2008 to Windows Server 2012 R2, requires one more step. It is necessary to apply permissions to Group Policy objects so that they can be managed by the Group Policy management console.

Your final goal to get Windows Server 2012 R2 is a drastic one. You may find that your network is not in a healthy or known state. Sometimes it's better to cut your losses and start with a new Active Directory that is well planned, documented, and maintained. You can build a new forest/domain. You can migrate users, data, and services to the new Active Directory. We've done that in the past when we joined a new company that was going through a spin-off closely followed by a series of mergers. It paid off with a much more stable and manageable environment.

This all sounds very high level, and it is meant to be. It is just a taste of what you can expect in Chapter 7.

# Unattended Installations

We bet you that you were finally getting to the end of this chapter. Surely, there is no more we could discuss about installing Windows Server 2012 R2, right? Well, think again.

Smaller organizations will be happy with the manual approach for installing or upgrading Windows Server 2012 R2 that we discussed earlier in the chapter. However, you may want to put some effort into alternative approaches. You could use a cloning solution such as Windows Deployment Sets, as found in Windows Server since Service Pack 2 for Windows Server 2003, or the free Microsoft Deployment Toolkit. Maybe you already use a third-party solution. There is another way that might be of interest for you that does not require a server to manage the process.

Unattended Installations extend the installation media by customizing your installation. Part of the process is to answer those questions that you probably get sick answering all the time. The idea is that you can setup an installation and walk away knowing that you will not have to answer any questions. The new server will be installed by itself according to your predefined answers. The new installation routine for Windows 8 and Server 2012 R2 is quite small, but if you are building lots of machines, you will soon get to entering product keys, setting OS options, and so on. The other more powerful part is the ability to tweak the installation in ways that are not revealed in the installation process. How would you like to install some components of the operating system that are not revealed in the GUI? You could simplify your post-installation customization and streamline your deployments

All of this is possible by using an answer file that you supply to the installation routine. This approach might be familiar to engineers who have deployed older versions of Windows. In the past you might have used a tool called Setup Manager to create a simple text-based answer file, which you probably had to customize a fair bit in Notepad.

The release of Windows Vista changed all. With Vista have come the release of the Windows Automated Installation Kit (WAIK), which has seen some updates including support for Windows Server 2008, Windows 7, and Windows Server 2008 R2. With the release of Windows Server 2012 R2, this kit has changed name to Windows Assessment and Deployment Kit (Windows ADK). ADK is a very powerful set of tools that include the ability to create a boot DVD. This is boot using Windows PE, a trimmed-down version of Windows that you can use for many tasks including deployment and troubleshooting. More important for this chapter, it includes Windows System Image Manager (WSIM). WSIM is the replacement for Setup Manager and is used to create answer files for Windows 8 and Windows Server 2012 R2.

The other big change you will see is the format of the answer files that you are going to use. It used to be pretty simple to edit files but XML is actually harder to set than the skeleton of the answer file. You generally had to do more work on the answer file in Notepad. WSIM creates XML files. Uh-oh! There that word: XML! Do not let it scare you many administrators at first because they are far from being programmers. But the WSIM interface provides pretty everything you need. You can still go in and edit the file by Notepad or whatever your XML editor is. The only time you might really do it is to jump in and change a product key.

We'll cover how to deploy Windows Server 2012 R2 in an unattended fashion. You'll see how to install ADK, use WSIM to create an answer file, and then use that answer file to get a silent installation.

Note that much, if not all, of what is covered in this section can also be used to deploy Windows 8.

# CHAPTER 2 INSTALLING AND UPGRADING WINDOWS SERVER 2012 R2

# Installing Windows Assessment and Deployment Kit

The exercise that you are now going to go through will demonstrate how to deploy an edition of Windows Server 2012 R2 with very little human intervention. You need to deploy several Windows Server 2012 R2 Standard edition servers. It makes sense to automate builds. You do this by using an answer file to answer the questions you encountered during the manual installation of Windows Server 2012 R2. We'll show how to create that answer file using System Image Manager, and then we will guide you through the process of deploying Windows in an unattended fashion.

ADK is a free set of tools that you can download from Microsoft. We hesitate to include a URL for a download because Microsoft has updated its deployment kits a few times since the initial release. Your best bet is to visit microsoft.com/downloads and search for Windows ADK. This will ensure that you get the latest version of ADK.

You'll be asked by the setup program which you would like to set up on the computer you're using or to download the setup program to be loaded on another machine. If you select to install on the computer you're on to download the ADK, it will download and install it at the same time. For this reason, we suggest you download it to be installed on another computer, which does not install and only downloads the software. This way you will have a complete copy of the software you would need to reinstall.

# NEW ADK RELEASE FOR WINDOWS 8

The download is very large, around 5.1 GB at the time of writing this. You may have previously downloaded ADK before the release of Windows Server 2012 R2. However, Microsoft released a new version to coincide with the release of Windows 8 to support the new server operating systems, so you will need to download a fresh copy of ADK.

The next thing you are going to need is an administrative workstation. An administrative workstation is a PC that you will use to prepare future builds. This might be just like your PC, but that might not be a good location because you're going to be messing with ADK and WSIM once you start to know them; you'll be making a mess of the administrative PC, so your day-to-day machine might not be sensible! Ensure you have enough disk space to play with. You will see soon why. Our preference is to have either a dedicated machine, or a better, virtual machine. The latter offers the benefit of being economical and having the ability to save and restore states. With virtual machines, you can also mount ISO files, which of great benefit you won't waste time messing with virtual and blank disks. Speaking of virtual machines, Virtual machines are great for testing for the same reasons that we like them as administrative workstations.

You will have support if you are running Windows Vista or later. The .NET Framework 4.0 (it will install 4.0 for you) is the prerequisite.

Using Windows Explorer, navigate to the directory where you downloaded the ADK software and run adsetup.exe.

The first screen will appear, asking for an installation location (see Figure 2.60). If you enter a location or the default, click the Next button to continue.
