
1.5. Allow all “show IP” commands for this privilege level in exec mode.

```
R1(config)#privilege exec all level 10 show ip
```

1.6. Create a new user account with the following options:

- username: “TelUser”;
- encrypted password “TelUpa$$”;
- privilege level 12.

```
R1(config)# username TelUser privilege 12 secret TelUpa$$
```

1.7. Configure the password “Priv12P$” for privilege level 12.

```
R1(config)#enable secret level 12 Priv12P$
```

1.8. Allow the “ping” command for this privilege level in the exec mode.

```
R1(config)#privilege exec level 12 ping
```

1.9. Allow the “telnet” command for this privilege level in exec mode.

```
R1(config)#privilege exec level 12 telnet
```

1.10. Allow all configuration mode commands for this privilege level

```
R1(config)#privilege exec all level 12 configure
```

1.11. Follow the same steps to configure a privilege level 13 by endowing it with the following options:

- passwords Priv13P$;
- authorized commands: telnet, traceroute, show (all), configure (all).

1.12. Access privilege levels 10, 12 and 13 and test the configuration.

```
Router>enable 12
Password:
R1#?
Exec commands:
<1-99>   Session number to resume
connect  Open a terminal connection
disable  Turn off privileged commands
- disconnect Disconnect an existing network connection
- enable Turn on privileged commands
- exit Exit from the EXEC
- logout Exit from the EXEC
- no Disable debugging information
- ping Send echo messages
- resume Resume an active network connection
- telnet Open a secure shell client connection
- terminal Set terminal line parameters
```

NOTE:
- 0 (zero) privilege level commands are automatically added.
- All commands that are not desired for a particular privilege level must be individually assigned to other privilege levels.
- Tests for results and privilege levels can also be carried out via ssh using the TelUser or sshUser accounts

1.13. Display the current privilege level.

```
R1# show privilege
```

## EXERCISE 2

### Topology

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_48_0.png)

### Addressing table

| Device | Interface | IP address / subnet mask | Operating System | Gateway |
| :--- | :--- | :--- | :--- | :--- |
| R1 | G0/0 | 192.168.0.1/24 | c2600-adventerprisek9-mz.124-1 | – |
| PC1 | NIC | 192.168.0.2/24 | Windows 7 or higher | 192.168.0.1 |

### Objectives

- Securing passwords.
- Putting in place connection restrictions.
- Securing access by managing “views” and “super-views”.
- Securing the configuration files and IOS system.
- Using automated security features.

### Software to be used

- GNS3.

### Part A: establishing the basic device configuration

- 1.1. Configure the host name as indicated in the topology.
- 1.2. Apply the IP addresses to the device interfaces according to the addressing table.

### Part B: securing passwords

- 1. Set a minimum password length of 8 characters.

```
R1(config)# security passwords min-length 8
```

- 2. Configure the password for the privileged mode.

```
R1(config)# enable secret Ci$c0ena
```

- 3. Configure the console ports, auxiliary ports and virtual access lines.

- 3.1. Configure a console port password and set the inactivity interval to 5 minutes.

```
R1(config)# line console 0
R1(config-line)# password Ci$c0con
R1(config-line)# exec-timeout 5 0
R1(config-line)# login
R1(config-line)# logging synchronous
```

- 3.2. Configure a password on the VTY lines and set the inactivity interval to 2 minutes.

```
R1(config)# line vty 0 4
R1(config-line)# password Ci$c0vty
R1(config-line)# exec-timeout 2 0
R1(config-line)# login
```

- 3.3. Disable the auxiliary port.

```
R1(config)# line aux 0
R1(config-line)# no exec
```

- 3.4. Access the R1 router from PC1 using Telnet.

```
PC1> telnet 192.168.0.1
```

- 4. Encrypt all passwords.

```
R1(config)# service password-encryption
```

### Part C: securing access to VTY lines with ssh

- 1. Configure ssh connections.

Use the following options to configure ssh connections:

- domain name: tri.local;
- username: sshadmin with the password: Ci$c0ssh;
- the RSA encryption key is 1024 bits;
- the SSH version used is version 2;
- the wait time is 90 seconds;
- the number of login attempts is 3;
- authorize ssh and VTY sessions.

- 2. Configure the connection parameters.

Use the "login block-for" command to configure a connection block of _60 seconds_ if there are two failed connection attempts within _30 seconds_.

```
R1(config)#login block-for 60 attempts 2 within 30
```

### Part D: securing access using “view” management

