# CHAPTER 31 PATCH MANAGEMENT

# FIGURE 31.20
Windows Update Group policy options for customization

![](bbox=[0.318, 0.107, 0.882, 0.493])

The Group Policy update that happens once you have pointed your client to a new WSUS server can take 90 to 120 minutes to do a refresh. The default GPO update takes 90 minutes for a refresh. If you want to test a client, you can do the following:

+   1. From your Windows client to execute a command.

+   2. Type in wauclt.exe /detectnow /reportnow.

This will force the client to go to the WSUS server right away, check its updates, and report to it, basically validating its existence.

To validate and check on any errors or issues with a local client, you can use the system's Event Viewer and open up the following location: \Applications and Services Logs\Microsoft\Windows\Windows Update Client\. Here you will see (as shown in Figure 31.21) the information, errors, and warnings your client system has regarding updates.