
Windows Server 2012 R2 can't do very much. It has no functionality installed. It's actually up to you to decide what this server will do on your network and what functionality should be installed. The result of this is that the server has a smaller attack surface. What does that mean? The functionality you install on a computer, the more targets you present to attackers. The goal is to install only the functionality you require, in other words, to reduce the number of targets or minimize your attack surface. Furthermore, on the security side, the operating system is locked down by default. The first thing it does when it boots up is request a new administrator password. You'll also find that the Windows Firewall is by default. This operating system pretty much isolates itself from the network until you configure it. It puts you in control of how this server interacts with your network and/or the Internet.

Does this sound like it is to a lot of work to get a server up and running? Maybe, but actually Microsoft has made it pretty easy. If you are doing manual installations or upgrades, you can quickly configure your servers using Group Policy and Server Manager. We'll talk about Server Manager later. If you're deploying many servers, you'll want to look at automated solutions like Windows Deployment Services or your favorite third-party solutions. Again, you can use Group Policy to deploy policies and use the command-line version of Server Manager, called PowerShell, in a scripted to customize the roles and features of the server.

## ABOUT SERVER CORE

You can learn more about the Server Core installation of Windows Server in Chapter 3, "Managing a Server without a Desktop: Server Core." The Server Core installation uses some different tools for configuring the functionality installed on a server.

How are you going to deploy Windows Server 2012 R2? There are some complications here. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## Installation Requirements

In previous versions of Windows Server, there would be different requirements for each edition of you wanted to install, that is, Enterprise versus Standard edition. In Windows Server 2012 R2, Enterprise edition is no longer available and the requirements have been scaled down to one set for all.

As usual, you are given a set of minimum and recommended requirements with the operating system. Be aware that minimum means exactly that; the operating system will run, but it will not necessarily run well. You should also take account of the applications that will be installed and the load that will be placed on your server.

This can vary wildly depending on applications and organizations, and and-fast rules on what your server specifications should be. The best thing to do is to develop a pilot environment and generate loads on your “proof-of-concept” servers monitoring the performance and responsiveness of the servers and applications. However, if your server is going to have moderate loads in a small environment, you're probably going to be OK with the recommended specifications.

## Table 2.1: Windows Server 2012 R2 Requirements

| Item | Minimum | Recommended | Maximum |
| :--- | :--- | :--- | :--- |
| CPU | 1.4 GHz for x64 | 2 GHz | 64 processor |
| RAM | 512 MB | 2 GB or more | 32 GB for Standard, 4 TB for Datacenter |
| Disk | 32 GB | 40 GB plus additional space for applications or, 10 GB Server Core Installation | | |
| DVD-ROM | Required to access the installation media; CD-ROM no longer supported | | |
| Display | Super-VGA (800x600) or higher | | |
| Input devices | Keyboard and compatible pointing device, such as a mouse | | |
| Internet Access | Required | | |

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade.

## CHAPTER 2: INSTALLING AND UPGRADING TO WINDOWS 2

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## 64-Bit Support

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## Installing the Operating System

## Performing a Clean Installation

[content]

In previous versions of Windows Server, there would be different requirements for each edition of you wanted to install, that is, Enterprise versus Standard edition. In Windows Server 2012 R2, Enterprise edition is no longer available and the requirements have been scaled down to one set for all.

As usual, you are given a set of minimum and recommended requirements with the operating system. Be aware that minimum means exactly that; the operating system will run, but it will not necessarily run well. You should also take account of the applications that will be installed and the load that will be placed on your server.

This can vary wildly depending on applications and organizations, and and-fast rules on what your server specifications should be. The best thing to do is to develop a pilot environment and generate loads on your “proof-of-concept” servers monitoring the performance and responsiveness of the servers and applications. However, if your server is going to have moderate loads in a small environment, you're probably going to be OK with the recommended specifications.

## Table 2.1: Windows Server 2012 R2 Requirements

| Item | Minimum | Recommended | Maximum |
| :--- | :--- | :--- | :--- |
| CPU | 1.4 GHz for x64 | 2 GHz | 64 processor |
| RAM | 512 MB | 2 GB or more | 32 GB for Standard, 4 TB for Datacenter |
| Disk | 32 GB | 40 GB plus additional space for applications or, 10 GB Server Core Installation | | |
| DVD-ROM | Required to access the installation media; CD-ROM no longer supported | | | |
| Display | Super-VGA (800x600) or higher | | | |
| Input devices | Keyboard and compatible pointing device, such as a mouse | | | |
| Internet Access | Required | | | |

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## AUDITING YOUR CURRENT INFRASTRUCTURE

It is critical that you accurately audit your existing infrastructure if planning a major change such as. Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## CHAPTER 2: INSTALLING AND UPGRADING TO WINDOWS 2

## 64-Bit Support

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

- Windows Server 2012 R2 is available with 64-bit architectures. Microsoft is shifting all of its products to 64-bit only. This means you cannot upgrade 32-bit installations of Windows Server 2008. You'll have to do a clean install on new hardware and move any services or data. If you have 64-bit deployments, you can do an in-place upgrade. This can be a time-saver, but it's not recommended. Microsoft pretty much urges you to do a clean install every time. If your server is running Microsoft features, roles, and applications (all 64-bit), then an in-place upgrade is possible. We've done this and had reliable servers afterward.

## Installing the Operating System

## Performing a Clean Installation
