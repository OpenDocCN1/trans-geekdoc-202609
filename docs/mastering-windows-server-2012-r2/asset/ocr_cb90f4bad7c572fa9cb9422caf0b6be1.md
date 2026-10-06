# UNDERSTANDING VIRTUAL DISKS 1373

These options are all accessed from the Edit Virtual Hard Disk Wizard. If you do a lot of testing using differing disks, you will be at some point wanting to create stand-alone disks, because a much-used differing disk will be larger than its parent—exactly the situation you wanted to avoid. We'll show an example. Say you have a differing disk called vhd, and you want to create a new; independent virtual disk. Again, for such procedure, the VM must be turned off.

+   1. From the Actions on the Hyper-V management console, start the Virtual Hard Disk Wizard.
2. Locate the disk you want to merge, which is differing.vhd in this example.

The wizard will determine that it's a differing disk and present you with the relevant options only.

+   3. From the Action dialog box, select the Merge option.
A sub-dialog box appears giving you two options: Do you want to merge the differing disk into its parent, or do you want a new dynamic or fixed differing disk? It will be really careful when merging a disk into its parent any other child disks will be invalidated.

+   4. For testing, you will want to create a new dynamic disk: Choose a suitable name, such as server-name-dynamic.vhd, as shown in Figure 27.20.

+   5. Click Next, and then click Finish to start the actual procedure.

+   6. To use the new disk, edit the virtual machine properties and replace the current-differencing disk.

FIGURE 27.20
Merging a differing disk and its parent to a new (dynamic) virtual hard disk

![](bbox=[0.347, 0.558, 0.905, 0.893])