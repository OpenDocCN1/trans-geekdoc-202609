
# 7. Application consolidation [[13–15](#index_split_000.html#p29), [19](#index_split_000.html#p29)]

# 8. Better use of existing hardware [[9](#index_split_000.html#p28)]

# 9. Sand boxing [[13](#index_split_000.html#p29)]

# 10. Numerous execution environments [[13](#index_split_000.html#p29)]

# 11. Debugging [[13](#index_split_000.html#p29)]

# 12. Software migration [[13](#index_split_000.html#p29)]

# 13. Appliances [[13](#index_split_000.html#p29)]

# 14. Reduction in IT infrastructure costs [[18](#index_split_000.html#p29)]

The following are the disadvantages of virtualization:

- Information leakage issues [[1](#index_split_000.html#p28), [13](#index_split_000.html#p29)].
- The biggest disadvantage in virtualization is overhead, as it worsens performance [[9](#index_split_000.html#p28), [13](#index_split_000.html#p29)].
- The management of different platforms and networks is the biggest problem with virtualization as they in turn increase the time complexity of networking and debugging [[9](#index_split_000.html#p28)].

![Image 8](index-22_1.jpg)

Introduction to Virtualization in Cloud Computing ◾ **7**

FIGURE 1.3 Virtualization architecture for cloud.

## 1.3.2 Virtualization Architecture for Cloud [[3–6](#index_split_000.html#p16)]

1. The OS takes full care of the underlying hardware.
2. A hypervisor/VMM in the virtualization architecture creates this illusion.
3. Virtualization is obtained with the help of virtualization software (i.e., hypervisor in [Figure 1.3](#index_split_000.html#p22)). Hypervisor is a software layer which:
   a. Allows several guest OS (virtual machines) to run on a single physical host at the same time.
   b. It can easily multiplex original hardware properties and offers hardware generalization to operating guest OSs.

## 1.3.3 Virtualization’s Significance in Cloud Computing [[7](#index_split_000.html#p16)]

1. It is possible to have a cloud without virtualization, but it would be complex and expensive.
2. The cloud creates the ideas of ‘pay for what you want’ and ‘infinite availability – use as much as you can’.
3. Only if there is a lot of versatility and reliability in the back-end are these ideas realistic. In virtualized environments, this efficiency is available.
4. Cloud computing is cost efficient when it uses virtualization.

![Image 9](index-23_1.png)

**8** ◾ ML and Optimization Models

FIGURE 1.4 Virtualization types.

## 1.3.4 Classes of Virtualization and Its Effects

Server, desktop device and disk virtualization are the three forms of virtualization. The types of virtualization techniques are shown in [Figure 1.4](#index_split_000.html#p23).

### Class A: Server virtualization

Through segmenting resources of individual servers through several networks, server virtualization enables a single server to handle the functions of several servers. The hypervisor layer provides this approach by using services in a cost-effective, highly accessible and efficient manner. Server virtualization can be categorized into three groups [[20](#index_split_000.html#p29)]:

a) Full server virtualization.
b) Para server virtualization.
c) Hardware-assisted server virtualization.

#### Full server virtualization

In full virtualization the VM gives the appearance of a virtual theater, on a physical machine within an isolated OS. For more secure and private computing the guest OS is separated from the hypervisor layer. [Figure 1.5](#index_split_000.html#p24) depicts the full and para virtualization.

#### Para server virtualization

In this virtualization, the guest operating system demands modification, to work with the hypervisor. This modified guest OS allows the hypervisor to more effectively schedule computing resources to VM, to increase performance. Hardware and software requirements depend upon the hypervisor.

**Advantages:**

- It increases noteworthy performance over other virtualization techniques.

**Disadvantages:**

- Needs modification in VM OS.

#### Hardware-assisted server virtualization

Hardware manufacturers are rapidly introducing new features to make virtualization simpler. This form of virtualization was first used in IBM’s VM/370 virtual machine, which was the first virtual machine. It accelerated the performance by reducing the maintenance overhead of the virtual machine, so this kind of virtualization is known as accelerated virtualization [[21](#index_split_000.html#p29)].

**Advantages:**

- Increase the performance.
- Products get distributed as a server OS or as a device.

**Disadvantages:**

- The vendor has to circulate a hardware compatibility list (HCL) in cloud that describes the hardware used with virtualization products [[22](#index_split_000.html#p29)].

Server virtualization has the following advantages [[22](#index_split_000.html#p29)]:

- Reduces the necessity for physical servers [[23](#index_split_000.html#p29)].
- Reduces server functioning maintenance [[24](#index_split_000.html#p29)].
- Reduces the operating expenditure [[19](#index_split_000.html#p29)].
- Reduces provisioning and the organizing of fresh services [[24](#index_split_000.html#p29)].
- Reduces disaster recovery times [[19](#index_split_000.html#p29)].
- Improves network and application security [[25](#index_split_000.html#p29)].
- Improves flexibility, availability and performance [[25](#index_split_000.html#p29), [26](#index_split_000.html#p29)].

[Table 1.1](#index_split_000.html#p25) shows the comparative study of full virtualization, para virtualization and hardware-assisted virtualization, on different parameters.

### TABLE 1.1 Comparison of Different Server Virtualization Techniques

| **Parameters** | **Full Virtualization** | **Para Virtualization** | **Hardware-Assisted Virtualization** |
| :--- | :--- | :--- | :--- |
| **Guest operating system** | Unchanged guest operating system | Changed guest operating system, so it cannot run on local hardware or another version of hardware | Unchanged guest operating system |
| **Performance** | Good performance | Better in certain cases | Good and can also increase over time, depending upon hardware improvement |
| **Used by** | VMware, Microsoft | VMware, Microsoft, Xen | VMware, Xen, IBM |
| **Dependency on guest OS hypervisor** | No | No | Xen Linux runs only on Xen Hypervisor |

Introduction to Virtualization in Cloud Computing ◾ **11**

### TABLE 1.2 Comparison of Different Types of Hypervisors and Their Virtualization

| **S. No.** | **Hypervisor Name** | **Full Virtualization** | **Para Virtualization** | **Hardware-Assisted Virtualization** |
| :--- | :--- | :--- | :--- | :--- |
| 1 | KVM | Yes | No | No |
| 2 | Proxmox VE | Yes | No | No |
| 3 | Virtual Box | No | Yes | Yes |
| 4 | XEN | No | Yes | Yes |
| 5 | Open VZ | No | No | No |

[Table 1.2](#index_split_000.html#p26) shows different existing hypervisor names and their virtualization type.

### Class B: Desktop or client virtualization [[22](#index_split_000.html#p29)]

This technology enables the system administrator to virtually update and monitor the desktop, mobile and laptop. There are many window manager programs based on X Window systems which are used to support multiple virtual desktop applications. These programs enable the user to switch between different desktops (e.g., mobile, laptop, computer desktop, etc.) and can display the output of specific applications [[13](#index_split_000.html#p29)]. Client virtualization is classified into the following three types:

1. **Remote or server hosted virtualization**: This is hosted on a server and managed by a network of clients.
2. **Local client virtualization**: The operating system is encrypted and virtualized, and it is run on a local desktop client. With the help of this kind of virtualization users are able to manage their desktop settings.
