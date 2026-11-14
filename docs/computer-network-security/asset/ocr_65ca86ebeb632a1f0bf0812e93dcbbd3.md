+   2.3. Add all the networks to EIGRP.

+   2.4. Test connectivity between all network elements.

# Part B: securing passwords

+   1. Set a minimum password length of 8 characters.

+   2. Set the password “Ci$c0ena” for the privileged mode.

+   3. Configure the console, auxiliary ports and virtual access lines.

+   3.1. Set “Ci$c0con” as the console port password and set the inactivity interval to 5 minutes.

+   3.2. Set the password “Ci$c0vty” on the VTY lines and set the inactivity interval to 2 minutes.

+   3.3. Disable the auxiliary port.

+   4. Encrypt all passwords.

```
R1(config)# service password-encryption
```

# Part C: securing the control plane

Configure MD5 authentication for EIGRP.

+   1. Configure the EIGRP key on R1.

```
R1(config)#key chain EIGRP-SECRET
R1(config-keychain)# key 1
R1(config-keychain-key)# key-string Ci$eigrp
```

+   2. Repeat the same configuration on R2.

+   3. Implement EIGRP authentication.

```
R1(config)#interface s0/0
R1(config-if)# ip authentication mode eigrp 1 md5
R1(config-if)# ip authentication key-chain eigrp 1 EIGRP-SECRET
```

+   4. Repeat the same configuration on R2.