- 1. Create a new user account “User01” with the encrypted password “Us01paSS”.

```
R1(config)# username User01 secret Us01paS$
```

- 2. Activate the “AAA” on R1.

```
R1# config terminal
R1(config)# aaa new-model
R1(config)# exit
```

- 3. Create a “ViewRouter” view.

```
R1#enable view
Password: (password enable)
R1#conf t
R1(config)# parser view ViewRouter
R1(config-view)#
```

- 4. Assign the password “ViewRouPs” to this view.

```
R1(config-view)# secret ViewRouPs
```

- 5. For this view, allow all the “show” commands in exec mode.

```
R1(config-view)# commands exec include all show
```

- 6. Allow all commands in the configure mode.

```
R1(config-view)# commands exec include all configure terminal
```

- 7. Allow all commands for the mode in router mode.

```
R1(config-view)# commands configure include all router
```

- 8. Follow the same steps to create a “ViewTelnet” view and to endow it with the following options:

- Password ViewTelPs;
- The authorized commands: telnet, traceroute, show (all).

- 9. Access the ViewRouPs view and test the configuration.

```
R1#enable view ViewRouPs
Password:
Router#?
Exec commands:
configure Enter configuration mode
disable Turn off privileged commands
enable Turn on privileged commands
exit Exit from the EXEC
logout Exit from the EXEC
show Show running system information
```

For the ViewTelnet view:

```
R1#enable view ViewTelnet
Password:
R1#?
Exec commands:
disable Turn off privileged commands
enable Turn on privileged commands
exit Exit from the EXEC
logout Exit from the EXEC
show Show running system information
telnet Open a telnet connection
traceroute Trace route to destination
```

- 10. Display the list of views.

```
R1#show parser view all
Views/SuperViews Present in System:
ViewRouter
ViewTelnet
-----(*) represent superview------
```

- 11. Assign “ViewRouter” to “User01”.

```
R1(config)#username User01 view ViewRouter
```

- 12. Create a super-view, “SuperView1” with the password “$uperView1”.

```
R1#enable view
Password: (password enable)
R1(config)# parser view SuperView1 superview
R1(config-view)#secret $uperView1
```

- 13. Assign the “ViewRouter” and “ViewTelnet” views to this super-views.

```
R1(config-view)# view ViewRouter
R1(config-view)# view ViewTelnet
```

- 14. Display the list of views.

```
R1#show parser view all
Views/SuperViews Present in System:
ViewRouter
ViewTelnet
SuperView1 *
-----(*) represent super-view-----
```

- 15. Assign “SuperView1” to “User01”.

```
R1(config)#username User01 view SuperView1
```

### Part E: securing configuration files and the IOS system

- 1. Display the content of the flash memory.

```
R1#show flash:
System flash directory:
File Length Name/status
  3  50938004 c2800nm-advipservicesk9-mz.124-15.T1.bin
  2  28282   sigdef-category.xml
  1  227537  sigdef-default.xml
[51193823 bytes used, 12822561 available, 64016384 total]
63488K bytes of processor board System flash (Read/Write
```

- 2. Securing the IOS image file by hiding it in the Flash memory.

```
R1(config)# secure boot-image
```

- 3. Securing the current configuration file on the Flash memory.

```
R1(config)# secure boot-config
```

- 4. Once again display the content of the Flash memory.

```
R1#show flash:
System flash directory:
File Length Name/status
2 28282 sigdef-category.xml
1 227537 sigdef-default.xml
[51193823 bytes used, 12822561 available, 64016384 total]
63488K bytes of processor board System flash (Read/Write
```

- 5. Can you see the IOS image file? Why?

............................................................................

- 6. Display the archive status of the Cisco IOS image and of the configuration file.

```
R1# show secure bootset
IOS image resilience version 12.4 activated at 00:01:50 UTC mon. march 1 1993
Secure archive flash:/c2800nm-advipservicesk9-mz.124-15.T1.bin type is image (elf) file size is 50938004 bytes, run size is 50938004 bytes
Runnable image, entry point 0x8000F000, run from ram
IOS configuration resilience version 12.4 activated at 00:02:03 UTC mon. march 1 1993
Secure archive flash:/runcfg-19930301-000203.ar type is config configuration archive size 551 bytes
```

- 7. Configure the startup from ROMMON and restart the router.

```
R1(config)#config-register 0x2100
R1(config)#exit
R1#reload
Proceed with reload? [confirm]
```

- 8. Display the secured files available in ROMMON mode.

```
rommon 1 > dir flash:
```
