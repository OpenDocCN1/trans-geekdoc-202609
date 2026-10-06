AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

# RUNNING THE ACTIVE DIRECTORY DOMAIN SERVICES
CONFIGURATION WIZARD

Now that you know what you will encounter, the next step is to add the Active Directory role and then run the Active Directory Domain Services Configuration Wizard. In Windows Server 2012 adding the Active Directory role adds all the necessary binaries and then you can configure Active Directory.

The following steps assume you have a clean installation of Windows Server 2012 without any additional roles installed. If you have installed additional roles, you may have some minor differences.

+   1. Log onto a Windows Server 2012 server using an account with local administrator privileges.
2. Start Server Manager and choose Manage ➤ Add Roles and Features.
3. Review the information on the “Before you begin” page.
4. Select “Role-based or feature-based installation.”
5. Select your destination for the server pool (see Figure 7.8).

![](bbox=[0.181, 0.442, 0.891, 0.793])

+   6. Select the Active Directory Services role and add the recommended features, as Remote Server Administration Tools.
7. On the Features dialog you don't need to select anything.
8. Review the Active Directory Domain Services dialog.