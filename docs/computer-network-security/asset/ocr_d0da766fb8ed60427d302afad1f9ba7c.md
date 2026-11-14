# 2. Configure the routing using the OSPF protocol.

+   2.1. Enable OSPF on the routers using the value 1 as the process ID.

+   2.2. Set the RID value to 1.1.1.1 for R1, to 2.2.2.2 for R2 and to 3.3.3.3 for R3.

+   2.3. Add all networks to the OSPF protocol.

+   2.4. Test connectivity between all network elements.

# Part B: configuring a zone-based firewall

+   1. Review the definition of the DMZ zone.

# 2. Creating security zones on R1.

+   2.1. Create the internal zone with the name IN-ZONE.

```
R1(config)# zone security IN-ZONE
R1(config-sec-zone) exit
```

+   2.2. Create the DMZ zone with the name DMZ-ZONE.

```
R1(config)# zone security DMZ-ZONE
R1(config-sec-zone) exit
```

+   2.3. Create the external zone with the name OUT-ZONE.

```
R1(config)# zone security OUT-ZONE
R1(config-sec-zone) exit
```

+   2.4. Create the external zone with the name HEAD-ZONE.

```
R1(config)# zone security HEAD-ZONE
R1(config-sec-zone) exit
```