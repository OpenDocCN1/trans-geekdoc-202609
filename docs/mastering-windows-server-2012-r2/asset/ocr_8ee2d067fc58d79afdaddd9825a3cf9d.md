# CHAPTER 23 THE THIRD DC: UNDERSTANDING READ-ONLY DOMAIN CONTROLLERS

You will notice that the required Domain field is blank.

+   6. Click the Select button and a Windows Security box will appear, requesting credentials for the deployment operation.

+   7. Enter the username and password of a user who is in the group that has been delegated permissions to complete the installation, and click Next to continue.

The Domain Controller Options page will display a notification that you precreated RODC has been created that matches your history. The wizard defaults to the configuration option of “Use existing RODC account,” as shown in Figure 23.21.

FIGURE 23.21 The AD DS Configuration Wizard detected the prestaged RODC.

![](bbox=[0.315, 0.315, 0.858, 0.644])

+   8. Keep the default and click Next to continue.

+   9. As discussed in earlier exercises, through the AD DS Configuration Wizard, making the appropriate selections on each page.

Promoting the RODC may take several minutes to run and requires a reboot upon completion. You can select the “Reboot on completion” check to allow it to reboot automatically. After the installation has completed successfully, the RODC will be fully promoted to the domain and ready for use.

# ## DNS on the RODC

It is strongly recommended that you install the DNS service on the RODC. In the steps used in this chapter, DNS was selected each time. It has very little overhead and provides significant gains.