These VSP modules are paired with corresponding VSC modules. For example, the storage module of the VSC will communicate with the storage module in the VSP. Where the VSC communicates only with the VSP in the parent partition, the VSP communicates with all VSC components. It is possible for non-Microsoft developers to design and build their own modules since the relevant APIs are all open.

With the kernel part of the Management OS covered, now we'll progress to the user mode components. The Virtual Machine (VMM) is responsible for managing all virtual machine partitions. Whenever a virtual partition is started, the VMM starts a new virtual machine worker (VMW) process for this guest. This process does not do any work, except for monitoring, starting, shutting down, and so on.

# WHAT PROCESS “RUNS” THE VM?

Contary to similar worker processes in the hybrid model, the VMW process does not really "run" the virtual machine partition. It controls it. You can't free from the CPU using the VMW process if the guest is doing anything, except with the exception of data transfer by legacy (non-enlightened) devices.

In fact, all virtual machine partitions may be running up to 100 percent CPU without anything showing up in the Management OS partition directly. To find out what the guest is doing, you will need to either connect to the guest directly using normal server management tools, Performance Counters, or accessing the WMI provider in the Management OS partition.

The final component in the Management OS partition is the WMI provider. Years ago Microsoft decided that WMI would be the preferred way to manage and monitor system resources, and Hyper-V is no exception. The WMI provider is widely documented on MSDN and provides the following functionality:

+   * Status reporting on mouse and keyboard
* Access to the VM BIOS
* Managing and reading the configuration of networking, serial devices, storage, guest partitions, and so on
* Reading current properties
* Managing power state

From this feature set you can see that the WMI provider has all the functionality required to manage the Hyper-V environment. In fact, most management systems for Hyper-V are expected to use WMI. Unfortunately, the WMI interface is a little too involved to use directly for most daily management activities. Only people with extensive WMI programming experience will be able to work productively with this, and more and more functionality has been introduced into PowerShell to help ease management and administration, this is surely the way forward.