# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

FIGURE 12-47

Sample output of get-hysical disk for creating storage tiers

| PhysicalDisk | MediaType | FriendlyName | OperationalStatus | HealthStatus |
|---|---|---|---|---|
| Disk0 | SSD | Disk0 | OK | Healthy |
| Disk1 | SSD | Disk1 | OK | Healthy |
| Disk2 | HDD | Disk2 | OK | Healthy |
| Disk3 | HDD | Disk3 | OK | Healthy |

# CREATING SSD AND HDD POOLS

As you can see, we have SSD and HDD drives in our environment. Now we'll create our storage tiers. We're creating two tiers in our example (which is also the maximum), and then we'll create a virtual disk that will be allocated across the tiers. We will partition and format the disk for use:

```
$ssdtier = new-StorageTier -StoragePoolName "TestPool" FriendlyName SSD_Tier -Mediatype SSD
```

For the HDD tier we use the following syntax:

```
$hddtier = new-StorageTier -StoragePoolName "TestPool" FriendlyName HDD_Tier -Mediatype HDD
```

The next step is to create a virtual disk and tie it to the storage tiers. After you whether you can remap an existing virtual disk to a storage tier, the answer is no.

With in mind, we'll create a virtual disk, which we will tie to our storage tiers. Here is the syntax to use:

```
New-VirtualDisk -StoragePoolName TestPool -FriendlyName Tiered_VDisk -StorageTiers(@ssdtier, $hddtier) -StorageSizes(@10GB, 50GB) -ResiliencySetting Simple
```

FIGURE 12-48

Output of creating a virtual disk in storage tiers

| FriendlyName | ResiliencySetting | OperationalStatus | HealthStatus | IsManualAttach | Size |
|---|---|---|---|---|---|
| Tiered_Disk | Simple | OK | Healthy | False | 60 GB |

Most of the options will be familiar from creating a virtual disk earlier. However, we have two options to relating a virtual disk in a storage tier:

StorageTiers(@ssdtier, $hddtier) specifies the tiers you can use. This is not a hash table, so be careful not to use curly brackets. We have stored our tiers in separate variables for ease of reference.

StorageSizes(@10GB, 50GB) specifies the size of each tier and is referenced in the order you use in the -StorageTier option. As you can see in Figure 12-48, the total size is 60 GB, which is 10 GB + 50 GB.