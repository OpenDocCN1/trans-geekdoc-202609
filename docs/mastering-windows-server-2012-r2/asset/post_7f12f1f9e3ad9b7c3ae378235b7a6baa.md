
# CHAPTER 12 WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SAN ABILITIES, AND BETTER TOOLS

Once you choose File and Storage Services, you will see all the related options to this menu, including Storage Pools, as shown in Figure 12.7.

Click Storage Pools will bring you into the main configuration. Take a look at Figure 12.8.

## FIGURE 12.7 Suboptions for File and Storage Services
(img/41a8320e690a3726203b8cea7_0.png)

## FIGURE 12.8 Storage Pools
(img/41a8320e690a3726203b8cea7_1.png)

This is the main configuration window, split into three main areas:

**Storage Pools** This area contains a section called Storage Spaces, and under it is listed primordial. By default, all disks assigned to the primordial pool. As you work with Storage Spaces you will notice the primordial pool will disappear when all disks have been assigned. As you can see, there are no other pools configured yet. In the top-right corner of this area, Tasks is the option to create a new storage pool. You can right-click the primordial pool and examine its properties.

**Virtual Disks** Virtual disks represent the volumes you create inside a storage pool. Remember, this is not a VHD or VHDX. You cannot create a virtual disk inside the primordial pool; you must create a storage pool.

**Physical Disks** Physical disks are the disks available to assign. A disk can be assigned to only one pool at a time. If you right-click on a disk in this list you get the option to toggle off to help find which disk you are working on; this will only work if the storage is SCSI compliant. It also works if a drive is failing and will communicate with Storage Spaces to let the administrator know what is happening.

Using PowerShell

As mentioned, you can use PowerShell cmdlets to quickly provide Storage Spaces. Administrators prefer to work with the command-line environment when administering servers. Windows 2012 has a PowerShell module called Storage which contains all the cmdlets you need to work with.

In Windows 2012 and above, the PowerShell module is automatically imported when you attempt to call a cmdlet from that module. To review the cmdlets available to you under the Storage module, open an elevated PowerShell window and run get-command Storage. Not all are storage related, but we are going to show you sample output from a couple of cmdlets. For example, type get-storagepool and observe the output. Now type get-storagepool | fl and see the difference. FL is an alias in PowerShell which stands for Format-List; the option determines which properties you want to display, * stands for All Properties. The output is shown in Figure 12.10. Repeat for the cmdlets get-physicaldisk and get-virtualdisk and observe the output.

## FIGURE 12.9 Storage cmdlets

```powershell
PS:\Users\Administrator> get-command *StoragePool* | where {$_.ModuleName -eq 'Storage'}
CommandType  Name                ModuleName
Function     Get-StoragePool     Storage
Function     New-StoragePool     Storage
Function     Set-StoragePool     Storage
Function     Update-StoragePool  Storage
```

## FIGURE 12.10 Sample output for storagepool
```powershell
PS C:\Users\Administrator> get-storagepool
PrimordialName  OperationalStatus  HealthStatus  Primordial  IsReadOnly
StoragePool     OK                  Healthy        True          False
PS C:\Users\Administrator> get-storagepool | fl
PrimordialName  OperationalStatus  HealthStatus  Primordial  IsReadOnly
StoragePool     OK                  Healthy        True          False

Properties:
Name: StoragePool
OperationalStatus: OK
HealthStatus: Healthy
IsPrimordial: True
IsReadOnly: False
TypeId: Unknown
Access: Unknown
FriendlyName: StoragePool
IsDetached: False
IsRetired: False
IsProvisioned: False
HealthStatus: OK
FaultStatus: None
Description: Unknown
OSSystem: Windows Server 2012
StoragePoolType: StoragePool
StoragePoolFriendlyName: Storage
Capabilities:
{
    Location:
    {
        Path: C:\
    }
    Disk:
    {
        0
    }
}
ResourceType:
{
    Type: StoragePool
}
ObjectType:
{
    Name: StoragePool
}
... (repeated properties)
```
