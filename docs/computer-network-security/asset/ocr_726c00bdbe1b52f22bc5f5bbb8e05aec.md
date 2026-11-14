![](bbox=[0.128, 0.106, 0.88, 0.404])

# 4.2. Configure the routers to use the AAA server.

```
R1(config)# radius-server host 192.168.0.3 key R@duis00
R1(config)# aaa authentication login TELNET_CON group radius
local
```

# 4.3. Connect to R1, via Telnet, using the Admin account.

```
PC1> telnet 192.168.0.1
```

# 4.4. Why is it no longer possible to connect to R1?

# 4.5. Connect to R1, via Telnet, using the account u1.

# 4.6. Configure R2 to use AAA authentication.

```
R2(config)# radius-server host 192.168.0.3 key R@duis01
R2(config)# aaa authentication login TELNET_CON group radius
local
R2(config)# line vty 0 4
R2(config-line)# login authentication TELNET_CON
```