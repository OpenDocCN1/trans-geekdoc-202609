# CHAPTER 16 SHARING PRINTERS ON WINDOWS SERVER 2012 R2 NETWORKS

FIGURE 16.24
Adding PushPrinterConnections
to the startup script

![](bbox=[0.378, 0.103, 0.722, 0.396])

If desired, you can -log to the Script Parameters text box to enable logging on computers where it runs. The log is located in the %windir%	emp\ppmMachine.log file for computers or in the %temp%ppmUser.log file for user connections.

+   6. Click OK to close the Add Script dialog, and click OK to close the Startup Properties dialog.

That's a cool feature of the PushPrinterConnections utility that is, if it attempts to start on a Windows 8 or Windows 2012 computer, it automatically detects the environment and exits. You don't have to worry about deploying this in a mixed environment.

# BEING SELECTIVE WITH GPOs

Although these steps will deploy the GPO to all users in the domain, you can be more selective. For example, if you wanted this printer deployed in the Sales OU, you could launch the Group Policy Management console, delete the link for the Deploy Printers GPO, and link the GPO to the Sales OU. As soon as domain refresh Group Policy (or you force it with gpupdate) the printer will be removed for all clients that aren't in the Sales OU.

# Viewing Deployed Printers

You can easily view all deployed printers from the Print Management console by selecting the Deployed Printers container in the Print Management console. This will query Active Directory and show all the printers that are deployed via GPO.

Although you can't deploy additional printers from this view, you can remove the deployment option for printers using this view. Simply select any deployed printer, select Deploy with Group Policy, and remove the deployment option.