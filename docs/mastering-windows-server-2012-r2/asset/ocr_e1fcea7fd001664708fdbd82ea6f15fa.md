Locked or compromised then it would affect multiple services and applications instead of just one. Since this is our first time through the configuration wizard, go ahead and create a new dedicated service account for AD FS.

7. Click Next to continue to the Specific Database page. As we mentioned earlier in the chapter, AD FS can use either Windows Internal Database or a SQL Server Database to store configuration data. For this exercise we will use WI. If by chance you are running through this configuration wizard on server that was previously configured for AD FS, you may have to overwrite that existing database. The nice part is that the wizard automatically detects the previous installation and all you have to do is check the box to Overwrite existing AD FS configuration data on the Confirm Overwrite page and continue as normal through the rest of the wizard.

8. Click Next to go to the Review Options page as shown in Figure 10.7.

![](bbox=[0.141, 0.357, 0.858, 0.706])

9. Review the information listed carefully and make sure that all of your choices are exactly like you want. Now would be the time to make any changes to your configuration options.

The configuration wizard will automatically create the additional signing and token-encryption certificates that you will need for this deployment during the installation. also configures the Windows Internal Database with the network service account, provided from the server, with access to the database. In addition to these settings, a browser sign-in will be deployed to the virtual directory under the default website in IIS.