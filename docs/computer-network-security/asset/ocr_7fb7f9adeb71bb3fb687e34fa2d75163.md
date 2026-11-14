```
R1(config-isakmp) # group 5
R1(config-isakmp) # lifetime 3600
R1(config-isakmp )# end
```

# 2.3. Based on the previous commands, fill in the following table:

| IKE Phase 1 settings |
|---|
| The ISAKMP policy ID | |
| The authentication method | |
| The encryption algorithm | |
| The number of bits used for the encryption key | |
| The hash algorithm | |
| The Diffie-Hellman group | |
| The lifetime of the Security Association | |

# 2.4. Verify the settings of the IKE policy.

```
R1r#show crypto isakmp policy
Global IKE policy
Protection suite of priority 10
encryption algorithm: AES - Advanced Encryption Standard
(256 bit keys).
Hash algorithm: Secure Hash Standard
Authentication method: Pre-Shared Key
Diffie-Hellman group: #5 (1536 bit)
Lifetime: 3600 seconds, no volume limit
```

# 2.5. Repeat the same configuration as above on R2.

# 3. Specify the PSK shared key and identify the IP address on the other side of the VPN tunnel.

```
Configure the pre-shared key on both routers.
R1(config)# crypto isakmp key Tri123 address 192.168.10.2
R2(config)# crypto isakmp key Tri123 address 192.168.10.1
```

# 4. Create the IPsec policy required Phase 2.