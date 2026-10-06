# Experiencing the Flexible Desktop

The ideal scenario for a user's working environment is the desktop, the laptop computer, or even the Remote Desktop server is nothing more than an appliance.

Consider the help-desk engineer who gets a call from a user having problems with one of their custom applications. For some reason, it won't work. The legacy deployment of a desktop network would require the engineer to sit at that desktop until the problem is resolved. The user has all of their data on a "data partition." Their settings, including their mail archive, contacts, and web browsers, are all local on the PC. There is no alternative to fix that application installation, no matter how long it takes.

Although there have been many improvements to the hardware in our devices to make them more reliable and less likely to fail still happens when the users look to IT to recover their data that was wasted? Sure, Windows 8 and Windows 7 both have a backup tool, but do you really have the time or resources to manage backups for hundreds or thousands of devices and laptops? What would happen in these scenarios if the user's device was nothing more an appliance? You could build the device using something like Windows Deployment Services, Microsoft Deployment Toolkit, or other paid-for-cloning solution like System Configuration Manager (SCCM/ConfigMgr 2012). That allows you to deploy an image of a configured operating system in minutes. Software deployment can be automated using solutions like Group Policy, ConfigMgr 2012, or using Microsoft's application virtualization solution, App-V. That connects the device to a previously known and managed standard in a few more minutes.

Patches are quickly deployed using Windows Software Update Services (WSUS) and ConfigMgr 2012. Group Policy manages the environment. Now the device is secured. This is all great because the device is back to a healthy state and the custom application is correct for the user. This entire process probably took no more than 30 minutes. That's probably much less than the help-desk engineer would have to resolve the issue.

But what about the data the user had on the device? Either youve formatted the disk by rebuilding the device or their data was lost during the hardware failure. Don't worry; the data was on a server all. If they had a laptop, you made it available locally using a synchronized cache. The user will still have access to all their data when they log into their newly built device.

Using the practices we'll cover in the users' data, you will show them how to follow:

+   - Provide backups
- Make data more available
- Allow the user to be mobile from one device to another or to a Remote server while maintaining access to data in a consistent manner
- Reduce time for troubleshooting
- Have users
- Create secure working environments where there is a shared computing
- Preconfigure the working environment to apply security policies or to even make the environment easier to use