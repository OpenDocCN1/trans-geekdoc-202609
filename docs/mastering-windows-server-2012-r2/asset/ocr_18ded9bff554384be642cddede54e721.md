# CHAPTER 2 INSTALLING AND UPGRADING TO WINDOWS SERVER R12

| Pass | Component | Property | Value |
|---|---|---|---|n| 1 | AMD64_Microsoft-Windows-Setup\DiskConfiguration\Disk | DiskID | 0 |
| | | WillWipeDisk | True |

This Disk subcomponent that you are adding to the answer file in pass 1 extends the installer to manage Disk 0 in the server. In Microsoft-speak Disk 0 is the first disk in the computer. You also have told the installer to wipe this disk.
In the Answer File pane, you should expand the Disk subcomponent. Extend subcomponents called CreatePartitions and ModifyPartitions. Right-click each of those two subcomponents and select Insert New. This will allow you to create a volume on your newly wiped Disk 0 and format it using the following subcomponent property settings:

| Pass | Component | Property | Value |
|---|---|---|---|n| 1 | AMD64_Microsoft-Windows-Setup\DiskConfiguration\Disk\CreatePartitions\CreatePartition | True |
| | | Order | 1 |
| | | Type | Primary |

You are instructing Windows Installer to create a partition and extend it, in order words, fill the entirety of Disk 0 with the new volume. Order instructs the installer to label the volume as 1 because you will refer to this label in a moment.
You might not want to fill Disk 0 with one partition because it is signed by the setting Extend = True. You can instead set size to whatever size in megabytes you want partition 1 to be, such as 40960 for a 40 GB volume. You should not set a value for size and Extend = True because that would cause a conflict.

| Pass | Component | Property | Value |
|---|---|---|---|n| 1 | AMD64_Microsoft-Windows-Setup\DiskConfiguration\Disk\CreatePartitions\ModifyPartition | Active | True |
| | | Format | NTFS |
| | | Label | Windows |
| | | Letter | C |
| | | Order | 1 |
| | | PartitionsID | 1 |

Here you can see where we refer to Order again. You are instructing the installer to format the previously created volume. It is set up as partition 1 using PartitionsID. In Microsoftspeak, partition 1 is the first partition; there is no partition 0. You set the volume as Active because you want to be able to boot from it. You format it with NTFS, label the volume as Windows, and give it the letter C.