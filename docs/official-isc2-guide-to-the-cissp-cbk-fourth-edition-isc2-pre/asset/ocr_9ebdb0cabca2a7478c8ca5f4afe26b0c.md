# Step 1 – Raise the Domain Functional Level

In the following procedure, you will raise the domain functional level of the target domain to Windows Server 2008 or higher. A domain functional level of Windows Server 2008 or higher is required to enable fine-grained password policies.

To Raise the Domain Functional Level

+   1. Right click the Windows PowerShell icon, click Run as Administrator, and type dsac.exe to open ADAC.
+   2. Click Manage, click Add Navigation Nodes, and select the appropriate target domain in the Add Navigation Nodes dialog box and then click OK.
+   3. Click the target domain in the left navigation pane and in the Tasks pane, click Raise the domain functional level. Select a forest functional level that is at least Windows Server 2008 or higher and then click OK.

![](bbox=[0.02, 0.42, 0.06, 0.48])

# Windows PowerShell Equivalent Commands

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

```
Set-ADDomainMode -Identity isc2.org -DomainMode 3
```

# Step 2 – Create Test Users, Groups, and Organizational Units

To create the test users and group need for this step, follow the procedures located here: Step 3 – Create a New Fine-Grained Password Policy (you do not need to create the OU to demonstrate fine-grained password policy).

# Step 3 – Create a New Fine-Grained Password Policy

In the following procedure, you will create a new fine-grained password policy using the UI in ADAC.

To Create a New Fine-Grained Password Policy

+   1. Right click the Windows PowerShell icon, click Run as Administrator, and type dsac.exe to open ADAC.
+   2. Click Manage, click Add Navigation Nodes, and select the appropriate target domain in the Add Navigation Nodes dialog box and then click OK.
+   3. In the ADAC navigation pane, open the System container and then click Password Settings Container.
+   4. In the Tasks pane, click New, and then click Password Settings.