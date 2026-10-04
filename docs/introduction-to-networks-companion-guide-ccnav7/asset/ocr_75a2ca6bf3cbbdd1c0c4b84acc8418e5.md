# Example 10-2 Securing Access to a Router

```
R1(config)# enable secret class
R1(config)#

R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config-line)# exit
R1(config)#

R1(config)# line vty 0 4
R1(config-line)# password cisco
R1(config-line)# login
R1(config-line)# transport input ssh telnet
R1(config-line)# exit
R1(config)#

R1(config)# service password-encryption
R1(config)#
```

It is a good idea to provide a legal notification that warns users that the device should be accessed only by permitted users. Legal notification is configured as shown in Example 10-3.

# Example 10-3 Configuring a Banner Warning

```
R1(config)# banner motd #
Enter TEXT message. End with a new line and the #
**************************************************
WARNING: Unauthorized access is prohibited!
**************************************************
#
R1(config)#
```

If the commands shown so far are all entered on a router that accidentally loses power, all this configuration is lost. For this reason, it is important to save the configuration when changes are implemented. The command shown in Example 10-4 saves the configuration to NVRAM.

# Example 10-4 Saving the Running Configuration

```
R1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
R1#
```