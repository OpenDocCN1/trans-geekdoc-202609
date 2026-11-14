
## RAID 3–Byte Level Striping with Dedicated Parity

Each data block is subdivided (striped) and written on the data disks. Stripe parity is generated on writes, recorded on the parity disk.

### Advantages
- The performance of the array is identical to the performance of one disk in the array except for the transfer rate, which is multiplied by the number of data drives (i.e., less parity drives).
- Excellent performance for large, sequential data requests.
- RAID level 3 requires a minimum of 3 drives to implement.

![Figure 3.18: RAID level 3: Byte level striping](images/Fig_3.18.jpg)
Figure 3.18: RAID level 3: Byte level striping

### Disadvantages
- This technology is fairly complex.
- Performance is slower for random, small I/O operations.
- Speed is limited by the slowest disk.

## RAID 4–Block Level Striping with Dedicated Parity

Each block is written onto a data disk.

### Advantages
- Parity is generated on writes, recorded on the parity disk.
- Very high read data transaction rate.
- RAID level 4 requires a minimum of 3 drives to implement.

![Figure 3.19: RAID level 4: Block level striping](images/Fig_3.19.png)
Figure 3.19: RAID level 4: Block level striping

### Disadvantages
- Single parity drive is involved in every write and becomes the bottleneck as `RAID 3`
- Worst write transaction rate and write aggregate transfer rate

## RAID 5–Block Level Striping with Distributed Parity

Each data block is written on a data disk.

### Advantages
- Parity for blocks in the same rank is generated on writes.
- Recorded in a distributed location.
- RAID level 5 requires a minimum of 3 drives to implement.

![Figure 3.20: RAID level 5: Block level striping with distributed parity](images/Fig_3.20.png)
Figure 3.20: RAID level 5: Block level striping with distributed parity

### Disadvantages
- Disk failure has a medium impact on throughput
- Most complex controller and its firmware design–difficult to rebuild in the event of a disk failure
- Medium write data transaction rate
- Data on virtual volume becomes inaccessible if two disks failed together or second disk fails when volume is in degraded state due to previous disk failure

### Recovering from a Disk Failure

`RAID 5` can tolerate the failure of one of the disks. In the case of failure of a drive, data on the failed drive is calculated by `RAID` controller with parity and data on other surviving drives. During this, the system runs slow, as it has to calculate user data from parity. The following table shows a simple example on how data(`Ax` or `By`) is derived when any disk fails. In reality, parity is a complex function of user data (`Ax` and `By`)

| `Ax` | `By` | `P = Ax⊕By` | `Ax = By⊕P` | `By = Ax⊕P` |
|------|------|-------------|-------------|-------------|
| 0    | 0    | 0           | 0           | 0           |
| 0    | 1    | 1           | 0           | 1           |
| 1    | 0    | 1           | 1           | 0           |
| 1    | 1    | 0           | 1           | 1           |

Table 3.2: Recovering data on failed disk from parity

### Rebuild Process

When a failed drive is replaced with a new one, data of the failed drive get generated from existing data and parity and then written to the new drive.

![A table showing values for D1, D2, and P, with arrows mapping D1 values (0, 0, 1, 1) to New Disk (D2, P) values: (0,0), (1,1), (0,1), (1,0). D1 = D2 XOR P.](images/Fig_3.20a.jpg)

| `D1` | `D2` | `P` |
|------|------|-----|
| 0    | 0    | 0   |
| 0    | 1    | 1   |
| 1    | 0    | 1   |
| 1    | 1    | 0   |

Table 3.3: Rebuilding data on to a new disk (`D1 = D2 XOR P`)

### RAID Level Comparisons

| RAID 2 | RAID 3 | RAID 4 | RAID 5 |
|--------|--------|--------|--------|
| Bit level striping with ECC parity | Byte level striping with dedicated parity | Block level striping with dedicated parity | Block level striping with distributed parity |
| All disks write and read as one. This lowers the tolerance for non-identical drives | Disks write and read independent of on another | | |
| Good performance for large amounts of data or the applications that process large blocks of data | Applications that manipulate small amounts of data, such as transaction processing applications and fewer writes than reads | | |
| Not used | Widely used | Rarely used | Widely used |

Table 3.4: Raid 2 vs. 3 vs. 4 vs. 5

### RAID Levels 4 and 5

Single parity drive in `RAID 4` is involved in every write, thus limits parallelism, whereas `RAID 5` distributes the parity blocks among all the `N+1` drives and enables parallelism.

![Figure 3.21: RAID level 4 vs. RAID level 5](images/Fig_3.21.png)
Figure 3.21: RAID level 4 vs. RAID level 5

### Why RAID 3 Provides Better Large Block Sequential Read/Write Performance than RAID 4 and 5?

- Each block of data is spread across all the drives in the array. All disks serve requests together, but only one host I/O request at a time. Hence sequential request and large block perform better on `RAID 3`. `RAID 3` cannot service multiple requests simultaneously.
- In case of `RAID 4` and `5`, different block of data resides on different drives, hence simultaneously random requests performs better on them.
- For an example, a read request for block `A` consisting of some bytes (`A0`, `A1`) would require all data disks to seek to the beginning first byte and reply with their contents. A simultaneous request for block `B` would have to wait.
- In case of `RAID 4` and `5`, a read request for block `A` would be serviced by first disk. A simultaneous read request for block `C` would have to wait, but a read request for `B` could be serviced concurrently by second disk.

![Figure 3.22: RAID Level 3 vs. RAID Level 4](images/Fig_3.22.jpg)
Figure 3.22: RAID Level 3 vs. RAID Level 4

- If the size of a stripe is reduced below the OS block size a `RAID 5` array then has the same performance pattern as a `RAID 3`.

### Why Does One Disk Become Bottleneck in RAID 4, but Not in RAID 3?

- Referring to the [Figure 3.22](#ch03.xhtml#fig3-22), in addition to the simultaneous writes of block (`A` and `B`) to their respective drives, both need also to be written to the parity drive. In this way `RAID` places a very high load on the parity drive in an array.
- In case of `RAID 3`, all drives synchronously–all serve same requests.

## RAID 6–Block Level Striping with Dual Parity

- Two independent parity computations are used in order to provide protection against double disk failure. Two different algorithms are employed to achieve this purpose.
- Essentially an extension of `RAID` level 5.
- `RAID` level 6 requires a minimum of 4 drives to implement.

![Figure 3.23: RAID level 6: Block level striping with dual parity](images/Fig_3.23.jpg)
Figure 3.23: RAID level 6: Block level striping with dual parity

### Disadvantages
- More complex controller and its firmware design
- Slow write performance because of controller overhead to compute parities
- Requires `N+2` drives to implement because of dual parity scheme

## Hardware versus Software RAID

### Software RAID
- A software solution implements the `RAID`
- Software `RAID`: run on the server’s CPU
- Directly dependent on server CPU performance and load
- Occupies host system memory and CPU operation, degrading server performance

### Hardware RAID
- A piece of hardware or hardware controller.
- Hardware `RAID`: run on the `RAID` controller’s CPU.
- It does not occupy any host system memory, alsoIt is not operating system dependent.
- Host CPU can execute applications while the array adapter’s processor simultaneously executes array functions: True hardware multi-tasking.

## Hybrid RAID Levels–RAID X+Y

Hybrid `RAID` levels are implemented by combining virtual volumes which already formed from physical drives. Following example shows, `RAID X` is formed from physical drives, now again one more time virtual volume is formed using `RAID Y` of those virtual volumes.

![Figure 3.24: Hybrid RAID](images/Fig_3.24.jpg)
Figure 3.24: Hybrid RAID

### Examples
- If `X=5`, `Y=0`, If you copy 30MB Data to `D1`, `D2`, `D4`, `D5`, `D7`, `D8` will get 5MB each and `D3`, `D6`, `D9` will have the parities.
- If `X=1`, `Y=0`, If you copy 30MB Data to, each drive will get 10MB `RAID 0+1`,`RAID 01`,`RAID 0&1` (Mirror of stripes)

![Figure 3.25: RAID 0+1: Mirror of stripes](images/Fig_3.25.png)
Figure 3.25: RAID 0+1: Mirror of stripes
