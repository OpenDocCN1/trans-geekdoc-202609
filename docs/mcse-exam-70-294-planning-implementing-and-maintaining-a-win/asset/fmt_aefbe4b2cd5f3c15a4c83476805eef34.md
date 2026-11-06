
## Profile Tab

The Profile tab is also used to configure elements of the user’s account, relating to profiles, logon scripts, and home folders. Roaming profiles can be used to provide consistency across the network, by ensuring that a user has the same desktop environment, application settings, drive mappings, and personal data regardless of which computer he or she uses on the network. The Profile path field on this tab is used to specify the path to the user’s profile. Similarly, logon scripts are also used to apply settings to a user’s account, by running a script when the user logs on to the network. The Logon script field is used to set where this script is located, so it will automatically run each time the user logs on to this account. Through these, the user’s environment is configured each time he or she logs on to a DC.

![note](images/note.jpg)Note

The Logon script field on this tab is a hold over from Windows NT days. Group Policy allows you to specify multiple logon, logoff, startup, and shutdown scripts. However, if the computers that your users are logging on from does not support Group Policy, this field comes in handy to ensure that they can still get a logon script applied to them. Windows 2000 and later computers are capable of using Group Policy.

Finally, as shown in [Figure 2.16](#B9781931836944500088.xhtml#f0085), the Home folder section of this tab is used to specify the location of a home directory that will contain the user’s personal files. The Local path text box is used to specify a path to the directory on the local system. Alternatively, you can specify a network location by using the Connect drop-down box to specify a drive letter that the path will be mapped to, and then enter a UNC path to the directory in the To text box.

![Figure 2.16 Profile Tab of User’s Properties](images/B9781931836944500088/f02-16-9781931836944.jpg)

Figure 2.16 Profile Tab of User’s Properties

### Terminal Services Tabs

Terminal Services allows users to access applications that are run on the server. Rather than running as independent computers, the clients that access Terminal Services act as dumb terminals. Throughout their session with the server, users run an environment that allows them to view and interact with programs that appear to run on the local computer but are actually running on the Terminal Services server located on the network.

The Properties dialog box of a user provides four tabs that specifically deal with Terminal Services: Environment, Sessions, Remote Control, and Terminal Services Profile. As seen in [Figure 2.17](#B9781931836944500088.xhtml#f0090), the Environment tab is used to configure settings for Terminal Service’s startup environment. By default, users receive a Windows Server 2003 desktop when connecting using Terminal Services. The Starting program section contains fields for specifying a particular program to run when logging on to Terminal Services. If this option is enabled, users will receive the program instead of a desktop. When the Start the following program at logon check box is selected, you can enter the path and executable name for the program.

![Figure 2.17 Environment Tab of User’s Properties](images/B9781931836944500088/f02-17-9781931836944.jpg)

Figure 2.17 Environment Tab of User’s Properties

The Client devices section also allows you to configure how devices on the computer you’re working on will be dealt with. The check boxes you can check to enable these settings are:

■ Connect client drives at logon This check box causes drive letters to be mapped to local client drives in the user’s Terminal Services session. This enables these local drives to be accessed from the session. Remember, when you are working in a session, you are actually working on the server, not your client. Therefore, the drives you seen in Explorer are the drives on the server, not the client. When this box is checked, you see both.

■ Connect client printers at logon This check box causes printers that are configured on the client computer to be connected and available while you are working in a Terminal Services session.

■ Default to main client printer This check box causes the default printer on your client computer to be the default printer in your Terminal Services session.

In addition to the settings on the Environment tab, the Sessions tab is also used for configuring Terminal Services. As seen in [Figure 2.18](#B9781931836944500088.xhtml#f0095), this tab includes numerous settings for configuring timeout and reconnection settings for Terminal Services sessions:

![Figure 2.18 Sessions Tab of User’s Properties](images/B9781931836944500088/f02-18-9781931836944.jpg)

Figure 2.18 Sessions Tab of User’s Properties

■ End a disconnected session This drop-down box allows you to choose how long a disconnected session should remain on the server. If set to Never, which is the default setting, a disconnected session will remain on the server indefinitely. If set to a specific time limit, the session will be terminated on the server when this time limit is reached.

■ Active session limit This drop-down box is used to specify how long a user’s session should remain active. The default setting is Never, meaning that the user’s session can remain active indefinitely. If set to a limit by selecting a time from the drop-down list, the user’s session will remain active until that time is reached. At this time, the user is either disconnected from the session or the session is terminated, depending on what is set for the When a session limit is reached or connection is broken option.

■ Idle session limit This drop-down box controls how long a user can remain connected without any activity before the session ends or the user is disconnected from it, depending on what is set for the When a session limit is reached or connection is broken option.

■ When a session limit is reached or connection is broken This option button allows you to set what will happen when either of these situations occurs. You can choose either Disconnect from session or End session.

■ Allow reconnection This option button allows you to control how a user can reconnect to a disconnected session. You can choose to either reconnect From any client or From originating client only.

![note](images/note.jpg)Note

There are two ways to end a Terminal Services session. The first it is to log off. This completely destroys the session that you were using on the server and frees up the resources it was consuming. The second option is to disconnect. This simply breaks the communication from your client to the Terminal Services server. It does not terminate your session, which means that it continues to consume resources on the server. When you reconnect to a disconnected session, it appears exactly as it did when you disconnected from it.

The Remote Control tab allows you to configure remote control settings for the user, which enables others to take over a session. By taking over the computer, the other person can then perform actions on the remote computer, enabling that person to perform various actions and show the user how to do certain tasks. As shown in [Figure 2.19](#B9781931836944500088.xhtml#f0100), the fields available to configure these settings are:

![Figure 2.19 Remote Control Tab of User’s Properties](images/B9781931836944500088/f02-19-9781931836944.jpg)

Figure 2.19 Remote Control Tab of User’s Properties

■ Enable remote control This check box determines whether others can control or view a user’s session. This turns on or off remote control for a session belonging to a user.

■ Require user’s permission This check box determines whether the user needs to give permission to allow another user to control or view a session.
