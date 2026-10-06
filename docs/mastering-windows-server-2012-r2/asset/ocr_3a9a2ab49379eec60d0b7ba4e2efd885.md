Hyper-V was first released back in Windows Server 2008 SP1, there have been some quiet changes in certain limits, such as the number of supported processor cores or number of running virtual machines. Although this information is correct at the time of writing, those limits may well again, so check the Microsoft site for the current feature set. For now, see Table 27.2.

# Table 27.2: Windows Server 2012 R2 Hyper-V Scalability List

| FEATURE | WINDOWS SERVER 2012 R2 STANDARD AND DATACENTER |
| --- | --- |
| Maximum host physical memory | 4 TB |
| Maximum host logical processors | 320 |
| Maximum number of running VMs per host | 1,024 |
| Maximum virtual processors per host | 2,048 |
| Maximum VM memory | 1 TB per VM |
| Maximum VM processors | 64 per VM |
| Maximum hosts in a single cluster | 64 |
| Maximum number of VMs in a single cluster | 8,000 |
| Maximum number of live migrations | Unlimited |

# Understanding the Hyper-V Architecture

By this time, you should have a feeling for the basic functionality of Hyper-V. You've learned what server virtualization is for and also what's required from a hardware and software perspective to get it up and running. However, to understand what's going on and to be troubleshoot problems, you need a deeper understanding of how Hyper-V was designed. In this section, you will learn more about the software architecture of Hyper-V.

CPU capabilities play an essential role in the implementation of server virtualization. The Intel/AMD model for processors has a number of privilege levels, known as rings. In the traditional model, ring 0 has the highest privilege. The Windows kernel and device drivers use this level. Ring 0 allows access to any hardware and system. Ring 1 and 2 are not normally used in current versions of Windows. Ring 3 has the lowest privilege level. It runs normal “user” programs. In practice, this should mean any code that does not require kernel privileges. The trick here is that the CPU forbids any code running in a higher ring to write data or code belonging to a lower ring. In other words, it's a hardware security feature.

When you deploy the Hyper-V role to your computer, you're creating a hypervisor architecture. A hypervisor is a software layer between the hardware and the operating systems running on the host. This is known as the bare-metal approach: virtualization at the lowest level. The main purpose of the hypervisor is to create isolated execution environments