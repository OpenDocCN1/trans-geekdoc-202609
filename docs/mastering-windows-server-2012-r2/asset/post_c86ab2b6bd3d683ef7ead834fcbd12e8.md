
# FIGURE 17.6

Remote Desktop Connection unknown certifying authority warning Name:

![](img/41a83208e6906a3732620203b836cea7_924_0.png)

- 12. Click Yes to connect despite the warning.

Your system will then connect to the remote session. Take your time looking around in the remote session.

If you used the defaults in RDC, the connection bar will display across the top of the screen with the name of the server. If you click the X to close the screen, you will disconnect the session, but you will not close it. The session will remain open, consuming resources, either until you reconnect or log off, or until another administrator closes your session.

- 13. Click Start, and select Log Off to log off close the session.

# UNKNOWN PUBLISHER Warnings

When using an unsigned RDP file, you will see two warnings indicating that the publisher of the remote connection cannot be identified and asking whether you want to connect anyway. The first warning is shown at the top of the dialog box in Figure 17.5, and the second warning is shown in Figure 17.6.

RDP files can be signed using certificates for security. A signed RDP file has a signature within it indicating the identity of the client of the certificate authority (CA) that verified that identity. If you trust the CA, you will trust this RDP file. When distributing RDP files to many clients, this security feature can be quite valuable.

However, RDP files do not have to be signed. Since you are creating this RDP file, you can simply ignore the warnings.

The RDP file is associated with the Remote Desktop Connection application, so by double-clicking, you will launch RDC. However, this RDP file is simply a text file. If you want to look at the contents, you can use Notepad and browse to the file to see the contents.

# RDC DISPLAY TAB

The Display tab allows you to configure the display for the remote desktop. You can configure the size of the desktop and the colors from this page. Figure 17.7 shows the Display tab.

FIGURE 17-7
Remote Desktop Connection Display tab

![](img/41a83208e6906a3732620203b836cea7_925_0.png)

If you drag the slider all the way to the right, the remote desktop will display in full-screen mode. By default, a connection bar will be displayed across the top when in full-screen mode.

# INCREASED PERFORMANCE OVER A WAN LINK

If you're accessing the remote server over a slow WAN connection, you can get increased performance by using a smaller screen or reducing the number of colors displayed. This isn't a problem in a well-connected network with a maximum of two remote sessions, but with a slow link, it helps.

The connection bar includes name of the remote server, which can be useful if you have more than one instance of RDC running at a time. For example, if you're troubleshooting a problem and remote into three different servers using three different instances of RDC, you can quickly glance at the connection bar at the top of the window to remind yourself which server you're accessing.

When you remote into a server using RDC in full-screen mode, this connection bar is the only apparent difference you'll see. Everything else will look as if you're standing in front of the server.

At the left of the connection bar is a pushicon. It is selected by default and pins the connection bar to the top of the screen. You can deselect it to enable autohiding of the connection bar.

# RDC LOCAL RESOURCES TAB

The Local Resources tab allows you to identify what resources you can bring to your remote session. For example, if you have a printer attached to your system and you want to print a log from the remote session, you can enable the local printer.

Microsoft introduced Easy Print in Windows Server 2008, which makes printer redirection easier with Remote Desktop Sessions and ensures that the client printers are installed in remote sessions. You don't have to install the printer drivers on the server to print from any RDS session.

You can click More to enable additional resources during the remote session. Figure 17-8 shows the Local Resources tab and the additional resources that can be enabled by clicking the More button.

FIGURE 17.8
The Remote Desktop Local Resources tab, with additional options

![](img/41a83208e6906a3732620203b836cea7_926_0.png)

The primary reason why you'll access this tab is to enable or disable local devices and resources. Local printers and the local clipboard are enabled by default. The local clipboard allows you to copy text from your system (such as a script) and paste it into an application in the remote session.

Local drives are not enabled by default, but if you want to copy data from a local drive to the remote system, you can easily select the box. This does represent a security risk, though either the remote system or your local system is infected with malware, connecting the drives makes them accessible by the malware and susceptible to infection.

You can also configure the audio and keyboard settings. Audio settings include the following:

- "Play on this computer" (your local computer)
- "Do not play"
- "Play on remote computer"

If you're a fan of keyboard shortcuts, you may want to change the keyboard settings. The choices are as follows:

- "On this computer"
- "On remote computer"
- "Only when full screen"

# RDC PROGRAMS TAB

The Programs tab allows you to identify what will start when the connection is established. Figure 17.9 shows the Programs tab.

FIGURE 17.9
Remote Desktop Connection Programs tab

![](img/41a83208e6906a3732620203b836cea7_927_0.png)

# RDC EXPERIENCE TAB

The Experience tab allows you to configure the visual effects of the remote session. You can select the desktop background, menu animations, and visual styles. Figure 17.10 shows the Experience tab.

FIGURE 17.10
Remote Desktop Connection Experience tab

![](img/41a83208e6906a3732620203b836cea7_928_0.png)

# CHAPTER 17 REMOTE SERVER ADMINISTRATION

If you're connected in a local LAN, you have high-speed connectivity, so all of the features are available. If you see a decrease in performance, you can deselect some of the features. Additionally, if you connect using a modem at 56kb, you could select the Modem (56 Kbps), and only bitrate caching will be enabled by default.

The selection isn't automatically determined. When it is selected, default features are selected, but you can easily add or remove these features by selecting or deselecting the corresponding check box.

This page also includes the setting "Reconnect if the connection is dropped." This is useful on unreliable links. If the network connection is dropped, RDC will automatically reconnect.

# RDC ADVANCED TAB

The RDC Advanced tab includes two sections: "Server authentication" and "Connect from anywhere."

- Server authentication is a new security feature available when connecting to Windows Server 2008 or later servers. It provides verification that you are connecting to the computer that you intended to, and it helps prevent the unintentional disclosure of confidential information.

You have three choices with server authentication:

- Connect and Don't Warn Me can use this if you are consistently connecting to pre-Windows Server 2008 servers that don't support server authentication. Since these servers don't support server authentication, they will always give warning.
- Warn Me This is the default. It would be used in a mixed environment of Windows Servers and Windows 2003 (or older) servers.
- Do Not Connect If your environment is all Windows Server 2008 servers or newer, this setting will ensure that connections aren't created if the server can't authenticate.

Figure 17.11 shows the Remote Desktop Connection Advanced tab with the Remote Desktop Gateway (RD Gateway) settings.

FIGURE 17.11
Remote Desktop Connection tab and Desktop Gateway settings

![](img/41a83208e6906a3732620203b836cea7_929_0.png)
