# FIGURE 23.8
Adding a site to Active
Directory Sites and Services

![](bbox=[0.403, 0.103, 0.747, 0.348])

+   3. Create a group that will be used to administer RODCs by following these steps:

+   a. Launch Active Directory Users and Computers by selecting Server Manager ➤ Tools ➤ Active Directory Users and Computers.

+   b. Right-click the Users container, and select New ➤ Group.

+   c. In the New Object - Group dialog box, enter Remote Office Admins as the name of the group. Ensure "Group scope" is set to Global and "Group type" is set to Security. Your display should look similar to Figure 23.9. Click OK.

# FIGURE 23.9
Adding a group for RODC
administration

![](bbox=[0.403, 0.554, 0.747, 0.798])

+   4. Log onto the Windows Server 2012 R2 server that you want to promote to a RODC.
This is a different server than you just used to create a site named RemoteOffice. To continue with the exercise of promoting this server to an RODC we will skip the step-by-step instruction of adding the AD DS role to this server. That step is assumed in this exercise. The same