# FIGURE 2.37 Server Selection

![](bbox=[0.296, 0.105, 0.903, 0.443])

+   * VHDs must be running Windows Server 2012 R2.
* VHDs cannot have more than one volume or partition.
* The network shared folder in which the VHD file is stored must grant the following access rights to the computer account of the server that you have selected to mount the VHD file.
* Read/Write access on the File Sharing dialog box.
* Full Control access on the Security tag, File or Folder Properties dialog box.

> ACCESS TIP!
User-only account access is not sufficient for installing a role on a VHD. The share can grant and Write permissions to the Everyone group to allow access to the VHD, but for security reasons, this is not recommended.

For now, click the radio button to select a server from your server pool. Then, from the list of servers highlight the server you wish to use and click Next.
You'll now see a listing of all the available roles you can install (see Figure 2.38). Clicking each one gives you a brief description of that role. The new server we set up is going to be a web server, so select Web Server (IIS).
A pop-up screen appears when you select the Web Server, informing you that additional management tools will need to be installed with your selection (see Figure 2.39). Click the Add Features button, then click Next on the “Select Server roles” screen.