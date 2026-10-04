6. Select Connect The Agent To Azure Log Analytics (OMS), as shown in Figure 2-18, and click Next. The **Azure Log Analytics** page appears, as shown in Figure 2-19.

![](bbox=[0.115, 0.073, 0.735, 0.452])

**FIGURE 2-19** Providing the workspace ID and primary key

7. On this page, you need to type the Workspace ID and the Primary Key that were obtained in step 5 of the previous procedure. Notice that the Primary Key should be entered in the **Workspace Key** field. If this computer is behind a proxy server, you need to click the **Advanced** button and provide the Proxy URL and authentication, if needed. Once you finish filling in these options, click **Next**.

8. On the **Microsoft Update** page, select **Use Microsoft Update for Updates (Recommended)**, and click **Next**.

9. On the **Ready To Install** page, review the summary field and click **Install.**.

10. The **Installing The Microsoft Monitoring Agent** page appears, and the installation proceeds.

11. Once the installation is finished, the **Monitoring Agent configuration Completed Successfully** page appears; click **Finish.**.

You can also perform this installation using the command-line interface (CLI), for that, using the following sample:

```
MMASetup-AMD64.exe /Q:A /R:N /C:/setup.exe /qn ADD_OPINSIGHTS_WORKSPACE=1 OPINSIGHTS_
WORKSPACE_AZURE_CLOUD_TYPE=0 OPINSIGHTS_WORKSPACE_ID=<workspaceid> OPINSIGHTS_
WORKSPACE_KEY=<workspaceprimarykey> AcceptEndUserLicenseAgreement=1
```