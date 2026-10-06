# CONFIGURING RULES AND FEATURES 133

[-InstallationMediaPath<String>] [-InstallDns] [-LogPath<String>]
[-MoveInfrastructureMasterRoleIfNecessary] [-DnsOnNetwork]
[-GlobalCatalog] [-RebootOnCompletion] [-ReplicationSource<String>]
[-SafeModeAdministratorPassword<SecureString>] [-SiteName]
[-SkipAutoConfigns] [-SkipPreChecks] [-SystemKey<SecureString>]
[-SysvolPath] [-Confirm] [-CommonParameters]]

Go ahead and run the cmdlet:

```
PS:\Users\administrator> Install-ADDSDomainController
```

You will be prompted with the following:

The target server will be configured as a domain controller and restarted when this operation is complete.

Do you want to continue with this operation?

+   [Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "Y")

When you select Yes, the installation will begin (Figure 3.20). This process may take several minutes to complete.

![](bbox=[0.098, 0.448, 0.878, 0.513])

# Configuring the DHCP Server

When Windows Server 2003 came out, Microsoft was starting to kick up sand onto the ultra-geek Linux system. It increased the available suite of commands to provide ultra-geek wannabes with the tools to configure as much as possible. That the netsh command came into fashion.

A branch office requires a basic DHCP implementation, with a single scope with standard options of default gateway, DNS servers, and DNS domain name. Before setting that up, you need to identify it in Active Directory, by using the add option. In the following code, interactive mode is utilized to execute the commands:

```
netsh dhcp
netsh dhcp>add server bfsc1.bigfirm.com 192.168.1.11
```

Adding server bfsc1.bigfirm.com, 192.168.1.11

Command completed successfully.