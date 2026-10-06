
# FIGURE 2-45

PowerShell
Get-WindowsFeature

![](img/41a83208e6906a3732620203b836cea7_100_0.png)

Let's verify the installation. Run PowerShell again with the Get-WindowsFeature cmdlet to check the results, as in Figure 2.46:

```
PS C:\Windows\Administrator> Get-WindowsFeature
```

# FIGURE 2.46

Checking our
installed role

![](img/41a83208e6906a3732620203b836cea7_100_1.png)

# CHAPTER 2 INSTALLING AND UPGRADING WINDOWS SERVER 2012 R2

The roles and role services that you requested designated with an X, which means that they are installed. You can also see that the required features for the FTP Service are also installed. You can ensure that the results are identical to those obtained using the GUI by launching Server Manager.

Anyone who was a little scared of command-line administration might be getting a little intrigued.

If you want a text report on your server configuration, then you could run just one command. It will export the report to a file called C:\InstalledFeatures.txt.

```
PS C:\Administrator> get-windowsfeature C:\InstalledFeatures.txt
```

A nice feature is that you can check out what would happen if you ran the command without actually running it. You can do that by adding the -whatif flag:

```
Add-WindowsFeature -name
```

If you're going to add the File-Services role and the FS-Resource-Manager role service, here's what would happen if you ran that command:

```
PS C:\Users\Administrator> add-windowsfeature File-Services,FS-Resource-Manager -whatif
```

What if: Checking if running in 'WhatIf' Mode.
What if: Performing operation 'Add-WindowsFeature' on Target "[File Services Resource Manager".
What if: Performing operation 'Add-WindowsFeature' on Target "[File Services File Server".
What if: This server may need to be restarted after the installation completes.

Nothing has been changed on the servers thanks to the -whatif flag. Notice that you might need to reboot? It is good to know that this command execution, you'll need to do a reboot. This will allow you to plan for the reboot and restart any of the services hosted by this machine.

# Installing Roles on Multiple Servers Using Scripts in PowerShell

Imagine you were setting up many more roles, role services, and features. You could bundle everything into this one script and run it. With that command-line option in PowerShell, you could automatically configure hundreds or thousands of servers like Microsoft System Center Configuration Manager. You should now understand the power of PowerShell. You could easily save hours of work on your server deployments and configuration projects.

Before you go too far into setting up a script installation, you need to first check if you are allowed to run scripts. Open PowerShell and run the following cmdlet:

```
PS C:\Users\Administrator> get-executionpolicy
Restricted
```

# USING SERVER MANAGER TO CONFIGURE YOUR SERVERS

This command shows that scripts are disabled on our server. That's the default in PowerShell. To run the script if scripts are disabled on your server, you'll have to run this command:

```
PS C:\Users\Administrator> set-executionpolicy unrestricted
```

# Execution Policy Change

The execution policy protects you from scripts that you do not trust. Changing the execution policy may expose you to the risks described in the about_Execution_Policies help topic. Do you want to change the execution?

[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"): Y

You can verify the change by running the Get-ExecutionPolicy command:

```
PS C:\Users\Administrator> get-executionpolicy
```

Your server is now set to allow all scripts. For security reasons, I would suggest when finished installing scripts that you change it to Restricted.

Let's look at using script with PowerShell. You'll find it when you want to add roles, role services, or features to multiple servers. You will need a configuration file to achieve this. Just to show how to do this, we will use the Add Roles and Features Wizard and export the configuration page to a file (see Figure 2.47).

Since the previous pages explained how to add a role using the wizard, go ahead and add a Remote Desktop Services role, but stop when you get the role configuration page. On the confirmation page (last page in the wizard), there is a link at bottom below you to export the configuration to a file (see Figure 2.47).

# Figure 2.47
Exporting a role to a configuration XML file

![](img/41a83208e6906a3732620203b836cea7_102_0.png)

# CHAPTER 2 INSTALLING AND UPGRADING WINDOWS SERVER 2012 R2

Save the file as RemoteDesktopConfig.xml on your C drive root or any convenient location you choose. If you want to open it with Internet Explorer to see what it looks like, free in. Figure 2.48 is a partial screenshot of the site. You can go ahead and cancel the wizard that you saved the file. Do not hit Install!

Figure 2.48
XML configuration file

```
<xml version="1.0"?>
<Config xmlns="http://schemas.microsoft.com/powershell/2004/04" Version="1.1.0.1">
 <Obj Ref="Root">
 <T>System.Collections.ObjectModel.ObjectCollection`1[System.Management.Automation.PSObject,System.Management.Automation,Version=3.0.0.0,Culture=neutral,PublicKeyToken=31bf35619344e089]</T>
 <T>System.Object</T>
 </Obj>
 <LIST>
 <Obj Ref="Ref1">
 <T>System.Management.Infrastructure.CInstance:ROOT/Microsoft/Windows/ServerManager</T>
 <T>System.Management.Infrastructure.CInstance:ROOT/Microsoft/Windows/ServerManager</T>
 <T>System.Management.Infrastructure.CInstance:ServerComponent_RDS_Server/ServerComponent</T>
 <T>System.Management.Infrastructure.CInstance</T>
 <T>System.Object</T>
 </Obj>
 <LIST>
 <T>ServerComponent_RDS_Server/ServerServer-1</T>
 <S Name="Name">Server1</S>
 <M>
 <D Name="NumericId">130 - 132</D>
 </M>
 <Obj Ref="Ref2">
 <T>System.Collections.ArrayList`1[System.Object]</T>
 <T>System.Object</T>
 </Obj>
 <LIST>
 <Obj Ref="Ref3">
 <S Name="ClassName">ServerManagerServerComponentDescriptor</S>
 <S Name="Namespace">ROOT/Microsoft/Windows/ServerManager</S>
 <S Name="BaseClass">System.Management.Infrastructure.CInstance</S>
 <D Name132 Name="Hash">55737032-132</D>
 <S Name="NAME">ServerManagerServerComponentDescriptor</S></QUALIFIER
```

OK, you are ready to install the Remote Desktop Services for multiple computers using a script file. Open PowerShell by right-clicking the PowerShell icon in the taskbar, and select Run as Administrator.
Inside PowerShell add the following function:

```
function Invoke-WindowsFeatureBatchDeployment
param (
[parameter(mandatory)]
[string[] $ComputerNames,
[parameter(mandatory)]
[string] $ConfigurationFilePath
)

# Deploy the features on multiple computers.
$jobs = @()
foreach($ComputerName in $ComputerNames) {
  $jobs += Start-Job -Script {
    Install-WindowsFeature -ConfigurationFilePath $using:ConfigurationFilePath -ComputerName $using:ComputerName
  }
}
Receive-Job $jobs -Wait | Select-Object Success, RestartNeeded, ExitCode, FeatureResult
}

# Sample Invocation
$ServerNames = 'TestServer_01', 'LabServer_02'
Invoke-WindowsFeatureBatchDeployment -ComputerNames $ServerNames -ConfigurationFilePath:RemoteDesktopConfig.xml
```

# REMING A ROLE

Removing roles, services, and features with PowerShell is as easy as it is to install them. The Remove-WindowsFeature cmdlet is similar to the Install-WindowsFeature cmdlet:

```
Remove-WindowsFeature <Role>,<RoleService>,<Feature> -restart -whatif
```

Here's the syntax:
