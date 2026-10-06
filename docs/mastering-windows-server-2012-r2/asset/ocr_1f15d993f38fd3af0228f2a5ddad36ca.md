# FIGURE 6.14

Zone transfers for a primary zone

![](bbox=[0.338, 0.096, 0.763, 0.396])

# FIGURE 6.15

Name servers for a primary zone

![](bbox=[0.338, 0.423, 0.763, 0.706])

The zone transfer process is not complex. For the primary zone changes it has made and has a serial number for the change. When a secondary server contacts the primary server, it checks out the serial number in the Start of Authority record. If the serial number on the secondary server doesn't match, it to replicate the changes. This is simply a text-based blast of DNS supported (all zone transfers) replication, which meant the entire zone was replicated to the secondary server. This could be too much traffic to throw onto the line. Windows DNS supports IXFR (which are incremental zone transfers), which replicates just the changes. Windows DNS also supports notification of secondary servers, which reduces the wait time to trigger replication.