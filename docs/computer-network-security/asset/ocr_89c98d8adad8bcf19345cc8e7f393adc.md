```
R1(config-cmap)# match access-group 102
R1(config-cmap)# exit
```

# ## 4. Create the Policy-Map to apply the Class-Maps.

# ### 4.1. Create a Policy-Map to apply the CMAP-IN-TO-DMZ Class-Map.

```
R1(config)# policy-map type inspect PMAP-IN-TO-DMZ
R1(config-pmap)# class type inspect CMAP-IN-TO-DMZ
R1(config-pmap-c)# pass
```

# ### 4.2. Similarly, create the following Policy-Maps:

+   - PMAP-OUT-TO-DMZ for the CMAP-OUT-TO-DMZ Class-Map
+   - PMAP- IN-TO-HEAD for the CMAP-IN-TO-HEAD Class-Map

# ## 5. Define the zone pairs.

Create the following zone pairs:

| Name of the zone pair | Source | Destination | Strategy to apply |
|---|---|---|---|
| IN-to-DMZ | IN-ZONE-Z10 | DMZ-ZONE | PMAP-IN-TO-DMZ |
| OUT-to-DMZ | OUT-ZONE | DMZ-ZONE | PMAP-OUT-TO-DMZ |
| IN1-to-HEAD | IN-ZONE-Z10 | HEAD-ZONE | PMAP- IN-TO-HEAD |
| IN2-to-HEAD | IN-ZONE-Z20 | HEAD-ZONE | PMAP- IN-TO-HEAD |

# ## 6. Assign the interfaces to the zones.

| Name of the interface | Name of the security zone |
|---|---|
| G0/0 | IN-ZONE-Z20 |
| G0/1 | IN-ZONE-Z10 |
| G0/2 | DMZ-ZONE |
| S0/0 | OUT-ZONE |
| S0/1 | HEAD-ZONE |

# ## 7. Verify the configuration of R1.

Using the “show running-config” command, verify all the parameters of your configuration.