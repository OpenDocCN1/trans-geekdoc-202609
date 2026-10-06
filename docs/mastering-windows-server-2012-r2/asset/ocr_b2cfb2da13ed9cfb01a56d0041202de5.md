# CHAPTER 8 CREATING AND MANAGER USER ACCOUNTS

You can configure a particular program to run every time a user logs in by selecting "Start the following program at logon". You should enter the command to run that program and also enter a folder that will be the startup folder for that.
The Remote Desktop Connection client allows a user to map their local drives and local printers and choose to print jobs when the server to always go to the computer's default printer. Administrators can forcefully control these options using this tab.

# REMOTE DESKTOP SERVICES OR TERMINAL SERVICES

Windows Server 2012 expanded the functionality in Terminal Services to include virtual desktop infrastructure. Microsoft rebranded Terminal Services in Windows Server 2008 R2 as Remote Desktop Services (RDS). That can be a little confusing if you're reading this chapter and still working with Windows Server 2008. Just know that when we refer to Remote Desktop Services, we are usually talking about Terminal Services on Windows Server 2008/2012.

# SESSIONS TAB

You can see the Sessions tab in Figure 8.13. It also controls how Remote Desktop Services will work for this user. A user's session on a server will remain in a disconnected state if they do not choose to log out. This means that they continue to use resources and their programs continue to execute. More importantly, this means that one of the two available concurrent sessions are used by administrators on servers will be consumed. Forgetful administrators can quickly consume both of these sessions, which will prevent administrators from logging in normally by using the Remote Desktop Connection client. Note that administrators can terminate those sessions by using Remote Desktop Services Manager either or from a remote computer.

Figure 8.13

Local user Sessions tab

![](bbox=[0.315, 0.597, 0.684, 0.93])