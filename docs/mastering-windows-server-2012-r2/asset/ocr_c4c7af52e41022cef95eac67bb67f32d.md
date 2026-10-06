# Deploying Printers via GPO

You can deploy printers using a Group Policy object. If you need to support Windows 8 clients and Windows Server 2012 R2 servers, there are a couple of warnings:

+   - Active Directory must be using a Windows Server 2012 R2 schema version. If you installed the first domain controller (DC) with Windows Server 2012 R2, you have the updated schema. If not, you'll need to run adprep to update the schema. You can find details at http://technet.microsoft.com/library/cb731728.aspx.
- Clients that are not running Windows 8 or Windows Server 2012 R2 must use the PushPrinterConnections.exe tool in a startup script or a login script.

If your domain is completely Windows Server 2012 R2 or the schema has been updated with adprep, you can then follow these steps to deploy printers via GPOs:

+   1. Launch MMC and browse the Printers node for the server.
2. Right-click the printer, and select Deploy with Group Policy.
3. On the Deploy with Group Policy page, click Browse.
4. Click the Create a New Group Policy Object icon, and name Deploy Printers. (If you hover over the icon, a tooltip will appear; you want the middle icon.)
Your display will look similar to Figure 16.21.

FIGURE 16.21
Creating a Group Policy object

![](bbox=[0.323, 0.545, 0.872, 0.843])