
### 16. If your original `DC` is also a `GC`, the warning dialog appears. In either case, click Yes to indicate that you are sure you want to transfer this `FSMO`.

### 17. After some mulling over by the `DC` and of course the failure to find the existing `FSMO`, you are presented with a nice message specifying that this `FSMO` can be forced, if we so choose (see [Figure 7.42](#B9781931836944500131.xhtml#f0215)). We so choose, so click Yes.

![Figure 7.42 FSMO Holder Could Not Be Found](images/B9781931836944500131/f07-42-9781931836944.jpg)

Figure 7.42 FSMO Holder Could Not Be Found

### 18. A nice dialog appears indicating success. Click OK and then Close the dialog.

Now, what to do about that other `DC` that is only offline physically? You are one plug away from domain chaos. If you re-insert the network plug, you will have two Infrastructure `FSMOs` in the same domain. Depending on the `FSMO` in question, the chaos will vary. With the Infrastructure `FSMO`, symptoms might not be readily apparent because its role is more interdomain than intradomain. In our example, it is a single domain forest so the Infrastructure `FSMO` is not used. An interesting note is that depending on which `DC` you ask, the Infrastructure `FSMO` is in a different location. According to our `tekease-dc1` `DC`, the Infrastructure `FSMO` is on `tekease-dc1`, which we just forced in the exercise. After bringing `skyline` `DC` back online and asking it, the answer was that the `skyline` `DC` holds the infrastructure `FSMO`. What happens in 15 minutes when these two `DCs` compare notes?

## Summary of Exam Objectives

This objective of this chapter is to teach you how to manage domain controllers (`DCs`) and operation masters (also called Flexible Single Master Operations, or `FSMOs`). Planning your `DCs` requires an understanding of what `Active Directory` is. `Active Directory` is the `NTDS` database containing the domain hierarchical structure, users, groups, and permissions. `DCs` are special servers that have been promoted to that role after having `Windows Server 2003` installed. The `DC`(s) on your network play an administrative role in maintaining the domain. Such functions as user logon authentication and `Active Directory` replication make up the bulk of the `DCs`’ responsibilities.

`DC` planning requires knowledge of your geographical and site structure, the number of users, groups, and computers on your network (both current and planned), and the amount of network traffic. These items, combined with the physical limitations of the computer running as a `DC`, control how many `DCs` you’ll need and where you’ll place them.

`DCs` are created from one of two types of servers: standalone or member (the server type is selected when you install `Windows Server 2003`). To create a `DC`, run the `Active Directory Installation Wizard` (`dcpromo`). Beyond the minimum hardware requirements, a `DC` requires a DNS server that supports both `SRV` records and dynamic updates. Creating additional `DCs` requires the same `ADIW`, but you must have access to a parent `DC` and know the credentials for an administrative account on that `DC`.

Backing up your `DC` consists of backing up two parts: the data that is stored on it, and the system state. The system state includes the Registry, and on a `DC` includes the `Active Directory` database. To back up the system state to a tape device, the device must be directly (locally) connected. The system state can only be restored back to the same `DC` from which it was backed up.

`FSMOs` are also referred to as operation masters. `FSMOs` handle required system operations that control the domain naming and internal infrastructure of your domains. By default, these `FSMOs` are automatically installed and managed by the domain, but if you need to move them or if you lose them, there are ways to manually manage them.

The `Schema Master` is managed through the `Active Directory Schema` tool. The `Active Directory Domains and Trusts` tool is used to transfer the Domain Naming `FSMO`. For the remaining domainwide operation masters, `PDC Emulator`, `RID`, and `Infrastructure`, use the `Active Directory Users and Computers` tool. As long as the existing `FSMO` is available, these `FSMOs` move to the designated new `DC` smoothly. Should a `FSMO` be lost, your domain will not function fully, and depending on which operation master is lost, your domain might not function at all. To force the creation of a new `FSMO`, use the `ntdsutil` from the command prompt.

## Exam Objectives Fast Track

### Planning and Deploying Domain Controllers

☑ Plan to have at least one `DC` per site. Sites keep the domain from flooding the WAN, so a `DC` at each site keeps the replication traffic off the WAN as well.

☑ The number of `DCs` to deploy is based on the number of users, geographic location, and fault tolerance. Each `DC` can handle 5000 objects, but you should have a second `DC` on the network in case the first `DC` crashes. A second `DC` also improves the network load by balancing the number of objects, changes, and authentication requests between the two `DCs`.

☑ If a `DC` is overloaded with account activity, you can add another `DC` or improve the hardware of that `DC`. Adding RAM is usually the first choice.

☑ `DCs` are created by promoting a server. Run `dcpromo` (`Active Directory Installation Wizard`) to do this.

☑ The first `DC` you create is the domain, tree, and forest all in one. Additional `DCs` are created using the same `ADIW` tool.

### Backing Up Domain Controllers

☑ `DCs` contain the `Active Directory` database and need to be backed up daily.

☑ The `Active Directory` is stored in the system state on a `DC`, so to back up the `Active Directory`, you must back up the system state.

☑ Backup of a `DC`’s system state requires a direct connection to the `DC`. This means that the backup program must run on the `DC`, and if you are backing up to a tape drive, the drive must be locally connected.

☑ A backup of a `Windows Server 2003` `DC` can be used to create additional `DCs` in the same domain. This is useful for creating `DCs` at remote sites.

### Managing Operations Masters

☑ Operation masters are also known as Flexible Single Master Operations (`FSMO`).

☑ `FSMOs` fulfill services that must be assigned to one `DC` and cannot be shared like all other `Active Directory` objects.

☑ There are two forestwide operation masters:

■ `Schema Master` controls all modifications to the schema. This `FSMO` must be accessible whenever the schema is extended. The schema is usually extended by applications that are Directory enabled, Microsoft Exchange is a good example of a Directory-enabled application,

■ `Domain Naming Master` directs the naming of any domains within the forest. It ensures that names are unique. This `FSMO` must be accessible when you create a new domain anywhere in the forest.

☑ There is only one `Schema` and one `Domain Naming` `FSMO` for the entire forest.

☑ There are three domainwide operations masters:

■ `PDC Emulator` has three responsibilities. It acts as the `PDC` for all `Windows NT 4` `BDCs`. It is also the central depository for all password and account lockouts. This means that any change to a password or account lockout is immediately delivered to the domain’s `PDC Emulator`. If a `DC` determines that an account is locked out or the password is incorrect, the `DC` will consult its `PDC Emulator` to see if there is a change that it just has not yet received. Finally, the `PDC Emulator` is used by Microsoft to be the timekeeper for each domain. This ensures that all `DCs` use a common time when sharing information, and is used to determine the order in which changes that might conflict occur. The first `PDC Emulator` created in your forest is the master timekeeper for all other `PDC Emulators`.
