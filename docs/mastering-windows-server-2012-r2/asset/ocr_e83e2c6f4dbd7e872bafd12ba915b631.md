Dynamic This is a new load-balancing mode that was introduced with Windows Server 2012 R2. This gives you the best of the other two load-balancing modes. Inbound and outbound traffic can be spread out evenly across the members of your NIC team using a concept called flowlets, which essentially breaks up a large flow of traffic into smaller pieces to deliver optimal data transfer.

Depending on whether you are planning to create your NIC team on a physical server or from inside a virtual server, there are a few requirements and limitations to consider:

NIC Teaming on a Physical Server Windows Server 2012 R2 supports up to 32 NICs in a team that has been created on a physical server. You must have at least one NIC to create a team: one-NIC team could be used for VLAN traffic separation, but a minimum of two NICs are recommended to provide for fault tolerance.

NIC Teaming inside a Virtual Machine If you decide to deploy NIC Teaming from inside a virtual machine, then you will be limited to only NIC members to form the team. The reason for this is due to supportability from Microsoft and doesn't necessarily mean that you can't create larger NIC teams for demo or test purposes.

Supported NIC Types Just about any Ethernet NIC can be used for NIC Teaming, providing it has passed the Windows Hardware Qualification Loop test. The following NIC types, however, are not supported:

+   * WLAN
* Bluetooth
* WWAN
* Infiniband

Mixing Different NIC Speeds If you are creating a NIC team for the purpose of load balancing and better throughput (as opposed to failover reasons), then you must ensure that each NIC in the team has the same speed connection (as 1 Gbps, for example). Mixing NICs with different speeds—such as some 1 Gbps and others 100 Mbps—in a team is not supported, and undesired results will occur if you deploy your team in the mix.

# NIC TEAMING ONLINE RESOURCES

If you want to learn more about NIC Teaming in Windows Server 2012, then take the time to read this excellent series of blog posts by Irish Hyper-V MVP Aidan Finn:

```
http://www.aidannfinn.com/?p=13984
```

Another resource worth checking out is the "What's New in Windows Server 2012 R2 Networking" session that was recorded at Microsoft's TechEd North America 2013 conference and is available here:

```
http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B216
```