
# RD GATEWAY—REQUIRED SERVICES AND FEATURES

RD Gateway requires the following additional role services and features on the Windows Server 2012 R2 server where it is hosted (which we had you install earlier in this section):

- Web Server (IIS) role:
    - Management Tools feature (to manage IIS)
    - Web Server services (support for HTML websites and ASP.NET)
- Network Policy and Access Services role: Network Policy Server services
- RPC over HTTP proxy features
- Remote Server Administration Tools feature

When you add the RD Gateway role, the wizard will prompt you to automatically install all the required roles, services, and features. You won't need to install them individually. However, if they are already installed, the wizard will recognize that they are active.

# RD GATEWAY—REQUIRED POLICIES

Before users connect through RD Gateway, you must have at least two policies:

**RD Connection Authorization Policy (RD CAP)** RD CAP specifies the users who can connect to the RD Gateway server. For example, you may choose to grant anyone in the Administrators group of the RD Gateway server permission to connect, or create a global security group (as G RD Gateway Users) specifically for this purpose. You will then place any users for whom you want to grant connection access into this new group.

**RD Resource Allocation Policy (RD RAP)** RD RAP specifies the resources that users can access once they connect. For example, you may be creating this policy so that administrators can remotely administer a specific server. You would identify the server in RAP. Administrators could connect to this server but not to any servers via the RD Gateway server.

It's also possible to configure RD RAP so that users can connect to any computer on the network without any restrictions.

# ENABLING REMOTE DESKTOP GATEWAY

Follow these steps to enable the Remote Desktop Gateway role service on a Windows Server 2012 R2 server. These steps will also lead you through adding the required roles, services, and features, as well as RD CAP and RD RAP.

1. Launch Server Manager from your taskbar.
2. Select Roles, and click Add Roles.
3. Review the information on the “Before you begin” page, and click Next.
4. Select the Role-Based Installation radio button and click Next.
5. Select the server to install it, and click Next.
6. Expand the Remote Desktop Services role on the Select Server Roles page, and select Remote Desktop Gateway. Click Next.
7. You will be prompted additional features may need to be installed. Click Add Features.
8. When the pop-up closes, click Next.
9. Click Next again on the features page.
10. Review the information on the Network Policy and Access Services page, and click Next.
11. Network Policy should be a selected role service; click Next.
12. Review the Confirmation page, select the check box to restart the server if needed, click Install.

After a few minutes and a reboot, you should have RD Gateway installed on your server. To access it you can hit your Windows key. You will see a new Metro-style button called Remote Desktop Gateway, as shown in Figure 17.26.

# FIGURE 17.26
Remote Desktop Gateway

![](img/41a83208e6906a3732620203b836cea7_944_0.png)

Once you get inside the RD Gateway Manager, you can see that it's very similar to the Group Policy Management. You can manage all aspects of RD Gateway using this tool. On the left pane you will see your server with two folders: Policies and Monitoring. If you click the server you will see current connection information and outstanding configurations, as shown in Figure 17.27. As you can see in Figure 17.27, we still need to configure the Gateway certificate.

1. Click the "View" or modify properties. The Choose Certificate for SSL page will appear. You can install an existing certificate, create a self-signed certificate, or import a certificate. You can purchase a certificate from an external CA or obtain one from an internal CA.
2. For these steps, choose the option "Create a self-signed certificate for SSL." Click "Create."
3. In Figure 17.28 we see that we can create our self-signed certificate using the defaults. Click OK.

# FIGURE 17.27
Gateway connection information

![](img/41a83208e6906a3732620203b836cea7_945_0.png)

# FIGURE 17.28
Create your self-signed certificate.

![](img/41a83208e6906a3732620203b836cea7_945_1.png)

You can see in Figure 17.29 that our certificate is installed successfully.

# FIGURE 17.29
Certificate installed properly

![](img/41a83208e6906a3732620203b836cea7_946_0.png)

Figure 17.30 shows that we still have a few items to add: the first one is Remote Desktop Connection Policy, and the other is Remote Desktop Resource Policies. For those familiar with Windows Server 2008 R2, you may have noticed that all of these, starting with the certificate, are configured during the installation of the Remote Desktop Services. In Windows Server 2012 R2 they get configured in Gateway Manager.

# FIGURE 17.30
Requirements needed to complete gateway configuration

![](img/41a83208e6906a3732620203b836cea7_946_1.png)

# OBTAINING A CERTIFICATE FROM A CA

Self-signed certificates are useful for testing, but it is not recommended to use a self-signed certificate in a production environment. Instead, you should obtain a certificate from a certificate authority. Since a certificate used by RD Gateway for administration will be used only by administrators, you can use an internal CA to create a certificate instead of purchasing a certificate from an external CA.

1. Let’s configure RD CAP by selecting the link “Create connection policy,” shown in Figure 17.30.
2. Under the General tab of the New RD CAP dialog box, enter a policy name, as shown in Figure 17.31.

![](img/41a83208e6906a3732620203b836cea7_947_0.png)

Under the Requirements tab, you can add permissions for groups and client computer membership. As you can see in Figure 17.32, we added Remote Management Users.

The next tab is Device Redirection, allowing or denying the use of these devices during the session.

# FIGURE 17.32
Requirements tab

![](img/41a83208e6906a3732620203b836cea7_948_0.png)

3. As shown in Figure 17.33, select the default to allow all devices on the client.

# FIGURE 17.33
Device Redirection tab

![](img/41a83208e6906a3732620203b836cea7_948_1.png)

4. The last tab is the Timeouts tab. Set your session timeouts as desired (see Figure 17.34).

# FIGURE 17.34
Timeouts tab

![](img/41a83208e6906a3732620203b836cea7_949_0.png)

5. Click OK.

Your newly created policy will now show up in the Connection Authorization Policy window. You will also notice that the requirement on the Gateway property has been fulfilled. As we mentioned earlier, we also need to set the Remote Desktop Resource Authorization Policy. This will fulfill the last requirement to setting up the Remote Desktop Gateway. This is very similar to the procedure you just completed for RD CAP.

1. On the Gateway summary page for the server, click the link Create Resource Authorization Policy. This will open the properties for the RAP.
2. Under the General tab, add a policy name and policy description, as we have done in Figure 17.35.
3. The User Groups tab is for adding the group permission for this policy. As shown in Figure 17.36, add your Remote Management Users group.

# FIGURE 17.35
Add a policy name and description.

![](img/41a83208e6906a3732620203b836cea7_950_0.png)

# FIGURE 17.36
Add a group to the User Groups tab.

![](img/41a83208e6906a3732620203b836cea7_950_1.png)
