This command applies weak encryption to all unencrypted passwords. This encryption applies only to passwords in the configuration file, not to passwords as they are sent over the network. The purpose of this command is to keep unauthorized individuals from viewing passwords in the configuration file.

Use the show running-config command to verify that passwords are now encrypted, as shown in Example 2-10.

# Example 2-10 Verifying That Passwords Are Encrypted

```
Sw-Floor-1(config)# end
Sw-Floor-1# show running-config
!
!
<Output omitted>
!
line con 0
password 7 094F471A1A0A
login
!
line vty 0 4
password 7 03095A0F034F38435B49150A1819
login
line vty 5 15
password 7 094F471A1A0A
login
!
!
!
end
```

# Banner Messages (2.4.5)

Although requiring passwords is one way to keep unauthorized personnel out of a network, it is vital to provide a method for declaring that only authorized personnel should attempt to access a device. To do this, you can add a banner to the device output. Banners can be an important part of the legal process in the event that someone is prosecuted for breaking into a device. Some legal systems do not allow prosecution, or even the monitoring of users, unless a notification is visible.

To create a banner message of the day on a network device, use the banner motd # the message of the day # global config command. The # in the command syntax is called the delimiting character. It is entered before and after the message. The delimiting character can be any character as long as it does not occur in the message.