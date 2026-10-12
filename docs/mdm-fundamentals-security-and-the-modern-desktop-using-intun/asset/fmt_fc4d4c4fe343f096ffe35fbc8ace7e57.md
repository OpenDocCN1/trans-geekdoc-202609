
The full docs on Offline Domain Join can be found here (but you won’t really need them for what we’re going to do):

`https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd392267(v=ws.10)`

The takeaway here is that Intune is going to do all the hard work to make the reservation and the ODJ blob for you, then download it and apply it on a target machine, thus joining a computer to Active Directory automatically.

But there is a catch with Intune. Hang tight for the reveal in a moment.

### Preparing Active Directory for Hybrid Azure AD Join

There’s a little pregame setup involved in Hybrid Azure AD Join.

One of the optional steps in [Chapter 2](#c02.xhtml) was to set up AAD synchronization using the Azure AD Connect tool. If you didn’t do this, and want to get your on-prem AD married to your Azure AD, then you can flip back to [Chapter 2](#c02.xhtml) and see the section titled “Syncing Your On-Prem AD to Azure AD Automatically.”

Then, after that, you need to first tell your on-prem Active Directory that it’s A-OK for some *computer* on your network to add *other* *computers* to your domain.

Your on-prem Active Directory doesn’t usually work like that; *people* usually do the joining of computers to your Active Directory. But you can gently explain to Active Directory that, yes, it really is okay for another *computer* to create computer records and do the joining of other computers.

Really Active Directory, it’s going to be okay.

To teach Active Directory about this, you’ll delegate the ability to create computer objects as well as manage their properties and permissions. In most Active Directories, the place where new computers magically show up when joined is the Computers container (and yes, I did mean container…it is not an OU).

This is typically where you’d start your delegation. It is possible that this is not your default location (this is changeable via the old and crusty (but it still works) command `redircmp`). If you’re unsure if the Computers folder is where computers appear when you join one to Active Directory, then just join one. Then find it. Once you know your default location, right-click over it and select Delegate Control as seen in [Figure 8.51](#c08.xhtml#figure8-51).

![Figure 8.51 Delegate Control over your known default location. If it’s not the Computers folder, then be sure to do it on your redirected location.](images/c08f051.jpg)

[**Figure 8.51**](#c08.xhtml#figureanchor8-51) Delegate Control over your known default location. If it’s not the Computers folder, then be sure to do it on your redirected location.

Then once inside the Delegation of Control Wizard, you need to change the view such that it lets you look for computers. (Again, this is unusual for Active Directory, so the default is that it doesn’t show you computers.) In the screen shown in [Figure 8.52](#c08.xhtml#figure8-52), you’ll click Object Types and then click to check on Computers.

![Figure 8.52 Enable Computers as an Object Type.](images/c08f052.jpg)

[**Figure 8.52**](#c08.xhtml#figureanchor8-52) Enable Computers as an Object Type.

Then, as seen in [Figure 8.53](#c08.xhtml#figure8-53), search for the computer name where you plan to install the Intune Connector for Active Directory. This can be a Domain Controller or member server within Active Directory. I’m picking my DC.

![Figure 8.53 Specify the computer where you plan to install the Intune Connector for Active Directory.](images/c08f053.jpg)

[**Figure 8.53**](#c08.xhtml#figureanchor8-53) Specify the computer where you plan to install the Intune Connector for Active Directory.

Then, in the Delegation of Control Wizard, select “Computer objects” as seen in [Figure 8.54](#c08.xhtml#figure8-54) along with “Create selected objects in this folder” and “Delete selected objects in this folder” and click Next.

![Figure 8.54 Specify that the computer can perform the selected delegated items.](images/c08f054.jpg)

[**Figure 8.54**](#c08.xhtml#figureanchor8-54) Specify that the computer can perform the selected delegated items.

Last, you’ll specify that the computer can manipulate the Permissions. In the next page of the wizard, select Full Control as seen in [Figure 8.55](#c08.xhtml#figure8-55). This will automatically check every other box.

![Figure 8.55 Select Full Control on the Permission page.](images/c08f055.jpg)

[**Figure 8.55**](#c08.xhtml#figureanchor8-55) Select Full Control on the Permission page.

The final page is a review from the wizard. Click Finish and you’re all set.

### Installing the Intune Connector for Active Directory

Now, let’s flip back to Intune. This is where you’re going to find and then download the Intune Connector for Active Directory. Head over to Intune ➢ Device Enrollment ➢ Windows Enrollment ➢ Intune Connector for Active Directory. Then click the link in Step 2 as seen in [Figure 8.56](#c08.xhtml#figure8-56).

![Figure 8.56 Downloading the Intune Connector for Active Directory](images/c08f056.jpg)

[**Figure 8.56**](#c08.xhtml#figureanchor8-56) Downloading the Intune Connector for Active Directory

Back on your on-prem server, it’s time to install it. You can do this upon a DC or a member server. It’s a simple MSI and doesn’t take very long. You can see the MSI and opening screen in [Figure 8.57](#c08.xhtml#figure8-57).

![Figure 8.57 Installing the Intune Connector for Active Directory](images/c08f057.jpg)

[**Figure 8.57**](#c08.xhtml#figureanchor8-57) Installing the Intune Connector for Active Directory

After clicking through the installation, you should see an “Installation Successfully Completed” message (not shown) and a “Configure now” button (also not shown). Also, if needed there is a Start Menu item if you need to re-access it.

Simply click the Sign In button (seen in [Figure 8.58](#c08.xhtml#figure8-58)), and then give it the credentials for the main Global Azure Administrator, Frank Rizzo (who also needs an Intune license for this to work). When it’s all done, you should see what’s seen in [Figure 8.58](#c08.xhtml#figure8-58).

![Figure 8.58 After you give the Global Admin’s credentials, you will get a success message from the connector.](images/c08f058.jpg)

[**Figure 8.58**](#c08.xhtml#figureanchor8-58) After you give the Global Admin’s credentials, you will get a success message from the connector.

At this point we’re almost ready to try this out.

### Verifying the Installation of the Intune Connector for Active Directory

Once you’ve installed the Intune Connector, as we just did, you can take a moment to look inside Windows’s Services and see that it’s present and running. It’s called the Intune ODJConnector Service and can be seen in [Figure 8.59](#c08.xhtml#figure8-59).

![Figure 8.59 Inspecting the Intune ODJConnector Service](images/c08f059.jpg)

[**Figure 8.59**](#c08.xhtml#figureanchor8-59) Inspecting the Intune ODJConnector Service

You can also see logs for the ODJConnector Service on this same machine. You would look in Windows’s Event Viewer ➢ Applications and Services Logs then ODJ Connector Service as seen in [Figure 8.60](#c08.xhtml#figure8-60).

You can see interesting event logs from the ODJ Connector Service, like the one in [Figure 8.61](#c08.xhtml#figure8-61), in case you need to do any troubleshooting.

Finally, back in Intune, you should (eventually) see the computer you’re using notated as performing a sync, as seen in [Figure 8.62](#c08.xhtml#figure8-62). This took about 10 minutes for me, and the Refresh button didn’t actually refresh it for me. I had to press F5 to refresh to the actual page.

![Figure 8.60 Finding the ODJ Service event log](images/c08f060.jpg)

[**Figure 8.60**](#c08.xhtml#figureanchor8-60) Finding the ODJ Service event log

![Figure 8.61 An event log item from the ODJ Connector Service](images/c08f061.jpg)

[**Figure 8.61**](#c08.xhtml#figureanchor8-61) An event log item from the ODJ Connector Service
