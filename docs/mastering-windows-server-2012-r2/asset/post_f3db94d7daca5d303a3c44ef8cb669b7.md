
Windows Server 2012 R2 VDI if running in a datacenter, will allow access for mobile devices using Hyper-V and Remote Desktop Services. Microsoft offers three different deployment types in a single solution: pooled desktops, personal desktops, and remote desktop sessions.
You can read more about VDI in Chapter 27.

## Networking Changes

Servers are no good without the ability to talk to one another

## EAP-TTLS

With Windows Server 2012 R2 an exclusive protocol is introduced as an Extensible Authentication Protocol (EAP) type called Tunneled Transport Layer Security (TTLS). This protocol is used with 802.1X Authenticated Wired and Wireless access. This new standards-based protocol provides a secure tunnel for client authentication. 802.1X provides a security shield that prevents unauthorized access to your allant.

## DNS

Although DNS has been around before, the process by which it translates names to get better with each change. Changes in Windows Server 2012 R2 affect both DNS Server and Client. Let's take a look at the changes for Windows Server 2012 R2.

In PowerShell, DNS management has received some improvements. The DNS Server role, for example, has had some improvements to installation and removal using PowerShell. Additional developments in PowerShell include user interface, client query, and server configuration on older operating systems. The LLMNR query time-out has been 300 msec, which is not enough for computers in power save mode. With the new improvements to DNS, client time-out has been increased to 820 msec.

## IP Address Management

The IP Address Management (IPAM) framework is a new set of technologies for managing, monitoring, and auditing IP space. By monitoring DHCP and DNS, IPAM can locate IP addresses within your network and allows you to manage them from a single central UI.

## NIC Teaming

NIC Technology in Windows Server 2012 R2 can take multiple network interface cards and them together to interface as one. Doing so helps with failover one device become in. Load balancing is also improved when NICs are teamed because the bandwidth is combined into a single larger bandwidth.

You can read more about these topics and new features in Chapter 4, "Windows Server 2012 R2 Networking Enhancements," and Chapter 5, "IP Address Management and DHCP Failover."

## Management Tools

Any good networking operating system offers ways to simplify the job of keeping one server or thousand servers up and running. The server should also stay up and running with the smallest amount of effort possible on the part of the humans doing the server administration. No operating system has the answer for server administration, but Windows Server has a bit better in 2012 R2 with some useful new tools.

## Server Manager

Prior to Windows Server 2008, when an administrator had to configure and maintain a server, the administrator would have to use many different tools. Windows Server 2008 changed all by introducing Server Manager, a one-stop shop for all of your configuration and management tools.

In Windows Server 2012 R2 (Figure 1.3), Microsoft has expanded this functionality further. Server Manager lets administrators manage multiple servers (virtual or physical/local or remote) as long as they are no older than Windows Server 2003.

![](img/41a83208e6906a3732620203b836cea7_47_0.png)

Adding roles and features in Server Manager has gone even smarter. As you make your selections, the Add Roles and Features Wizard dynamically changes. The wizard assists you in deciding which subset of tools and features are needed for the requested role.

Server Manager has a new dashboard that can show you if problems exist using color-coded boxes. If, for example, an error occurred from within the DNS event, the DNS box on the dashboard would turn red. This is an excellent tool for troubleshooting your server, and since the dashboard is the first thing you see when you log in, you can't miss it.

## MANAGEMENT TOOLS

Speaking of troubleshooting your server, Server Manager has a host of new troubleshooting tools that we will show you more about in Chapter 2. These tools are all inside, inside Server Manager, you do not have to run multiple applications like Event Viewer or Performance Analyzer to see the results—they are all in one!
You can read more about Server Manager in Chapter 2.

## The Remote Tools: WinRM and WinRS

