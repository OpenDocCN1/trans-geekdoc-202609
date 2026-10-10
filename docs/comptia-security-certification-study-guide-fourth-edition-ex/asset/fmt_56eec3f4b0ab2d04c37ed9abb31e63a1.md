
If one of the disks in the mirror fails, you can replace the failed disk by breaking the mirror, adding a new functioning disk, and then rebuilding the mirror from the existing disk that did not fail. Once you have reestablished the mirror, you have your fault tolerance back.

[Figure 18-3](#ch18.xhtml#ch18fig3) displays the concept of a mirrored volume. When a user saves data to a mirrored volume, the data is written to both disks that make up the volume.

![Image](f0723-01.jpg)

**FIGURE 18-3**

A mirrored volume stores a copy of the saved data on both disks.

**EXERCISE 18-3**

![Images](video.jpg)

**Creating a Mirrored Volume on a Windows Server**

In this step-by-step procedure, you create a mirrored volume on a Windows Server by using two of the dynamic disks created in the preceding exercise. Remember that a mirrored volume stores all the data on both members (disks) in the volume.

1. Log on to ServerA and then launch the Computer Management console.
2. In the Computer Management console, select Disk Management on the left side under Storage.
3. Right-click an area of unallocated space on disk 1 and choose New Mirrored Volume.
4. The New Mirrored Volume Wizard appears. Click Next.
5. Add disk 2 as a selected disk for the mirrored volume, and type `200` in the Select the Amount of Space in MB box. Also notice that the total space used by the volume is 200MB as well (instead of the 400MB in the case of a striped volume). With a mirrored volume, there is 200MB per disk, but you can store only 200MB—the other 200MB is to store a copy of the data in case of disaster.
6. Click Next.
7. Assign `M` as the drive letter and click Next.
8. Type a Volume Label of `Mirrored` and choose the Perform a Quick Format option. Click Next to format for NTFS.
9. Click Finish. The mirrored volume is created. Notice that the legend in Disk Management displays the color codes for each volume type.

As mentioned, RAID 1 is known as disk mirroring because the data is duplicated across two different disks but using only one disk controller. When using two disk controllers, each with a hard disk connected to it, we term the RAID 1 solution `disk duplexing` rather than disk mirroring. [Figure 18-4](#ch18.xhtml#ch18fig4) shows the difference between disk mirroring and disk duplexing. Both are considered RAID 1.

![Image](f0724-01.jpg)

**FIGURE 18-4**

Disk mirroring versus disk duplexing

![Image](exam.jpg)

**RAID 1 is known as disk mirroring, which “mirrors,” or stores, a full copy of the data on a second disk in case the first disk fails. Disk mirroring is when you have two drives connected to a single controller, whereas disk duplexing, which is a form of mirroring, is when the two drives are connected to different controllers.**

### RAID 5

RAID 5 is known as `striping with parity` because a RAID 5 volume acts as a RAID 0 volume but adds the parity information to create redundancy. RAID 5 volumes write data to all disks in the volume but store redundant information on one of the disks per stripe (a `stripe` is a row made up of 64KB chunks on each disk, as shown in [Figure 18-5](#ch18.xhtml#ch18fig5)). For example, when you save data to a RAID 5 volume made up of four disks, the data is split into 64KB data chunks (that may change, depending on the product or implementation) and written to each disk (let’s say disks 0, 1, and 2). But disk 3 will store redundant data (parity data) of the three 64KB blocks that have been saved already. If the three 64KB blocks are not sufficient to complete saving the file, the save operation will continue onto the next row. There will be parity information for that row as well, but the parity information is stored on a different disk for each row.

![Image](f0725-01.jpg)

**FIGURE 18-5**

A RAID 5 volume stripes the data and stores parity information.

**EXERCISE 18-4**

![Images](video.jpg)

**Creating a RAID 5 Volume on a Windows Server**

In this exercise you see how to create a RAID 5 volume on a Windows Server by using three drives. Remember that a RAID 5 volume is similar to a striped volume, but it also stores redundant information for each stripe that is written.

1. Log on to ServerA and launch the Computer Management console.
2. In the Computer Management console, select Disk Management on the left side under Storage.
3. Right-click an area of unallocated space on disk 1 and choose New RAID-5 Volume.
4. The New RAID-5 Volume Wizard appears. Click Next.
5. You now need to choose the disks that will participate in the striped volume solution. Select disks 2 and 3 on the left and click Add to add to the striped volume. Notice that the disk you started the volume on was already selected as a member of the volume. Because we started the volume on disk 1 and added disk 2 and disk 3, we will have three disks in this solution.
6. Once you have added each disk, at the bottom of the dialog box, type the amount of space you want to use on each disk for the volume. Type `200` and notice that each disk will use 200MB—for a total of 400MB for the entire volume, because a third of the space is used for parity and is not actual usable space.
7. Click Next.
8. Assign a drive letter of `R` for RAID-5 Volume.
9. Click Next.
10. Click Next to format for NTFS.
11. Click Finish; the new RAID-5 volume has been created. Notice that drive R: shows multiple times because it is made up of multiple disks.
12. Close all windows.

If one of the disks fails, with a RAID 5 volume you can still access the data, but you may want to replace the faulty disk. To recover from a disk error with RAID 5, you simply replace the failed disk and regenerate the volume so that the data on the failed disk is created on the newly added disk.

![Image](exam.jpg)

**RAID 5 volumes are known as striping with parity because this volume type splits the data across all disks but saves parity data on one of the disks per stripe. The parity information is used to calculate the missing data if a disk in the RAID 5 volume fails.**

## CERTIFICATION OBJECTIVE 18.04

## Understanding High Availability

It is important to understand that having a RAID array does not ensure that your users can gain access to the data. For example, if you have an e-mail server that is connected to the RAID array, as shown in [Figure 18-6](#ch18.xhtml#ch18fig6), notice that the clients connect to the e-mail server to retrieve the data and not directly to the RAID array. What if the e-mail server fails? Although you have the e-mail data on a RAID array, the users are unable to get to that data because they must make the request through the e-mail server.

![Image](f0726-01.jpg)

**FIGURE 18-6**

Identifying the need for high availability

`High availability` is ensuring that clients can always gain access to the services they need, whether it be an e-mail server, database server, or WAN link. To have high availability, you must first identify all of your single points of failure and then create redundancy in those areas. The following are some key areas where single points of failure are found:

- **Servers** Servers providing network services such as e-mail or a web site are a single point of failure. Clustering or load balancing can be used to provide high availability of these services. Clustering typically provides high availability to a back-end server that maintains data, such as a database server. Load balancing is a way to add scalability to your solution (along with high availability). For example, if you are load balancing your web site across two web servers and then your company web site gets really popular, scalability is the fact that you can add more servers to the load-balanced solution so that the workload is divided among all servers in the load-balanced solution.
- **Hard drives** Hard drives store our valuable company data and are a single point of failure. You can use RAID to provide fault tolerance to the drives.
