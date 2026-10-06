
# CHAPTER 3 INTRODUCTION TO SERVER CORE

```
<listener>
<cfg:EnableCompatibilityHttpsListener>false</cfg:EnableCompatibilityHttpsListener>
<cfg:CertificateThumbprint></cfg:CertificateThumbprint>
<cfg:Service>
<cfg:Winrs>
<cfg:AllowRemoteShellAccess>true</cfg:AllowRemoteShellAccess>
<cfg:IdleTimeout>1880000</cfg:IdleTimeout>
<cfg:MaxConcurrentUsers>5</cfg:MaxConcurrentUsers>
<cfg:MaxShellRunTime>217483647</cfg:MaxShellRunTime>
<cfg:MaxProcessesPerShell>15</cfg:MaxProcessesPerShell>
<cfg:MaxMemoryPerShell>156</cfg:MaxMemoryPerShell>
<cfg:MaxShellsPerUser>5</cfg:MaxShellsPerUser>
</cfg:Winrs>
</cfg:Config>
```

The listener also copies the mapping of a certificate to a port and IP address. So, using the trusty technique of copying the example from the embedded documentation from winrm / command, we created the following command to create a listener:
winrm winrm/config/Listener?Address=Transport=HTTPS @Hostname=bfsc1.big.com,CertificateThumbprint=03AD8670C63EBD1DBB764D7AA58YC51D8543077C

Here's an explanation of the parameters::

- **Address=** The service will listen on all available IP addresses.
- **Transport=HTTPS** There are only two options: HTTP and HTTPS. They use the default ports 5985 and 5986, respectively.
- **Hostname=** This has to be the name of the host on the certificate.
- **CertificateThumbprint=** This is the thumbprint obtained with the certutil command.

# CREATING AN INBOUND FIREWALL RULE

The next requirement is to enable an inbound firewall rule to receive the client requests. There is one available for the insecure HTTP, which would be set up with the /quickconfig option, but you need to build one for the HTTPS port.

If you're a, leatherneck system admin type, you might be inclined to torture your learning experience of the netsh advfirewall-sipping firewall command. The MMC snap-in is for French-vanilla-latte-sipping, pencil-neck-geek system admins. In this book, we appease both the leathernecks and the pencil necks.

We'll start with the essential parameters in constructing a rule. Wizards like the New Inbound Rule are useful because they walk you through configurations without missing important ones. They will assist you in constructing a command line to create the same rule. Just as in the "Server Core Survival Guide” section, we recommend creating the rules through a wizard first on a standard installation and then trying it with the command line. Another option is to take the easy way out and create it on a standard installation and simply convert it to Server Core, as explained in the survival guide section.

Using Windows Firewall with Advanced Security focused on the Server Core installation, we'll walk you through the New Inbound Rule Wizard.
The first page, shown in Figure 3.14, allows you to select a port rule.

# FIGURE 3.14
Selecting the type of inbound rule

![](img/41a83208e6906a3732620203b836cea7_162_0.png)

On the Protocol and Ports page, select TCP and enter 5986 for the port, as shown in Figure 3.15.

The Action page provides three options, as shown in Figure 3.16:

- "Allow the connection"—This is what you want for this example.
- "Allow the connection if it is secure"—As the window explains, this IPSec communication to continue the connection. The Network Access Protection feature can be used to set the IPSec policies within a network for this.
- "Block the connection"—This blocks the connection.

# FIGURE 3.15
Entering the protocol and port for the inbound rule

![](img/41a83208e6906a3732620203b836cea7_163_0.png)

# FIGURE 3.16
Selecting the action for the inbound rule

![](img/41a83208e6906a3732620203b836cea7_163_1.png)

The Profile page applies the rule to any of the three profiles you select, as shown in Figure 3.17. The public and private profiles are meant for computers that are mobile so you can work at home or at a wireless hotspot. Since this server is a domain controller, the concepts of private and public don't apply. We'll stick with the domain profile just to be secure.

# FIGURE 3-17
Limiting the rule to domain communication

![](img/41a83208e6906a3732620203b836cea7_164_0.png)

The Name page allows you to enter the name and optional description for the new rule, as displayed in Figure 3.18.

# FIGURE 3.18
Providing a descriptive name for the rule

![](img/41a83208e6906a3732620203b836cea7_164_1.png)

# CHAPTER 3 INTRODUCTION TO SERVER CORE

Now that you know the parameters required to create an inbound rule, we'll look at the leatherneck method. The embedded help information provides the following syntax for creating a firewall rule. Note that this was performed in the netsh interactive shell. It could be done as one command line well:

```
netsh advfirewall firewall=add rule ?
```

```
Usage: add name=<string>
dir=inout
action=allow|block|bypass
program=<program path>
service=<service name> any
description=<string>
enable=yes|no (default=yes)
profile=[public|private|domain](...
localip=<IPv4 address|<IPv6 address><subnet>|<range>|list>
rememoteip=<localsubnet|dhcp|wins|defaultgateway>
IPv4 address|<IPv6 address><subnet>|<range>|list>
localport=0-65535|<port range>[...]|RPC-EPC-PM|IPHTPS
```
