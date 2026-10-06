
# FIGURE 25.29
The Global Resource Property List screen

![](img/41a83208e6906a3732620203b836cea7_816_0.png)

Add our resource property to the Global Resource Property List.

- 4. Click the Add button.
5. From the Select Resource Properties window, navigate to department_contoso and click the arrows pointing to the right to add it, as shown in Figure 15.30.

# FIGURE 25.30
Adding a new resource property to the Global Resource Property List

![](img/41a83208e6906a3732620203b836cea7_816_1.png)

- 6. Click OK, browse the resource property list, and ensure that your resource property is now listed. Click OK on the main window to close it.

You have created a new claim type, a referenced resource property, and added it to the Global Resource Property List. Next, you will need to create a Central Access Rule:

# CHAPTER 15 DYNAMIC ACCESS CONTROL: FILE SHARES, REIMAGINED

1. From the main Dynamic Access Control window again, click Central Access Rules, and in the Tasks select New > Central access rule.

2. In the Create Access Rule window, enter Contoso_Demo_rule in the Name field, as shown in Figure 15.31.

# FIGURE 15.31
Central Access Rule screen

![](img/41a83208e6906a3732620203b836cea7_817_0.png)

Under Target Resources, you can be more selective if you need to the resources you need to control all of. For example, leave it as All Resources so that you can set read-access for all authenticated users to all resources.

3. Navigate to Permissions, and click “Use following permissions as current permissions,” as shown in Figure 15.32.

# FIGURE 15.32
Adding permissions for a central access rule

![](img/41a83208e6906a3732620203b836cea7_817_1.png)

- 4. Click the Edit button.

This will open the Advanced Security Settings for Permissions window, as shown in Figure 15.33.

# FIGURE 15.33 Advanced Security Settings for Permissions screen

![](img/41a83208e6906a3732620203b836cea7_818_0.png)

- 5. Click Add.

This will open the Permission Entry for Permissions window.

- 6. Click Select a Principle, and type in Authenticated Users; leave the Read and Read Execute permissions as is; see Figure 15.34.

# FIGURE 15.34
Permission Entry for Permissions screen

![](img/41a83208e6906a3732620203b836cea7_818_1.png)

Next, as you did earlier in this chapter, you are going to add conditions.

- 1. Click "Add a condition."

This will bring up options for you to configure.

- 2. In the first box select User, in the second box select department_contoso, and in the final box select Accounts.

Notice that the drop-down list in the final box contains the options that you created

- 3. Repeat this step for the remaining departments. Use the “And” condition, as shown in Figure 15.35.

# FIGURE 15.35
Adding conditions to a Central Access rule

![](img/41a83208e6906a3732620203b836cea7_819_0.png)

- 4. Click OK when you've finished adding conditions, and click OK twice to close all windows.

Great! You are nearly finished, now you need to create a Central Access Policy that you will then use to deploy to your file servers:

- 5. From the main Dynamic Access Control window, select Central Access Policies, and in the Tasks menu select Test CAP ➤ Central Access Policy.

- 6. Enter Contoso Test CAP in the Name field when the new Create Central Access Policy window opens, as shown in Figure 15.36.

- 7. You need to add all the rule you created, so click Add under Member Central Access Rules.

This will open the Add Central Access Rules window.

- 8. Select Contoso_Demo_rule, click the arrows pointing to the right, and click OK, as shown in Figure 15.37.

- 9. Click OK to finish creating the policy.

# FIGURE 15.36
Create Central Access Policy window

![](img/41a83208e6906a3732620203b836cea7_820_0.png)

# FIGURE 15.37
Adding a Central Access rule to a Central Access Policy

![](img/41a83208e6906a3732620203b836cea7_820_1.png)

# APPLY DYNAMIC ACCESS CONTROL POLICIES

