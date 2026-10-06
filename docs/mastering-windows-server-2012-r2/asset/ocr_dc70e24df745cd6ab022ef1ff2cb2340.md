# 1176 CHAPTER 23 THE THIRD DC: UNDERSTANDING READ-ONLY DOMAIN CONTROLLERS

FIGURE 23.16
Viewing the Policy Usage tab

![](bbox=[0.41, 0.105, 0.86, 0.41])

+   12. Click Cancel to close the Active Directory search page, click Close to the Advanced Password Replication Policy page, and click OK to close the RODC's properties sheet.

Users or groups added to this page will be to have their passwords replicated or cached onto this RODC. However, if you want a user or group to have their passwords replicated or cached onto any RODC, you need to modify the Allowed RODC Password Replication group.

# Modifying the Allowed List

If you want to allow users to have their passwords replicated or cached onto any RODC instead of a specific RODC, you can modify the properties of the Allowed RODC Password Replication group by following these steps:

+   1. Launch Active Directory Users and Computers.

+   2. Browse to the Users container.

+   3. Right-click the Allowed RODC Password Replication group, and select Properties.

+   4. Select the Members tab.

+   5. Click the Add button.

+   6. Enter Remote Office Admins in the text box.

This is the name of a group created earlier in this chapter. If desired, you can also click the Advanced button and browse to locate a user or group. Your display will look like Figure 23.17. Notice that you can add or remove groups from this page.