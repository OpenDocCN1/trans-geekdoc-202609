# MANAGING VM REPLICAS

With your VMs configured, you can perform a number of actions by right-clicking the offline VM located on the destination host and choosing the Replication menu, as shown in Figure 28.23.

FIGURE 28.23
VM replication options on the destination host

| Connect... | |
|---||
| Settings... | |
| Start... | |
| Snapshot | |
| Move... | |
| Export... | |
| Rename... | |
| Delete... | |
| Replication | Failover...
| Help | Test Replication
View Replication Health...
Remove Replication |

From this menu, you can perform the failover tasks:

**Unplanned Failover** An unplanned failover is not to be carried out, and itmumes that the production VM cannot be contacted anymore as a result of an unexpected outage or disaster. You can simulate an unplanned failover by turning off the production VM, right-clicking the replica VM located on the destination host, and selecting the Failover option. From there you can choose the relevant recovery point. When you've chosen the recovery point, the replica VM will power up on the destination.

**Test Failover** A test failover creates a copy of the VM by cloning and storing the clone on a differential virtual disk using the replica VM's storage as its parent. Because it uses the replica's storage, it will save the differential disk in the same volume as the replica; ensure you have enough disk space on this volume if you intend to keep the test VM up and running for an extended period of time. This test process allows you to verify if your recovery points are up to date and when you should need to use them in a DR situation.

**Pause Replication** This option does exactly what it says on the tin. You will use this if you want to pause replication between the destination and source hosts for a particular VM. When you've paused replication, this option changes to Resume Replication, which you can use to restart the process when you're ready.

**View Replication Health** This option will provide you with statistics on the health of your replicated VM, as shown in Figure 28.24. You can get some useful information here including things as data size, latency, errors encountered, and last sync time. It's always a good place to start when troubleshooting HVR replicas.

**Remove Replication** Another obvious option here. If you wish to remove replication for a particular VM, then this is what you need to choose. You must select this option on both the source and destination VMs to fully remove replication.