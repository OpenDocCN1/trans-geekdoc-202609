# 7. Test the ACL created previously.

+   — Check that it is possible to access the http service from PC1.

![](bbox=[0.13, 0.17, 0.87, 0.4])

+   — Check that the http service cannot be accessed from PC2.

+   — Check that it is possible to send a ping request to http-server from PC2.

+   — Check that it is not possible to send a ping request to PC3 from PC1.

+   — Check that it is possible to send a ping request to PC4 from PC1.

# 8. Delete the created ACL.

```
R3(config)#no access-list 100
```

# 9. On R3, create and test an extended ACL named “ACL_HTTP” which makes it possible to fulfil the security requirements stated earlier.

# 9.1. Create the extended ACL.

```
R3(config)#ip access-list extended ACL_HTTP
R3(config-ext-nacl)#
```

# 9.2. Allow http access from PC1 to http-server

```
R3(config-ext-nacl)# permit tcp host 192.168.0.2 host 192.168.2.3 eq
www
```