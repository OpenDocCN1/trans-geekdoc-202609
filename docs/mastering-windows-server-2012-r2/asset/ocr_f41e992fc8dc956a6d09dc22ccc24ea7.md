# Chapter 28

# Managing Virtual Machines

A brief overview

In the previous chapter, you learned the main points of Hyper-V: how to install it, its software architecture, and the ins and outs of virtual disks and networks. We also discussed how to get started with virtual machines and what's required to configure and install them. There's still a lot to talk about with Hyper-V, and in this chapter we will discuss topics such as virtualizing domain controllers, live migration, managing your virtual machines, and disaster recovery. Some of these topics we will briefly discuss for awareness, and others we'll dive into in depth.

In this chapter, you will learn to:

+   - Virtualize domain controllers

+   - Understand how to move your VMs around

+   - Manage your VMs

+   - Understand disaster recovery with Hyper-V

# Domain Controllers and Hyper-V

While virtualization has taken most parts of server computing by storm, it's always been just a bit dangerous to virtualize domain controllers (DCs). Let's be honest, though; with the flexibility and cost savings of virtualization, the temptation for us to have idealized DCs was just too much, and there are plenty of them sitting on various hypervisor platforms. Prior to Windows Server 2012, if you virtualized your DCs, then you had to jump through a number of hoops and cut through some red tape to ensure Active Directory maintained its integrity.

When you virtualize your DCs, due to the dependency that the Kerberos authentication has on reliable timekeeping, issues as maintaining accurate time synchronization inside the VM become paramount to the health of your overall Active Directory.

To illustrate what might go wrong, consider a real-world example of a VM running an Active Directory domain controller. It's running on a stand-alone Hyper-V host that is not joined to a network component, a centrally located switch, for example. The switch gets a new firmware update and accidentally sets the time a year ahead. During maintenance, the host picks this up and also sets its time to a year ahead. Then the virtual DC does the same. At that point, it stops replicating with its peers because Kerberos authentication is broken, and pretty soon your phone will start start ringing off the wall with users complaining of logon issues.