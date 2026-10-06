# 1574 CHAPTER 32 WINDOWS SERVER 2012 R2 AND ACTIVE DIRECTORY BACKUP AND MAINTENANCE

FIGURE 32.8

Creating an Active snapshot

```
Administrator: C:\Windows\system32\cmd.exe - ntdutil
Microsoft Windows (Version 6.2.7601)
(C) 2012 Microsoft Corporation. All rights reserved.
C:\Administrators\Administrator> ntdsutil
tdssnapshot: activate instance ntds
Building instance is "ntds"
Creating snapshot...
snapshot: {c66b1272-68b6-44c1-adf9-d798bc685efe} generated successfully.
snapshot:-
```

+   6. Type quit and press Enter to exit snapshot mode, and then type quit and press Enter to exit Ntdutil.exe.

# Mounting an Active Directory Snapshot

You won't be able to use an AD DS snapshot until you have mounted it. Mounting takes the snapshot and makes it available as a local path on the server computer. Once it's mounted, you can access the AD files in the NTDS folder under Windows.

+   1. Open an elevated command prompt.

+   2. Type ntdsutil, and press Enter.

+   3. Type Snapshot, and then press Enter.

+   4. At the snapshot prompt, type Activate instance NTDS, and then press Enter.

+   5. List All, and press Enter.

This will display all the snapshots currently on the server computer. Each entry will have an index number and then display the GUID of the snapshot.

+   6. Mount x, where x is either the index number or the GUID of the snapshot you want to mount, and then press Enter.

If the command completes successfully, it will return the local path of the snapshot-typically folder off the C drive. The result should be similar to Figure 32.9.

+   7. Type quit and press Enter to exit snapshot mode, and then type quit and press Enter to exit Ntdutil.exe.

# Working with Mounted Active Directory Snapshots

After you have created and mounted an Active Directory snapshot, you need to make it available by using the Dsmain.exe command. Dsmain.exe is installed on Windows Server 2012 R2 with the AD DS role or the Active Directory Lightweight Directory Services (AD