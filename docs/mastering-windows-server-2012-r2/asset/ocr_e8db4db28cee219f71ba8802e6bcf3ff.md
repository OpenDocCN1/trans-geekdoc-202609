7. Click OK after all the proper counters have been added.

8. Click Next to go to the Event Trace Providers page.

9. Click Add to browse through event providers, and select AD FS and AD FS Tracing to be added. Click OK.

10. Click Next to add any registry keys for monitoring.

This task is optional; you do not have to monitor any registry keys unless you want to do so.

11. Click Next to continue.

You are prompted for where you want the data to be saved.

12. Accept the default location unless you wish to browse and select a different location to store the data.

13. Click Next to move to the final page of this wizard.

You are asked to confirm the creation of your new data collector set.

14. Keep the defaults and click Finish to complete this wizard.

If you go back into Performance Monitor, you will see that the new data collector set has been successfully created. The new data collector set appears in the console tree under the User Defined node. Right-click the AD FS Performance data collector set, and click Start to begin collecting data. You will notice that a new AD FS report is being generated under the Reports node in the console, as shown in Figure 10.16. You can now use this report to watch the performance of your AD FS infrastructure.

# FIGURE 10.16
Generating an AD FS report using
Performance Monitor

![](bbox=[0.253, 0.589, 0.898, 0.887])