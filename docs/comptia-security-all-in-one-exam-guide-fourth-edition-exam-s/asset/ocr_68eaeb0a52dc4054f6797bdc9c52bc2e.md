team, or elements of it, are gathered together and presented with a scenario. They can walk through their decision-making steps, communicate with others, and go through the motions of the exercise in the pattern in which they would likely be involved. The scenario is presented at a level to test the responsiveness of their decisions and decision-making process. Because the event is frequently run in a conference room, around a table, the name tabletop exercise has come to define this form of exercise.

# Fault Tolerance

Some other terms that are often used in discussions of continuity of operations in the face of a disruption of some sort are high availability and fault tolerance.

Fault tolerance basically has the same goal as high availability—the uninterrupted access to data and services. It can be accomplished by the mirroring of data and hardware systems. Should a “fault” occur, causing disruption in a device such as a disk controller, the mirrored system provides the requested data with no apparent interruption in service to the user. Certain systems, such as servers, are more critical to business operations and should therefore be the object of fault-tolerant measures.

![](bbox=[0.04, 0.51, 0.13, 0.58])

> **EXAM TIP** Fault tolerance and high availability are similar in their goals, yet they are separate in application. *High availability* refers to maintaining both data and services in an operational state even when a disrupting event occurs. *Fault tolerance* is a design objective to achieve high availability should a fault occur.

# Hardware

Hardware forms the backbone of a system in a form of infrastructure. From network equipment to the servers, storage, and user machines, the hardware is all interconnected, providing a conduit across which the data is stored, processed, and used. This equipment forms the backbone of the operations and is the location where security activities will occur. Hardware components such as network control devices, firewalls, intrusion detection systems, and logging systems are essential to providing the required levels of security.

# RAID

A common approach to increasing reliability in disk storage is Redundant Array of Inexpensive Disks, now known as Redundant Array of Independent Disks (RAID). RAID takes data that is normally stored on a single disk and spreads it out among several others. If any single disk is lost, the data can be recovered from the other disks where the data also resides. With the price of disk storage decreasing, this approach has become increasingly popular to the point that many individual users even have RAID arrays for their home systems. RAID can also increase the speed of data recovery, as multiple drives can be busy retrieving requested data at the same time instead of relying on just one disk to do the work.