+   - Inspect:
+   - Drop:

# 4.2. Create a Policy-Map to apply the Class-Map CMAP-IN-TO-DMZ.

```
R1(config)# policy-map type inspect PMAP-IN-TO-DMZ
R1(config-pmap)# class type inspect CMAP-IN-TO-DMZ
R1(config-pmap-c)# pass
```

# 4.3. Similarly, create the following Policy-Maps:

+   - PMAP-OUT-TO-DMZ for the Class-Map CMAP-OUT-TO-DMZ;
+   - PMAP- IN-TO-HEAD for the Class-Map CMAP- IN-TO-HEAD.

# 5. Define the zone pairs.

5.1. Create a zone pair that applies the PMAP-IN-TO-DMZ policy between IN-ZONE and DMZ-ZONE.

```
R1(config)#zone-pair security IN-to-DMZ source IN-ZONE
destination DMZ-ZONE
R1(config-sec-zone-pair)# service-policy type inspect PMAP-IN-TO-
DMZ
```

# 5.2. Similarly, create the following zone pairs:

+   - OUT-to-DMZ that applies the PMAP-OUT-TO-DMZ strategy;
+   - IN-to-HEAD that applies the PMAP-IN-TO-HEAD strategy.

# 6. Assign the interfaces to the zones.

```
R1(config)#interface G0/0
R1(config-if)#zone-member security IN-ZONE
R1(config)#interface G0/1
R1(config-if)#zone-member security DMZ-ZONE
R1(config)#interface S0/0
R1(config-if)#zone-member security OUT-ZONE
R1(config)#interface S0/1
R1(config-if)#zone-member security HEAD-ZONE
```