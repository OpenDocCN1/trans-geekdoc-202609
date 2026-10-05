called a hypervisor hosts multiple virtual machines (VMs). Each VM has its own virtualized hardware environment, so an administrator can install a standard operating system and applications on it.

Like a physical computer, for a VM to function on a network, it must have the standard networking hardware devices, as a network interface adapter and access to a switch. As part of its virtualized hardware configuration, a VM includes software-based, virtualized versions of these devices, some of which are described in this section.

# Hypervisor

The hypervisor is the software component that abstracts the physical hardware of the computer and supplies a virtualized version of hardware to each VM. There are two types of hypervisors used in use, based on how the software runs in relation to the operating system, as follows:

+   * **Type 1:** Usually implemented as part of an operating system product, the Type hypervisor loads the OS and exists as an abstraction layer between the VMs and the physical hardware. The hypervisor creates partitions, first of which is the parent partition and the others child partitions. The partition partition partition, which manages the physical hardware and runs the virtualization stack that creates the partitions. In this arrangement, there is no underlying operating system splitting resources with the hypervisor.
* **Type 2:** Implemented as a stand-alone process that runs on top of existing operating system, the Type 2 hypervisor must have processor resources among the host OS and divide its allocation of resources among the guest VMs. Used in workstation-based virtualization products, Type 2 hypervisors typically do not provide the performance needed to host production servers.

# Virtual Network Interface Card (vNIC)

Every computer, even a virtual, needs a network interface adapter to connect to the local network. In a virtualized environment, therefore, to connect a VM to a network, it must have a virtual network interface card (vNIC).

A vNIC performs many of the same functions as a physical network interface adapter, as implementing a data link layer protocol and getting packets for transmission to the network. With some virtualization products, it is even possible to install more than one vNIC in a single VM and create multiple networks within the virtualized environment.

# vSwitch

In a virtualized environment, a vSwitch performs the same role as a physical switch on a LAN. A switch is a data link layer device that functions as the communications nexus for a LAN. Each computer connected to one of the switches can communicate with the other connected computers by sending traffic through the switch.