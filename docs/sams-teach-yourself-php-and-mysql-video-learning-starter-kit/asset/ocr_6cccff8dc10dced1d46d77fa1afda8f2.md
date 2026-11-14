![](bbox=[0.06, 0.09, 0.56, 0.37])

FIGURE 2.9 Continuing the MySQL server instance configuration.

+   13. The Security Options configuration screen is the most important screen of all. As shown in Figure 2.10, use this configuration screen to set a root password. Enter the password twice to confirm it. Do not check the Enable Root Access from Remote Machines check box unless you really know what you're doing; typically, root connections are allowed only from 1oca1host. Additionally, you can create an anonymous account, but doing so is not recommended for security reasons. After completing the configuration options in this screen, click Next to continue.

+   14. One step remains in the configuration sequence, and that is to click the Execute button to start the process. After the wizard has made it through the various configuration steps, you will see a confirmation screen as shown in Figure 2.11, indicating the configuration file has been created and the MySQL service has been started. Click Finish to close the wizard.

> NOTE: You can manually edit the my.ini file with any text editor. After making changes, you must restart your MySQL server.

The completion of the installation and configuration wizards results in a running MySQL service and a custom my.ini file in the C:\\Program Files\\MySQL\\MySQL Server 5.0 directory.

Now that MySQL has been started, skip to the “Basic Security Guidelines” section later in this chapter. If you had any issues with your installation, check the “Troubleshooting Your Installation” section.