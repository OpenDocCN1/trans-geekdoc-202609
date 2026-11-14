| Command | Description |
|---|---|
| R1(config)# ip access-list extended VPN-ACL | Creates an extended ACL. |
| R1(config-ext-nacl)# permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255 | Identifies the “interesting traffic”. |

2) create an IKE policy and configure the settings required for Phase 1.

| Command | Description |
|---|---|
| R1(config)# crypto isakmp policy 10 | Creates the IKE policy. |
| R1(config-isakmp) # authentication pre-share | Defines the authentication method. |
| R1(config-isakmp) # encr aes 128 | Defines the encryption protocol. |
| R1(config-isakmp) # hash sha | Defines the hash function. |
| R1(config-isakmp) # group 5 | Defines the DH group to be used. |
| R1(config-isakmp) # lifetime 86400 | Defines the IKE timeout. |

3) specify the shared key (PSK) and identify the IP address on the other side of the VPN tunnel.

| Command | Description |
|---|---|
| R1(config)# crypto isakmp key PassVPN address 44.113.202.129 | Defines the shared key and the IP address for the other side of the VPN tunnel. |

4) create the IPsec policy required for Phase 2.

| Command | Description |
|---|---|
| R1(config)# crypto ipsec transform-set R1-to-R2-SET esp- sha-hmac esp-aes 128 | Defines the communication settings for Phase 2. |

5) create the encryption map and configure the parameters of the crypto map.

| Command | Description |
|---|---|
| R1(config)# crypto map R1-to-R2-MAP 10 ipsec-isakmp | Creates an encryption map connected to IKE policy number 10. |
| R1(config-crypto-map)# set transform-set R1-to-R2-SET | Defines the identifier of the IPsec policy required for Phase 2. |
| R1(config-crypto-map)# set peer 44.113.202.129 | Sets the IP address for the other side of the VPN tunnel. |
| R1(config-crypto-map)# match address VPN-ACL | Sets the ACL ID for the traffic of interest. |