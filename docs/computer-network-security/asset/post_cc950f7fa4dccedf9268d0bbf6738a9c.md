

| Command | Description |
|---|---|
| router(config)#interface interface-type router(config-if)#ip ospf authentication message-digest | Configures per interface authentication. |
| router(config-if)#ip ospf message-digest-key key-id md5 key | Defines the authentication settings. |

- to configure per zone MD5 authentication, proceed as follows:

| Command | Description |
|---|---|
| router(config-router)#area area-id authentication message-digest | Configures per zone authentication. |
| router(config)#interface interface-type router(config-if)#ip ospf message-digest-key key-id md5 key | Defines the authentication settings. |

## 2.7.4. Configuring EIGRP protocol authentication

In order to configure the MD5 authentication for EIGRP, we must perform the following operations:

- configure a key chain;
- configure a key ID under the key chain;
- specify a password for the key ID;
- specify the acceptance and expiry time for the key (optional).

Proceed as follows:

| Command | Description |
|---|---|
| router(config)#key chain name-of-key-chain | A key chain makes it possible to configure multiple keys that may then be used to carry out secured authentication. This makes it possible, for example, to configure a validity period for a given key or to use a series of rotary keys for limited periods of time in order to reduce the probability of having a compromised key. |

| Command | Description |
|---|---|
| router(config-keychain)#key key-id | Creates a key and enter the key configuration mode. |
| router(config-keychain-key)#key-string key-string | Configures a secret key. |
| router(config)#interface interface-type router(config-if)#ip authentication key-chain eigrp as-number key-chain-name | Configures the use of a chain of specific keys for authentication. |
| router(config-if)#ip authentication mode eigrp as-number md5 | Configures the use of MD5 authentication. |

NOTE - EIGRP only supports MD5 authentication.

## 2.7.5. Configuring RIP authentication

To configure MD5 authentication for RIP, proceed as follows:

| Command | Description |
|---|---|
| router(config)#key chain name-of-key-chain | Creates the key chain. |
| router(config-keychain)#key key-id | Creates a key and enter the key configuration mode. |
| router(config-keychain-key)#key-string key-string router(config-keychain-key)#end | Configures a secret key. |
| router(config)#interface interface-type router(config-if)#ip rip authentication key-chain key-chain-name | Configures the use of a specific key chain for authentication. |
| router(config-if)#ip rip authentication mode md5 | Configures the use of MD5 authentication. |

## 2.8. Exercises for application

### EXERCISE 1.

### Topology

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_41_0.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_42_0.png)

### Addressing table

| Device | Interface | IP address / subnet mask | Operating system (GNS3) | Gateway |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1/24 | c2600-adventerprisek9-mz.124-1 | - |
| PC1 | NIC | 192.168.0.2/24 | Windows 7 | 192.168.0.1 |

### Objectives

- Securing passwords.
- Putting in place connection restrictions.
- Assigning administrative roles.

### Software to be used

- Packet Tracer.
- Or GNS3.

### Part A: establishing the basic device configuration

- 1.1. Configure the host name as indicated in the topology.
- 1.2. Apply the IP addresses to the device interfaces according to the addressing table.

### Part B: securing passwords

- 1. Set a minimum password length of 8 characters.

```
R1(config)# security passwords min-length 8
```

- 2. Configure the password for the privileged mode.

  - 2.1. Define a word in clear text for this mode.

```
R1(config)# enable password Ci$c0123
```

- 2.2. Can you read this password from the “show run” command?

- 2.3. Set an encrypted password for the privileged mode.

```
R1(config)# enable secret Ci$c0ena
```

- 2.4. Can you read this password from the “show run” command?

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

  - 3.4. Access R1 from PC1 via Telnet.

```
PC1> telnet 192.168.0.1
```

- 4. Encrypt all passwords.

  - 4.1. Use the “Password-Encryption Service” command to encrypt console and VTY passwords.

```
R1(config)# service password-encryption
```

- 4.2. Can you read console and VTY passwords from the “show run” command?

### Part C: putting in place connection restrictions

- 1. Configure a login warning banner.

  - 1.1. Configure a warning for unauthorized users using the “motd” command.

```
R1(config)# banner motd $ Access strictly forbidden for unauthorized persons $
R1(config)# exit
```

  - 1.2. From the command “show run”, what has replaced the character “$” on the configuration file?

### Part D: securing access to VTY lines

- 1. Configure ssh connections.

Use the following options to configure ssh connections:

- domain name: tri.local;
- username: sshadmin with the password: Ci$c0ssh;
- the RSA encryption key is 1024 bit;
- the SSH version used is version 2;
- the wait time is 90s;
- the number of login attempts is 3;
- authorize the ssh and telnet sessions.

- 2. Configure the connection parameters.

  - 2.1. Use the “login block-for” command to configure the connection being stopped for 60s if two connection attempts have failed within 30s.

```
R1(config)# login block-for 60 attempts 2 within 30
```

  - 2.2. Use the “Login delay” command to configure a delay of 5 seconds between successive connection attempts.

```
R1(config)# login delay 5 (GNS3)
```

  - 2.3. Add an entry to the event log each time a connection attempt was successful.

```
R1(config)# login on-success log
```

or:

```
R1(config)# login on-success log every 1 (GNS3)
```

  - 3. Create two new user accounts with a secret password.

```
R1(config)# username user01 secret user01pass
R1(config)# username user02 secret user02pass
```

- 4. Connect to R1 from a telnet session.

  - 4.1. Establish a telnet session to R1 from PC1.

```
PC1> telnet 192.168.1.1
```

  - 4.2. Have you been asked to enter a user account? Why?

............................................................................

  - 4.3. Define the VTY lines to use the login accounts defined locally.

```
R1(config)# line vty 0 4
R1(config-line)# login local
```

  - 4.4. Re-establish a telnet session to R1 from PC1.

```
PC1> telnet 192.168.1.1
```

  - 4.5. Try to log in with a wrong user ID or password twice. What message is displayed on PC1 after the second failed attempt?

............................................................................

  - 4.6. What message is displayed on the R1 console after the second unsuccessful connection attempt?

............................................................................

- 4.7. From PC1, try to establish another telnet session to R1 within 60 seconds. What message is displayed on PC1 after the Telnet connection attempt?

- 4.8. What message was displayed on the R1 router after the Telnet connection attempt?

- 5. Restrict the connection to R1 only through the use of ssh protocol.

  - 5.1. Configure the VTY lines to use only the ssh protocol.

```
R1(config)# line vty 0 4
R1(config-line)# transport input ssh
R1(config-line)# exit
```

  - 5.2. From PC1, try to establish another ssh and telnet session to R1.

### Part E: assigning administrative roles

- 1. Configure the privilege levels.

  - 1.1. Create a new user account with the following options:
    - account name: “SshUser”;
    - encrypted password ‘SshUpa $$’;
    - privilege level 10.

```
R1(config)# username SshUser privilege 10 secret SshUpa $$
```

  - 1.2. Configure the password “Priv10P $” for privilege level 10.

```
R1(config)# enable secret level 10 Priv10P$
```

  - 1.3. Allow the “ping” command for this privilege level in the exec mode.

```
R1(config)# privilege exec level 10 ping
```

  - 1.4. Allow the “ssh” command for this privilege level in the exec mode.

```
R1(config)# privilege exec level 10 ssh
```

