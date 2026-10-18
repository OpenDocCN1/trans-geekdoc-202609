+   - **.vmdk:** This is the actual virtual hard drive for the virtual guest operating system. Virtual hard drives can be fixed or dynamic. Fixed virtual hard drives remain the same size. Dynamic virtual hard drives expand as needed.
+   - **.vmem:** This is a backup of the virtual machine’s paging file/swap file. This can be very important to a forensic investigation.
+   - **.vmsn:** These are VMware snapshot files, named based on the name of the snapshot. A VMSN file stores the state of the virtual machine when the snapshot was created.
+   - **.vmsd:** A VMSD file contains the metadata about the snapshot.
+   - **Oracle VirtualBox:**
+     - **.vdi:** These are VirtualBox disk images called virtual disk images.
+     - **/config/VirtualBox:** This is a hidden file that contains configuration data.
+     - **.vbox:** This is the machine settings file extension. Prior to version 4.0, it was .xml.
+   - **Virtual PC:**
+     - **.vhx:** These are the actual virtual hard disks. They are obviously quite important to a forensic examination.
+     - **.bin files:** These contain the memory of the virtual machine, so these absolutely must be examined.
+     - **.xml files:** These files contain the virtual machine configuration details. There is one of these for each virtual machine and for each snapshot of a virtual machine. These files are always named with the GUID used to internally identify the virtual machine in question.

# Cloud

A cloud has been defined as “a pool of virtualized computer resources.”

People often speak of the cloud as if there were only one cloud, or at least one type of cloud. This impression is inaccurate. There are multiple clouds and multiple types of clouds. Any organization with the appropriate resources can establish a cloud, and it may establish it for diverse reasons, leading to different types of clouds.

Public clouds are defined by the NIST as those clouds that offer their infrastructure or services to either the general public or at least a large industry group.

Private clouds are those used specifically by a single organization without offering the services to an outside party. There are, of course, hybrid clouds that combine the elements of a private and public cloud. These are essentially private clouds that have some limited public access.

Community clouds are a midway point between private and public. These are systems wherein several organizations share a cloud for specific community needs. For example, several computer companies might join to create a cloud devoted to common security issues.

A cloud system depends on several parts. Each of these could be a location for evidence:

+   - **Virtual storage:** The virtual servers are hosted on one or more actual/physical servers. The hard drive space and RAM of those physical servers is partitioned for the various virtual servers’ usage.
+   - **Audit monitor:** There is usually an audit monitor that monitors usage of the resource pool. This monitor will also ensure that one virtual server does not/cannot access data of another virtual server.
+   - **Hypervisor:** The hypervisor mechanism is the process that provides the virtual servers with access to resources.
+   - **Logical network perimeter:** Since the cloud consists of virtual servers, not physical ones, there is a need for a logical network and a logical network perimeter. This perimeter isolates resource pools from each other.