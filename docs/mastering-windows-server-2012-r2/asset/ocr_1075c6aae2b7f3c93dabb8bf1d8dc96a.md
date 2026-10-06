# MANAGING PRINTER PROPERTIES

You're not quite finished yet. Even though auditing has been enabled on the printer object, you still need to ensure that auditing is possible in the environment. This is typically done via Group Policy. You can use the Local Security snap-in for a stand-alone server. If you're in a domain, you can create a new Group Policy (GPO) or use an existing GPO such as the Default Domain Policy.

Follow these steps to enable auditing of access in the Default Domain Policy:

+   1. Launch the GPMC by pressing the Windows key and choosing Group Policy Management.

+   2. Browse to your domain, and select Default Domain Policy.

+   3. Right-click Default Domain Policy, and select Edit, as shown in Figure 16.36.

# FIGURE 16.36
Modifying Default Domain Policy using the GPMC

![](bbox=[0.313, 0.337, 0.893, 0.623])

+   4. The Group Policy Management Editor will launch. Browse to the Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Audit Policy node.

+   5. Double-click the "Audit object access" property.

+   6. Select the "Define these policy settings" check box and select the Success check box.

+   7. Your display will show Figure 16.37. Click OK.