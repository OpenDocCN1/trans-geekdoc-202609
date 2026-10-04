Once you've granted the proper level of permissions, follow the steps below to request access using Security Center dashboard.

+   1. In the **Just-In-Time VM Access** blade, select the **Configured** tab, select the check box next to the VM for which you want remote access, and then click the **Request access** button as shown in Figure 5-7.

![](bbox=[0.118, 0.155, 0.839, 0.342])

**FIGURE 5-7** Requesting access to a VM using Security Center dashboard

+   2. The **Request access** page opens as shown in Figure 5-8. Its contents vary depending on the policy settings assigned to the VM. For added security, toggle off any ports that are not required.

![](bbox=[0.118, 0.455, 0.839, 0.633])

**FIGURE 5-8** Customizing the access request

+   3. Click the **Open Ports** button to commit the changes.

> **NOTE** You can also configure Jit VM request using PowerShell or Security Center API. For an example of how to use PowerShell to request access to a VM access, see http://aka.ms/JITVMRequest.