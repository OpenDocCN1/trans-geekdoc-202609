
# Steps to implement storage solution

Generally, more than one storage volumes are configured for an application. For ease of management some storage vendors allow to create an additional storage object called volume collection, volume set or volume group, which comprises set of virtual volumes in it. A volume set relates to an application.

Similarly, another object called host collection, host set or host group for set of hosts in it. A host set maps to host’s cluster.

If a volume set is assigned to a host, all the volumes in it gets assigned to the host with a unique `LUN` ID. Again, when a volume set is assigned to a host set, all the volumes in it get assigned to all the hosts.

Typically each management software can be accessed through multiple interfaces, such as `GUI`, `CLI` for performing operations in batch through script and `REST` API, which is platform independent can initiate create, read, update, and delete (`CRUD`) operations.

Storage management software have several other features such as reporting and alerting capabilities, unified management console that allows the administrator to manage multiple storage systems through a single pane of glass (`SPoG`), integration with other software solutions, and so on.

Typically four steps are to be followed to implement a storage solution:

![](images/Fig_9.2.jpg)
![Figure 9.2: Steps to implement a storage solution and storage solution architecture](images/Fig_9.3.jpg)

Figure 9.2: Steps to implement a storage solution and storage solution architecture

There are various storage solutions available to meet different purposes. Following three are commonly seen configurations:

- SAN storage connected to multiple hosts in cluster
- Storage connected to host server via `iSCSI`
- File storage connected to `SMB` and `NFS` client systems

## SAN storage connected to multiple hosts in cluster

In `SAN` environment, fabric comprises of one or more `FC` switches. Following is brief description of each step to implement `SAN` storage solution.

### Physical cabling

- Connect the cable between storage and `FC` switches.
- Connect cable between host servers and `FC` switches.
- Label each cable. This is most important for troubleshooting any issue in future.

### Configuring switches

- Identify `WWPN` of `FC` `HBA`
  - Refer product document to determine worldwide port number (`WWPN`) of `N_Port` device connected to fabric
- Create aliases
  - Assign meaningful name to each `WWPN`
- Create zone
  - Follow zoning best practices as per the product documents to provide desired access
- Create configuration or zone set and enable it

### Configuring storage

- Creation of host
  - Host is a logical entity in storage that represents the host server, which is going to access the virtual volume. Typically host requires `WWPN` of `FC` `HBA`s or `IQN` number of `iSCSI` initiator adapters and operating system name running on it. Some storage vendor may require additional information for creation of host.
  - In case of cluster environment multiple hosts may have to be created.
- Creation of virtual volume
  - Virtual volume is the logical disk that is created on storage system to provide access to host for storing data and read/write operations.
- Export or presentation or assign the virtual volume to the host
  - The `LUN` masking provides access of the virtual volume to the host. In case of cluster, single virtual volume is needed to be accessed to multiple hosts in cluster.

Generally more than one storage volumes are configured for an application. For ease of management some storage vendors allow to create an additional storage object called volume collection, volume set or volume group, which comprises set of virtual volumes in it. A volume set relates to an application.

Similarly another object called host collection, host set or host group for set of hosts in it. A host set maps to hosts cluster.

If a volume set assigned to a host, all the volumes in it gets assigned to the host with unique `LUN` ID. Again when a volume set assigned to a host set, all the volumes in it gets assigned to all the hosts.

### Configuring host servers

- Scan for new disk
- Create file system
- Mount file system

Follow the operating system and application documentation to configure your disk and file system.

## Storage connected to host server via iSCSI

### Physical cabling

- Connect cable between storage and Ethernet switches.
- Connect cable between host servers and Ethernet switches.
- Label each cable.

### Configuring Ethernet switches

- Create `VLAN`.
- Follow `VLAN` best practices as per the product documents to provide desired access.

### Configuring storage

- Identify `IQN` number of `iSCSI` initiator adapter. Refer product documentation to determine the `IQN` number.
- Creation of host.
  - Specify `IQN` number to create an `iSCSI` host in storage:
- Creation of virtual volume.
- Export or presentation or assign the virtual volume to the host.

### Configuring host servers

- Open `iSCSI` initiator console or `CLI` interface and login to `iSCSI` target
- Once login is successful, scan for new disk
- Create file system
- Mount file system

Follow operating system and application documentation to configure your disk and file system.

## File storage connected to SMB and NFS client systems

Physical cabling and Ethernet switch configuration is the same as `iSCSI` described above.

### Configuring file server storage

- Create `SMB` or `NFS` share. Refer product documentation for exact steps to create shares.
- Assign permission to share for desired user.

### Configuring file share client

- Mount the `SMB` or `NFS` share using `\\Server IP or Hostname\<Share name>`
- Supply username and password to access the share.

# Conclusion

All storage vendors develop and provide suite of software that manages the storage system as well as the solution.

Primary purpose of any management software of a storage system is to provision and configure the storage system and also monitor health of the storage system. For example, storage administrator uses this software to create a storage volume and monitor connection status of all the ports of the storage controllers.

Apart from storage system management software there is other management software that helps to configure and perform local and remote replications; backups monitor storage live and past performances, and so on.

Typically there are four fundamental steps to configure and access a storage system’s virtual volume such as cable, configure switches, create virtual volume and configure host server to access the volume.

# Case studies

## Case study 1: Provisioning storage space to a Linux host server

Let us provision storage space to a Linux host server:

### Requirement

A Linux host is connected to a `SAN` storage. Network and `SAN` zoning are already configured. Provide steps to create and configure storage volume in host server via `FC` and `iSCSI`.

### Analysis

Following steps are followed to provision storage space to a host in the storage system:

Step 1: Creation of a host entry.

Step 2: Creation and presentation of virtual volume to the host in the host server: Although there are several methods available or third party tools available, configure file system on a storage volume, typically these steps are followed using Linux native command and utilities.

Step 3: Scan for new disk:

```
find /sys/class/scsi_host/host*/scan | while read line; do echo - - - > $line; done
```

Step 4: Listing all devices:

```
fdisk -l
```

Step 5: Partitioning disk:

```
fdisk <device file>
```

Step 6: Creating file system:

```
mkfs <device file>
```

Step 7: Mounting file system:

```
mount <device file> /<mount point>
```

### Solution

Step 1: Creation of a host entry:

A host entry must be created in storage for the first time configuration for a host server. To create a host entry, couple of information is important:

- `WWPN`s of `FC` `HBA`, `IQN` name for `iSCSI` or `NQN` of `NVMe` subsystem
- Operating system
