Create a Central Access Policy and add the Central Access rule to the policy. When you have finished, create a new GPO and add the new Central Access Policy. Apply the group policy to the appropriate OU so it gets applied to the correct file servers.

If necessary, GPUPDATE on the relevant file servers, and then on a share you want to apply the policy to, select the Central Access Policy.

Classify and secure data without knowing what the data is. Imagine a vast file server array with millions of files. As you know, it has not been common practice to properly classify documents as they are written. Knowing how to approach this and properly classify and secure this data is paramount to an organization.

Master It Across your file servers you have documents that contain sensitive information, including credit card numbers and payroll data. How can you automatically secure this data and ensure only the Accounts and HR departments can access this?

Solution First, create classification rules; the credit cards should use regular expressions to detect credit card numbers. The next set of rules should define strings that are relevant to pay, for example, monthly pay or salary. Configure the options in File Resource Manager to run on a schedule so it retroactively apply to the server. Finally, using Dynamic Access Control, create a new access rule and policy that will target the resources that have been classified by department, and secure them using conditional access to the Accounts and HR departments.

# Chapter 16: Sharing Printers on Windows Server 2012 R2 Networks

Add the Print and Document Services role. Windows Server 2012 R2 servers can be configured as print servers. One of the first steps you must take is to add the Print and Document Services role. There are different steps needed if you're adding the role to a full installation of Windows Server 2012 R2 vs. a Server Core installation.

Master It What tool would you use to add the Print and Document Services role on a full installation of Windows Server 2012 R2 What tool would you use to add the Print and Document Services role on a Server Core installation of Windows Server 2012 R2?

Solution Use Server Manager to add the Print and Document Services role on a full installation of Windows Server 2012 R2. Use the PowerShell command-line utility to add the Print and Document Services role on a Server Core installation of Windows Server 2012 R2. The actual command is as follows:

```
add-WindowsFeature Print-Service
```

Manage printers using the Print Management console. After adding the Print and Documents Services role to the server, you can use the Print Management console to manage other print servers, printers, and print drivers.