You have created a Dynamic Access Control policy, but you need to apply it to your servers to be effective. This is done via Group Policy. By deploying it via Group Policy you have flexibility to start targeting specific groups and roll it out as necessary. In Chapter 9 you have become familiar with Group Policy; if not, skip back now and read it. You need to use the Group Policy Management console to create a new group policy to roll out your Central Access Policy. To recap, the Group Policy Management console is located in Server Manager  Tools.

In our example, Group Policy Management console is located on our domain controller. We assume at this point that you are familiar with this. You are now going to create a group policy under the root level of the domain contoso. Here is some best practice advice:

- Create the necessary groups to properly target the file servers.
- Create organizational units in a structured fashion and assign the group policy to the desired organizational unit at the root domain.

Let's begin:

1. Right-click contoso, as shown in Figure 15.38, and Create a GPO in this domain and Link it.

![](img/41a83208e6906a3732620203b836cea7_821_0.png)

- 2. In the New GPO window, give it a name. In our scenario we are using CAP-Contoso-Demo.

- 3. Click OK, as shown in Figure 15.39. It should now appear in the list under contoso.

- 4. Click the group policy, and under Security Filtering on the Scope tab of the Group Management screen, as shown in Figure 15.40, select Authenticated Users and click Remove.

# FIGURE 15.39
New GPO window

![](img/41a83208e6906a3732620203b836cea7_822_0.png)

# FIGURE 15.40
Removing Authenticated Users

![](img/41a83208e6906a3732620203b836cea7_822_1.png)

- 5. When prompted “Do you want to remove this delegation?” click OK.
6. Click Add.

This will bring up the Select User, Computer, or Group window.

- 7. Click Object Types button and select Computer, since it is not checked by default, and click OK.

- 8. In the “Enter object to select” field, type in the name of the file server you want to apply it to. In the example, we are using contoso1.

- 9. Click Check Names, ensure that it resolves, and click OK. See Figure 15.41.

# CHAPTER 15 DYNAMIC ACCESS CONTROL: FILE SHARES, REIMAGINED

# FIGURE 15.41
Ensuring the name resolves in the search window

![](img/41a83208e6906a3732620203b836cea7_823_0.png)

In the Security Filtering, you will see the full name of the computer account listed; this simply means that the policy will apply only to this computer, even though it is located at the root of the domain. See Figure 15.42.

# FIGURE 15.42
Computer account added to Security Filtering field

![](img/41a83208e6906a3732620203b836cea7_823_1.png)

Next, you need to edit this group policy.

- 10. Right-click the CAP-Contoso-Demo group policy and click Edit. This will open the Group Policy Management Editor window.
11. Navigate to Computer Configuration Policies > Windows Settings > Security Settings > File System > Central Access Policy, as shown in Figure 15.43. Currently, nothing is configured.
12. Right-click Central Access Policy, and click Manage Central Access Policies, as shown in Figure 15.44.

# FIGURE 15.43
Central Access Policy Location in Group Policy Management Editor

![](img/41a83208e6906a3732620203b836cea7_824_0.png)

# FIGURE 15.44
Manage Central Access Policies

![](img/41a83208e6906a3732620203b836cea7_824_1.png)

The Central Access Policies Configuration window will open, and you will see the Central Access Policies that you configured earlier.

- 13. Select the policy that you want to apply, and click Add. In this example, we are choosing contoso Test CAP, as shown in Figure 15.45.

- 14. Click OK.

# CHAPTER 15 DYNAMIC ACCESS CONTROL: FILE SHARES, REIMAGINED

# FIGURE 15.45
Selecting Central Access Policies to apply

![](img/41a83208e6906a3732620203b836cea7_825_0.png)

- 15. Next, scroll down in the Group Policy Management Editor to Advanced Audit Policy Configuration > Audit Policies > Object Access, and double-click Central Access Policy Staging, as shown in Figure 15.46.

# FIGURE 15.46
Enabling Central Access Policy Staging

![](img/41a83208e6906a3732620203b836cea7_825_1.png)
