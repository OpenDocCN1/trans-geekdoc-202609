REMOTE DESKTOP FOR ADMINISTRATION 907

In past versions of Windows, it was possible to remotely administer servers from the Internet. However, you had to open port 3389 on the firewall (or convince the firewall administrator to open the port). But every additional port opened on a firewall presents an vulnerability that needs to be managed.

From a security standpoint, it's much easier to leave the port closed. Even though remote administration through port 3389 was a useful feature, it was often blocked by the network firewall to mitigate the associated risks.

Since RD Gateway uses RDP over HTTPS through port 443, the external firewall needs only port 443 open. Port 443 is common to open all other HTTPS traffic. If port 443 is for other HTTPS traffic, you don't need to open additional ports to use RDP over HTTPS.

As an example, if a company was hosting a web server over HTTP and HTTPS, ports 80 and 443 would be needed to support the web. You then implement RD Gateway on a server in the DMZ without modifying the firewall.

Even if port 443 isn't alone, the security of HTTPS is well understood by most administrators. It's easier for an administrator to weigh the risks of HTTPS and make a decision to open this port than it is to consider opening port 3389 for remote administration.

# REMOTE DESKTOP CONNECTION CLIENT

RD Gateway supports connections from Remote Desktop Connection 6.0 or greater. However, to support all the features available in Windows Server 2012 R2, Remote Desktop Protocol 8.0 is recommended. This is natively provided in the RDC client supplied with Windows 8 and Windows 2012. The RDP 8.0 is also available as an add-on for Windows 7 SPI and Windows Server 2008 R2 SP1 (http://support.microsoft.com/kb/2592687).

Although these features are most useful when using Desktop Services to host desktops and remote applications, administrators may find them useful too. These are some of the additional features that are available:

RemoteFX RemoteFX technologies enhance the user's visual interface experience. There are a number of new improvements enhancing RemoteFX:

+   - WAN support

+   - Network Auto Detect

+   - Adaptive Graphics

+   - Media Streaming

+   - USB Redirection for non-RemoteFX vGPU virtual desktops

Support for Nested Sessions You can now run a remote desktop session from within another remote desktop session.

Performance Counters for Monitoring the User Experience Performance counters lets monitor and troubleshoot user experience issues.