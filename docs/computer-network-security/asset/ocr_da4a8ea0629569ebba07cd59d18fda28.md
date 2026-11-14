![](bbox=[0.145, 0.105, 0.86, 0.405])

# 2.3. Launch the attack by pressing the “Execute” button and check the result:

```
S1#sh ip dhcp binding
Bindings from all pools not associated with VRF:
IP address          Client-ID/                                          Lease expiration   Type
                    Hardware address/
                    User name
172.16.0.10         0100.1122.3344.93                                   Mar 01 2002 12:28 AM
Automatic
172.16.0.11         0100.1122.3344.e2                                   Mar 01 2002 12:28 AM
Automatic
172.16.0.12         0100.1122.3344.9b                                   Mar 01 2002 12:28 AM
Automatic
172.16.0.13         0100.1122.3344.ce                                   Mar 01 2002 12:28 AM
Automatic
```

# 3. Secure the S1 F0/1 port.

Enable port security on S1 and redo the TP. Ensure that attacks can no longer occur.