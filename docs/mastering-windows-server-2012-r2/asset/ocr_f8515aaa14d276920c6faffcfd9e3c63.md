# 514 CHAPTER 9 GROUP POLICY: AD GAUNTLET AND ACTIVE DIRECTORY DELEGATION

linked. Then you must view the ACLs and WMI information to see whether there's any filtering and also check out the Disabled, Block Inheritance, and Enforcement options. Don't forget the item-level targeting, which can get granular, confusing to evaluate by hand. Finally, you need to view the settings of the policies in question before you get to the bottom of things. You will need to take notes. Personally, we prefer the RSOP tool.

The RSOP tool is easily launched by typing rsop.msc at the command prompt. When it is launched, you will see it working, determining the result of policy that has been applied on the computer you are running in or the user that is logged in at the time the tool is run.

The result is a window that is similar to that shown in the GPME, as shown in Figure 9.32.

# Figure 9-32 rsop.msc generates a real-time view of the policy settings that have been applied.

![](bbox=[0.216, 0.311, 0.875, 0.636])

Here are a few things to note about using the rsop.msc tool:

+   - The tool provides only the applied GPOs and the settings from those GPOs.
- The tool provides a view of which GPO each setting coming from.

# Group Policy Results Using the GPMC

Inside the GPMC is a tool that is similar to that of the localized version of the RSOP, but it allows you to query any computer and on the network to get the RSOP. Imagine that a user calls to indicate that they can't access a website that is required for their job. You could visit their desk, but that would only take time, when you are sure that they are getting their Internet Explorer proxy settings from a GPO. So, instead, follow these steps: