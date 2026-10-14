
*   [How to evaluate which MySQL HA solution best suits you](http://www.percona.com/live/mysql-conference-2012/sessions/how-evaluate-which-mysql-high-availability-solution-best-suits-you)

*   [MySQL ZFS Replication](http://dev.mysql.com/doc/refman/5.0/en/ha-zfs-replication.html)

*   [MySQL DRBd Replication](http://dev.mysql.com/doc/refman/5.0/en/ha-drbd.html)

*   [Percona XtraDB Cluster](http://www.percona.com/software/percona-xtradb-cluster)

*   [Percona Replication Manager](https://github.com/jayjanssen/Percona-Pacemaker-Resource-Agents/blob/master/doc/PRM-setup-guide.rst)

*   [Tungsten Replicator](http://code.google.com/p/tungsten-replicator/)

### Understanding issues with NUMA

**TL;DR** - NUMA ([Non-Uniform Memory Access](http://en.wikipedia.org/wiki/Non-Uniform_Memory_Access)) is pretty much a complex topic and only involves a subset of MySQL implementations: Servers running *multiple* Intel Nehalem or newer CPUs, with large amounts of Memory (i.e., over 64GB) and a very large `innodb_buffer_pool_size`. What happens is MySQL swaps out large amounts of memory even though there may be plenty of free memory on the system, causing MySQL performance to drop dramatically.

While the problems around NUMA architecture haven’t been completely solved, you can fix most of the issues by patching `/usr/bin/mysqld_safe`, running Percona Server 5.5, and setting `zone_reclaim_mode` to `0`.

#### What exactly is NUMA?

Before Nehalem CPUs, most multi-CPU systems used a SMP architecture which gave both CPUs equal access to all of the system memory.

![System architecture with SMP](images/06----smp.png)

System architecture with SMP

Starting with Intel’s Nehalem architecture, Nehalem processors and newer processors (Sandy Bridge and Ivy Bridge included), use a new method of accessing memory in multiple CPU systems. **It’s worth noting that this only matters on systems with *multiple physical CPUs*, not single CPU systems with multiple cores.**

Anyways, described simply- with NUMA, instead of having a central access path to memory, each CPU now has direct access to some local memory banks. This ties specific sticks of memory to each CPU and makes accessing non-local memory slower and more complex.

![System architecture under NUMA](images/06----numa.png)

System architecture under NUMA

#### How does NUMA impact MySQL?

Let’s imagine a scenario- You have a huge MySQL system with 2 Physical CPUs and 64GB of memory. Obviously, to take advantage of your 64GB, you set your `innodb_buffer_pool_size` to be 57GB. You run your system under heavy load and notice that even though there is plenty of free system memory, MySQL is performing very poorly because it’s swapping memory to the disk. At first glance, this doesn’t make any sense.

What’s happening is that Linux doesn’t let each CPU address the full 64GB- instead, each CPU can only work with its “local” pool of memory- 32GB in this case. As soon as a single CPU needs to access more memory than is free in its local pool, Linux starts swapping to the disk even if there is free memory in the other CPU’s local pool.

![What happens when a CPU needs to address more than 32GB](images/06----numa_swap.png)

What happens when a CPU needs to address more than 32GB

**How can we overcome this problem?**

There are a couple of ways that we can overcome this serious limitation.

1.  Set `innodb_buffer_pool_size` to 32GB.

2.  Only use MySQL servers with a single physical CPU.

Obviously, these are both horrible solutions. Luckily, there is a better solution. The first step is to use Percona Server 5.5 instead of the stock MySQL Server from Oracle. The version from Percona includes numerous enhancements and patches that make MySQL a bit saner on NUMA systems.

The second part of the solution is to tune Linux to allow memory interleaving across the CPUs, effectively removing the 32GB limit from each CPU and allowing it to work with the full 64GB.

To do this, we need to install `numactl`.

```
1 > apt-get install numactl
```

Next, we have to patch the MySQL startup script `mysqld_safe` to use `numactl`.

```
1 > vi /usr/bin/mysqld_safe
```

Once the file is open, we need to replace this line (line 735 on my system):

```
1 cmd="`mysqld_ld_preload_text`$NOHUP_NICENESS"
```

with a line that uses `numactl`:

```
1 cmd="/usr/bin/numactl --interleave all $NOHUP_NICENESS"
```

#### Further Reading

A great article on NUMA and MySQL is [The MySQL “Swap Insanity” Problem and the Effects of the NUMA Architecture](http://blog.jcole.us/2010/09/28/mysql-swap-insanity-and-the-numa-architecture/) by Jeremy Cole. It’s pretty long, but an interesting read, if you want to really understand the problem and the solution.

### Choosing the best hardware

If you’re going to spend money on hardware, putting it into your MySQL cluster is almost always going to give you the biggest performance increase.

When choosing a CPU, there are a couple of things to keep in mind.

#### CPU Speed (impacts a single query)

MySQL executes each query in a single thread. It does not parallelize your query, so a single query can only take advantage of one CPU core. So, for single query performance in a purely CPU-bound environment, more GHz is always going to win over more cores. Keep in mind though that unless you can fit all of your data into memory, MySQL is rarely CPU-bound.

#### CPU Cores (impacts concurrency)

MySQL can’t split up a single query across multiple cores, but it can run multiple queries concurrently and having more cores gives you more concurrency. In a high-volume environment, more cores are better.

Right now, the best CPU on the market is the Intel Xeon SandyBridge 26xx Series. You can put up to two CPUs per box, each of which can have up to 8-cores each. That gives you 32 concurrently executing threads with Intel’s Hyper Threading. On top of that, they make them as fast as 3.5GHz per core.

#### Memory

This one is easy. Get the most amount of memory that you can possibly cram into your motherboard. As long as you have more data than memory, there is no reason (other than cost) why you should avoid maximizing the memory in your database servers. The more memory you have, the bigger you can set `innodb_buffer_pool_size`.

We run ours with 64GBs per slave, but 128GB, 256GB, or even 512GB in a box isn’t unheard of nowadays. At the time of writing, a 16GB stick of ECC/Registered DDR3 runs around $175, so *even 512GB only costs around $5500*.

If you go with the Intel Xeon 26xx CPUs, SuperMicro even makes a motherboard with enough sockets to fit 768GB. Crazy times we live in.

#### Storage

Making the right storage decisions is very important to the performance of a MySQL cluster. Not all storage is built the same and a master/slave setup means that you have vastly different storage requirements. What works on your master database server won’t necessarily work well for your slave server, and vice-versa.

##### Hard Drives

I highly recommend using high-end server hard drives for your master database. Grab a couple of 10,000 or 15,000 RPM drives and put them into a RAID (discussed below).

Why not go for SSDs on your master? Remember what we talked about when sizing out `innodb_log_file_size`? For writes, MySQL can use mainly sequential I/O by taking advantage of a correctly sized log file. Sequential I/O is fast, even on rotational disks, so for a write-only master database server, it’s not really necessary to pay the price for SSDs.

###### Put your Master Server’s disks into a RAID!

Don’t play with fire. Your drives will fail, usually at the worst time, and will cause downtime.

###### Don’t use RAID-5!

The cost/GB is tempting in a RAID-5 but it’s too slow to use on a high-volume database server. If you’re working on the cheap, use a RAID-1.

###### Do use a RAID-10
