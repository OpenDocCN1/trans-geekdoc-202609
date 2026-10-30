# Virtualization

Virtualization technology is used to allow a computer to have more than one OS present and, in many cases, operating at the same time. Virtualization is an abstraction of the OS layer, creating the ability to host multiple OSs on a single piece of hardware. One of the major advantages of virtualization is the separation of the software and the hardware, creating a barrier that can improve many system functions, including security. The underlying hardware is referred to as the host machine, and on it is a host OS. Either the host OS has built-in hypervisor capability or an application is needed to provide the hypervisor function to manage the virtual machines (VMs). The virtual machines are typically referred to as the guest OSs.

> **EXAM TIP** A hypervisor is the interface between a virtual machine and the host machine hardware. Hypervisors are the layer that enables virtualization.

Newer OSs are designed to natively incorporate virtualization hooks, enabling virtual machines to be employed with greater ease. There are several common virtualization solutions, including Microsoft Hyper-V, VMware, Oracle VM VirtualBox, Parallels, and Citrix Xen. It is important to distinguish between virtualization and boot loaders that allow different OSs to boot on hardware. Apple’s Boot Camp allows you to boot into Microsoft Windows on Apple hardware. This is different from Parallels, a product with complete virtualization capability for Apple hardware.

Virtualization offers much in host-based management of a system. From snapshots that allow easy rollback to previous states, faster system deployment via preconfigured images, ease of backup, and the ability to test systems, virtualization offers many advantages to system owners. The separation of the operational software layer from the hardware layer can offer many improvements in the management of systems.

# Snapshots

A snapshot is a point-in-time saving of the state of a virtual machine. Snapshots have great utility because they are like a savepoint for an entire system. Snapshots can be used to roll a system back to a previous point in time, undo operations, or provide a quick means of recovery from a complex, system-altering change that has gone awry. Snapshots act as a form of backup and are typically much faster than normal system backup and recovery operations.

# Patch Compatibility

Having an OS operate in a virtual environment does not change the need for security associated with the OS. Patches are still needed and should be applied, independent of the virtualization status. Because of the nature of a virtual environment, it should have no effect on the utility of patching, as the patch is for the guest OS.

# Host Availability/Elasticity

When you set up a virtualization environment, protecting the host OS and hypervisor level is critical for system stability. The best practice is to avoid the installation of any