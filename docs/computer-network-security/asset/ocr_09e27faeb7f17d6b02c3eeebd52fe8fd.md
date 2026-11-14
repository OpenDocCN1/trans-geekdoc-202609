# 3. Create an IPS rule.

```
R2(config)#ip ips name ipsRule
```

# 4. Enable logging to the Syslog server.

```
R2(config)#service timestamps log datetime msec
R2(config)#logging on
R2(config)#logging 192.168.10.3
R1(config)#ip ips notify log
```

# 5. Configure the IPS to use the signature categories.

# 5.1. Remove all signatures

```
R2(config)#ip ips signature-category
R2(config-ips-category)#category all
R2(config-ips-category-action)#retired true
R2(config-ips-category-action)#exit
```

# 5.2. Only activate the signatures from the category “ios_ips basic”.

```
R2(config-ips-category)#category ios_ips basic
R2(config-ips-category-action)#retired false
R2(config-ips-category-action)#exit
R2(config-ips-category)#exit
Do you want to accept these changes? [confirm]
```

# 6. Apply the IPS rule to an interface.

```
R2(config)#interface S0/0
R2(config-if)#ip ips ipsRule in
```

# 7. Modify the signature parameters.

7.1. Display the information associated with the signature “ICMP Echo Request” (IDsig: 2004, IDsubsig: 0).