It's all too often that new operating systems include some really important and useful features that go largely unnoticed. Windows Server 2012 R2 contains one of these largely unknown features in a new network protocol called Remote Management (WinRM). To understand why WinRM is a great feature, let's consider what WinRM is intended to replace: a protocol known as the Procedure Call (RPC).
Even if you've never heard of RPC, there are chances you are using it for years. RPC's job is to allow one program to talk to another, even if those programs are running on different computers. For example, if you started up Outlook to read your email on an Exchange server, then you used RPC; how Outlook can sync to the shoulder or if you used an MMC snap-in DNS, DHCP, or Management to remotely control functions on a computer you've used RPC.
RPC is a protocol that has provided great service over the years, but it has one big problem: it is hard to secure. Microsoft inserted RPC back in the days when there was Internet, and the vast majority of LANs extended further than the distance from the first floor to the top of an office building, security wasn't all a big concern. Years later, when security became a big concern, Microsoft tried to retrofit security over RPC with some changes first by XP SP2, but by that point the horse was out of the barn, and requiring RPC security would just end breaking hundreds or perhaps thousands of RPC-dependent applications.
Clearly, the time came for a change in how Windows programs talk to each other, Microsoft decided to adopt a protocol that did the same sort of RPC did, with a few changes:

- It is not proprietary but standards-based and platform-independent—there are similar implementations popping up on Linux and Mac OS.
- It is a modified form of HTTPS.
- Its communications are encrypted.
- It requires authentication to use.

Components of Windows 2012 R2 use WinRM include log collection; the ability to use the new Server Manager snap-in on remote servers; and my favorite, a secure remote command called Windows Shell, or winrs. If you need a secure, low-bandwidth remote-control tool, look to winrs. Read more about WinRM in Chapter 17, "Remote Server Administration."

## Remote Desktop Services

In Windows Server 2012 R2 Microsoft has made large strides in improving the user and management experience. Microsoft intended to improve the user experience regardless of the kind of device being used to connect. They wanted to make sure connecting through a WAN or LAN (to virtual desktops, RemoteApp programs, or session-based desktops) provides a experience to the user. Microsoft also wanted to make the remote desktop management experience better. We agree that they made it better by adding a centralized console so administrators can manage Remote Desktop Services from a single location.

You can read more about Remote Desktop Services in Chapter 17.

## Group Policy Object Improvements

What got better? Plenty. Managing Group Policy objects (GPOs) got easier with the built-in Group Policy Management Console. In previous Windows versions, one problem that administrators had was manually forcing a GPO to update. Even though GPOs automatically update every 90 minutes, there are times when you need a GPO to take effect immediately. Administrators had to remote to the specific computer and run gupdate.exe from the command line to manually updating a GPO.

Now if an administrator wants to manually force a GPO update, the administrator can use the context menu for an OU in the Group Policy Management Console and schedule gupdate. exe to run on multiple computers at the same time. Administrators can also achieve this by using the PowerShell utility and the new Invoke-GPUpdate cmdlet.
Here are some additional changes to Group Policy in Windows Server 2012 R2:

- When dealing with monitoring replication issues at the domain level, you no longer need to download separate tools.
- For devices using RT, you can now configure local Group Policy. By default it is disabled, and the service must be set to and automate.
- Group Policy has been upgraded to support Internet Explorer.

You can read more about Group Policy in Chapter 9, "Group Policy: AD's Gauntlet and Active Directory Delegation.".

## File and Print Sharing

Back before we ran web or email services on our Windows servers, we only used Server for things: big drives and expensive printers. File and print are the oldest services offered Microsoft networks, but apparently they're not too old to learn a few tricks.

## BranchCache

BranchCache is a technology that optimizes Windows bandwidth by copying content either your main location or cloud server to your branch office. Once content is copied to the branch, users can cache rather than over the WAN. Having benefit to cache files will conserve bandwidth and improve service. BranchCache can support any size office and is not limited to how many times it can serve. BranchCache can be deployed with just a single Group Policy object (GPO). This technology uses the Windows file server to divide files into small encrypted pieces. The cool thing about dividing the files into smaller pieces is that client computers can download only the pieces that changed. BranchCache will also check for duplicate content and only download one instance of the content, saving disk space.
