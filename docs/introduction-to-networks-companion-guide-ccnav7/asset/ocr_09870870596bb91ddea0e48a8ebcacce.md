Network administrators might become distracted and accidently leave a privileged EXEC mode session open on a terminal. This could enable an internal threat actor access to change or erase the device configuration.

By default, Cisco routers log out an EXEC session after 10 minutes of inactivity. However, you can reduce this setting by using the exec-timeout minutes seconds line console configuration command. This command can be applied on line console, auxiliary, and vty lines. In Example 16-2, exec-timeout 5 30 tells the Cisco device to automatically disconnect an inactive user on a vty line after the user has been idle for 5 minutes and 30 seconds.

# Example 16-2  Configuring Additional Password Security on a Cisco Router

```
Router(config)# service password-encryption
Router(config)# security password min-length 8
Router(config)# login block-for 120 attempts 3 within 60
Router(config)# line vty 0 4
Router(config-line)# password cisco
Router(config-line)# exec-timeout 5 30
Router(config-line)# transport input ssh
Router(config-line)# end
Router#
Router# show running-config | section line vty
line vty 0 4
  password 7 03095A0F034F
  exec-timeout 5 30
  login
Router#
```

# Enable SSH (16.4.4)

Telnet simplifies remote device access, but it is not secure. Data contained in a Telnet packet is transmitted unencrypted. For this reason, it is highly recommended to enable Secure Shell (SSH) on devices for secure remote access.

It is possible to configure a Cisco device to support SSH by using the following six steps:

+   Step 1. Configure a unique device hostname other than the default.
Step 2. Configure the IP domain name of the network by using the global configuration mode command ip domain name name.

![](bbox=[0.1, 0.84, 0.23, 0.9])