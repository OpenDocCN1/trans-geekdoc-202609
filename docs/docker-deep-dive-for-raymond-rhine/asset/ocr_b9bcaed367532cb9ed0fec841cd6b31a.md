Let’s quickly compare namespaces and containers with hypervisors and virtual machines (VM).

Namespaces virtualize operating system constructs such as process trees and filesystems, whereas hypervisors virtualize physical resources such as CPUs and disks. In the VM model, hypervisors create virtual machines by grouping virtual CPUs, virtual disks, and virtual network cards so that every VM looks, smells, and feels like a physical machine. In the container model, namespaces (containers) by grouping virtual process trees, virtual filesystems, and virtual network interfaces so that every container looks, smells, and feels exactly like a regular OS.

At a very high level, namespaces provide lightweight isolation but do not provide a strong security boundary. Compared with VMs, containers are more efficient, but virtual machines are more secure.

Don’t worry, though. Platforms like Docker implement additional security technologies, such as cgroups, capabilities, and seccomp, to improve container security.

Namespaces are a tried and tested technology that’s existed in the Linux kernel for a very long time. However, they were