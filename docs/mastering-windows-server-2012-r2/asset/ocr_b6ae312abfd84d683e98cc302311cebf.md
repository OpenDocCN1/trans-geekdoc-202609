If you open Network Connections from the control panel, you can see the new NIC team object that has been created, and when you check its status and configured speed, you will see that it has combined the speed of all the NICs in the team. Our example in Figure 4.8 shows a speed of 20 Gbps because we have added two virtual NICs to our team.

# Figure 4.8 NIC team status

![](bbox=[0.273, 0.206, 0.891, 0.583])

# NIC TEAMING IN VIRTUAL MACHINES

If you choose to deploy NIC Teaming inside your Hyper-V virtual machines (VMs), first be aware that you can use only synthetic NICs as members of a NIC team and not legacy NICs. Synthetic NICs are the default configuration for a VM in Hyper-V. Second, failover between NICs in a VM might result in traffic being sent with the wrong MAC address reference, and this could affect load balancing. Balancing this, you must ensure that each Hyper-V switch port on the Hyper-V host that is associated with a VM using NIC Teaming is allowed to teaming. To do this, use an account with administrative permissions, run the following PowerShell command-mand here:

```
Set-VMNetworkAdapter -VMName <YourVmName> -AllowTeaming On
```

If you want to create your NIC teaming using PowerShell, then follow these steps (we've configured our NIC team here the same way as we had it when we used the GUI to create it earlier):