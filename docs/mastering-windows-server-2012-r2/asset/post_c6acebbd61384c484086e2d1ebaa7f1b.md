
# REMOTE DESKTOP FOR ADMINISTRATION

If you are connecting to a remote server through an RD Gateway, you will configure the connection settings here. RD Gateway will be covered in more detail later in this chapter. The important thing to realize is that the server name you enter here is that of the gateway server. RDC will connect to the RDC server first and then to the remote server identified on the General tab.

You will need to authenticate with both the RD Gateway and the remote computer. If you use the same credentials for both, you can check the "Use my RD Gateway credentials for remote computer" check box. With this check selected, you will be challenged only once. If you deselect it, you will be challenged at both servers, and you can enter different credentials for each.

Although knowing each of the tabs in the Remote Desktop Connection can do for you useful, you will want to know some other details. For example, you can launch it from the command line, and with any command-line command, there are useful switches to master. Additionally, you can control several limitations on remote connections.

# MSTSC

You can launch the Remote Desktop Connection from the Run or the command line using the mstsc.exe command. The name mstsc is derived from Microsoft Terminal Services. Even though Terminal Services has been used for Remote Desktop Services, the mstsc command is still the same.

You can access the help screen by entering mstsc / at the command line. The following items show some of the common uses for mstsc:

**Default Usage** Use the following command to launch Remote Desktop Connection (RDC):

mstsc

**Identify a Server** Connect to a server named Srv1 using the /v switch:

mstsc /v:srv1

**Use an RDP File** Launch RDC using an RDP file located in the path c:\data\srv1.rdp:

mstsc c:\data\srv1.rdp

**Connect in Full Screen** Use the /f switch to RDC in full-screen mode after the connection is established:

mstsc /f

**Use Multiple Monitors** If you want RDC to be able to span multiple monitors available your local system, use the /span switch. This will cause the remote system to use the same width and height of your local desktop.

mstsc /span

**Connect for Administrative Purposes** The /admin switch is used to connect to a Windows Server 2012 R2 server for administrative purposes. This is meaningful only if the server has the Remote Desktop Services installed. In other words, when the server is used for Remote Desktop for Administration mode only, all connections are for administrative purposes, and this switch isn't needed. However, if the server is configured as a Remote Desktop Session Host server, you can use this switch to connect to one of the two administrator sessions.

# CHAPTER 17 REMOTE SERVER ADMINISTRATION

You can also use the /admin switch to launch RDC in legacy console mode when connecting to Windows Server 2003 servers. Windows Server 2003 servers support a console session that isn't supported in Windows Server 2012 R2. The /admin switch will connect to the console session in Windows Server.

# CONNECTION LIMITATIONS

Only two connections are allowed to the server when it is used for normal administrative connections. In other words, only two administrators can be logged onto a single server at a time.

If the server is used to host desktops or applications for end users, then you can have as many connections as you need. Remote Desktop Services requires licenses for connections used in Remote Desktop session host server mode. However, licenses are not required for the two administrator connections.

The two connections include either remote sessions or the session at the computer. Previous operating systems allowed you to connect to two remote sessions and the session at the computer. The session at the computer was referred to as the console session and you were even able to connect to this console session remotely, but the console session is no longer available. Figure 17.12 shows what a third user tries to connect when two sessions are already active.

FIGURE 17.12 Blocking the third remote session

![](img/41a83208e6906a3732620203b836cea7_931_0.png)

In the figure, a user named Darril is physically located at the server and logged on. Sally is connected via a remote session. Joe tries to log on, but since his session will be the third, it is blocked. Notice that the dialog indicates whether these sessions are active or idle. In the figure, Sally's session has been idle for 11 minutes and Darril's session is active. If Joe selects the check box next to "Force disconnected of this user" and selects one of the users, that user will be immediately disconnected with a message saying:

Your Remote Desktop session has ended. Another user connected to the remote computer your connection was lost. Try connecting again, or contact your network administrator or technical support group.

If Joe doesn't select the check box but instead just selects one of the users to disconnect the session, the user will get a notification. Figure 17.13 shows what appears on Darril's session when Joe tries to disconnect without the check box selected. If Darryl is working at the computer, he can see this connection attempt and click Cancel to block it. Otherwise, the request will automatically disconnect Darryl's session after 30 seconds and allow Joe session.

# FIGURE 17.13
Disconnect request

![](img/41a83208e6906a3732620203b836cea7_932_0.png)

# ACTIVE CONNECTIONS FOR INACTIVE SESSIONS

Figure 17.13 shows what appears on Darril's session when Joe tries to disconnect without the check box selected. If Darryl is working at the computer, he can see this connection attempt and click Cancel to block it. Otherwise, the request will automatically disconnect Darryl's session after 30 seconds and allow Joe session.

# FIGURE 17.13
Disconnect request

![](img/41a83208e6906a3732620203b836cea7_932_0.png)

If Darryl is working at the computer, he can see this connection attempt and click Cancel to block it. Otherwise, the request will automatically disconnect Darryl's session after 30 seconds and allow Joe session.

# ACTIVE CONNECTIONS FOR INACTIVE SESSIONS

Figure 17.13 shows what appears on Darril's session when Joe tries to disconnect without the check box selected.

This, the to the the session is active or idle, and even to to the session.

# INSTALLING REMOTE DESKTOP SERVICES WITH SESSION HOST

For the next few sections of this chapter you will need Remote Desktop Services installed on the server. To install this role, do the following:

- Open Server Manager, and click Add Roles and Features.
- Click Next to get past the “Before you begin” screen.
- On the next screen, select “Role-based or feature-based.”
- Next, select the server that you will install the role on.
- Next, select the Remote Desktop Services role, as shown in Figure 17.16, and click Next.
- Since you do not need any features in the Features screen in Figure 17.17, just Next to continue.
- In the next screen, shown in Figure 17.19, the following role services are available:

- Remote Connection Broker: Allows users to reconnect to their existing virtual desktops and session-based desktops. It also enables you to load-balance the pooled virtual desktops.
- Remote Desktop Gateway: Enables authorized users to connect to an internal corporate network from any Internet-connected device.
- Remote Desktop Licensing: Manages the licenses required to connect to a Remote Desktop Session Host.
- Remote Desktop Session Host: Enables a server to host session-based desktops.
- Remote Desktop Virtualization Host: Integrates with Hyper-V to deploy pooled or personal virtual desktop collections within your organization by using Remote Desktop Connection.
- Remote Desktop Web Access: Allows users to connect via a web browser.

Select Remote Desktop Session Host.
