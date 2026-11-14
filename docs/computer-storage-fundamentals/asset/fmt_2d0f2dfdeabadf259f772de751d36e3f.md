
# Virtual Volume Family and Snapshots

Virtual volume along with all its snapshots is called virtual volume family.

Depending on the storage system design, vendors set the maximum limit of the number of snapshots that can be created for a virtual volume.

![Figure 7.11: Snapshot of snapshot](images/Fig_7.11.jpg)

*Figure 7.11: Snapshot of snapshot*

## Clone

The clone is another technology to create a copy of the data on a virtual volume. The clone is the same as a snapshot at the time of creation, but data blocks get copied in the background and eventually, the clone becomes a separate and independent volume from the parent volume.

![Figure 7.12: Clone creation](images/Fig_7.12.jpg)

*Figure 7.12: Clone creation*

### Step A

As a first step of clone creation, all blocks point to corresponding blocks in the parent volume. This is similar to a snapshot.

Some vendors allow host access to the clone at this stage itself.

### Step B

After the creation of the clone, blocks start copying from the parent to the newly created clone volume in the background. Depending on the size of the volume, the data in it, and the system load, this process may take a significant amount of time.

![Figure 7.13: Background copy process](images/Fig_7.13.png)

*Figure 7.13: Background copy process*

### Step C

Once the background copy process is completed, the clone becomes separate and independent from the parent volume. Now, the clone will have the same data as the parent volume at the time of the clone's creation.

![Figure 7.14: Clone separation](images/Fig_7.14.jpg)

*Figure 7.14: Clone separation*

Since the clone is an independent volume from the parent, the primary advantage of a clone compared to a snapshot is that it provides protection of data even in the case of physical failures of the parent volume. However, for successful creation of a clone, an amount of free space equal to that of the parent volume is needed in the storage system.

### Clone Sync Operation

Most modern storage systems also allow synchronous operation of a clone to its parent volume at regular intervals, just to copy the difference in data since it was last synced. For example, a clone was created on Monday at 10:00 PM; when it is synced with the parent on Tuesday at 10:00 PM, instead of copying the entire data again, only the blocks that have changed since Monday 10:00 PM to Tuesday 10:00 PM are copied. The clone can be synced again on Wednesday, and so on.

During a sync operation, the application must be stopped and the host must discontinue accessing the clone volume. This sync process helps applications that use the clone for analysis or report generation have access to up-to-date data without creating a new clone every time.

## Remote Replication

Technologies that copy data from one storage system to another are called remote replication. This is typically implemented between two storage systems that are geographically apart. In case a disaster strikes, such as a flood, earthquake, or fire at either site, the application can switch over to the surviving site and continue its operations. Therefore, a remote replication solution is also referred to as a disaster recovery solution. Large enterprise organizations, which deal with business-critical applications, implement this solution to ensure their business continuity in case of any disaster.

![Figure 7.15: Storage remote replication](images/Fig_7.15.png)

*Figure 7.15: Storage remote replication*

Different vendors use different terminologies to name this pair of storage systems, such as source and target, local and remote, primary and secondary storage pairs.

Hosts write data to the virtual volumes in the source array, and the array copies the data to the virtual volumes in the destination array. I/O ordering is important to maintain across the virtual volumes used by an application. A replication group is a logical entity that consists of source and target virtual volume pairs. This concept is to configure an application's data on all the virtual volumes in a replication group. A replication group ensures I/O consistency on the destination array in the event of a failure of the source array.

In the following example, `S_Vol1` and `T_Vol1` volumes of the same size make a replication pair, and `S_Vol2` and `T_Vol2` also make another replication pair, and so on. An application can be configured to use multiple volumes. For example, a database requires a minimum of three volumes for data, log, and archive. In this case, one replication group needs to be configured, consisting of three replication pairs for data, log, and archive.

![Figure 7.16: Replication group concept](images/Fig_7.16.png)

*Figure 7.16: Replication group concept*

In replication, failover reverses the replication direction for a replication group. The destination array assumes the role of the source, and the source array assumes the role of the destination. Similarly, failback sets the replication direction back to the original. Failover and failback are done as part of planned maintenance or after any unplanned failures.

A storage system can have multiple replication groups to configure different applications on each group.

To achieve load balancing and utilize both storage systems effectively, most vendors support bi-directional replication. One or more applications can be configured on each storage system, and the other storage system can be used as the destination storage.

![Figure 7.17: Bi-directional remote replication](images/Fig_7.17.png)

*Figure 7.17: Bi-directional remote replication*

There are typically two different modes of replicating data from source to destination storage systems: synchronous and asynchronous.

### Synchronous Replication

![Figure 7.18: Synchronous replication operations](images/Fig_7.18.png)

*Figure 7.18: Synchronous replication operations*

The following is the step-by-step process that takes place in synchronous replication:

1. **Step 1:** First, the host writes data to the source storage.
2. **Step 2:** The source storage writes and then sends data to the destination storage.
3. **Step 3:** The destination storage sends an ACK to the source storage.
4. **Step 4:** The source storage sends an ACK to the host server.

In synchronous replication, the write I/O completion status is not returned to the host until both the source and destination storage systems have written the data. Data is mirrored in real-time. Applications for which data consistency is crucial require synchronous replication. Since data is replicated in real-time, this mode of replication can increase the response time to the host if a higher bandwidth link is not used for replication.

Synchronous mode of replication is commonly referred to as sync replication.

### Asynchronous Replication

![Figure 7.19: Asynchronous replication operations](images/Fig_7.19.jpg)

*Figure 7.19: Asynchronous replication operations*

The following is the step-by-step process that takes place in asynchronous replication:

1. **Step 1:** First, the host writes data to the source storage.
2. **Step 2:** The source storage writes, stores the data in a temporary location, and then sends an ACK to the host server.
3. **Step 3:** The source storage sends data to the destination storage.
4. **Step 4:** The destination storage sends an ACK to the source storage.

Steps 3 and 4 are independent of Steps 1 and 2.

In asynchronous replication, the I/O completion status is returned when the local write completes. Destination writes are deferred until later. Unwritten data is stored temporarily on the source storage system's cache memory or any temporary disk space.

The primary disadvantage of this mode of replication is that unsent data from the source to the destination is at risk if the source system fails, but it improves host write performance, as the ACK is sent immediately after writing to the local storage system.

Some storage vendors implement asynchronous replication through snapshots. A snapshot gets created at a user-defined time interval, and the data on it is copied to the remote storage system.

In asynchronous replication, frequent updates to the same block of data are replicated only once to the destination within the update period, whereas in synchronous replication, every update, even for the same block, gets replicated every time.
