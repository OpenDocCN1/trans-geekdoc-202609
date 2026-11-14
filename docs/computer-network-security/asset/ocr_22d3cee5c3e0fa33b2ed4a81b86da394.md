# 9. Check that your configuration works.

# 9.1. Review the definition of an IDS.

# 9.2. Send out a “ping” from PC2 to Server-http2.

# 9.3. Check that the following message was added to the Server-SYSLOG:

> %IPS-4-SIGNATURE: Sig:2004 Subsig:0 Sev:25 [192.168.0.2 -> 192.168.10.2:0] RiskRating:25

# 9.4. Why can R2 be considered as an IDS and not an IPS?

# 9.5. Modify the “ICMP Echo Request” signature to refuse ICMP packets.

```
R2(config)#ip ips signature-definition
R2(config-sigdef)#signature 2004 0
R2(config-sigdef-sig)#engine
R2(config-sigdef-sig-engine)#event-action produce-alert
R1(config-sigdef-sig-engine)#event-action deny-packet-inline
R2(config-sigdef-sig-engine)#exit
R2(config-sigdef-sig)#exit
R2(config-sigdef)#exit
Do you want to accept these changes? [confirm]
```

# 9.6. Send out a “ping” from PC2 to Server-http2. Why was this command unsuccessful?

# 9.7. Verify that a message has been added to the Server-SYSLOG.