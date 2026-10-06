# USING THE WRITE-BACK CACHE

Now we'll show you how to use one of the last features of Storage Spaces in Windows Server 2012 R2, the write-back cache. With storage tiers, you cannot enable this via the GUI; it must be done via PowerShell. Remember, the write-back cache can speed up applications because writing to cache is quick and doesn't have to wait for storage to commit the write.

The PowerShell command we used to build our storage tier and modify the name and the StorageTierSiers options. Add the -WriteCacheSize option with a size setting; in this case you want a write-back cache size of 2 GB.

```
VirtualDisk -StoragePoolFriendlyName TestPool -FriendlyTier_VDISK -StorageTiers($ssthtier) -StorageTiers($20GB, 70GB)-ResiliencySettingName Simple -WriteCacheSize 2GB
```

You will now create a virtual disk that will use storage tiers, with write-back cache enabled.

# STORAGE TIERS OPTIMIZATION

The final thing we discussed about storage tiers at the start of this chapter is that every night at 1:00 AM, it will run a job to reprioritize the storage and move around what needs to be in the fast tier versus the slow tier.

In Scheduler, choose Task Library > Microsoft > Windows > Storage Tiers Management. Task Scheduler lists a job Storage Tiers Optimization, as shown in Figure 12.51.

# FIGURE 12.51 Storage Tiers Optimization task

![](bbox=[0.166, 0.545, 0.905, 0.883])