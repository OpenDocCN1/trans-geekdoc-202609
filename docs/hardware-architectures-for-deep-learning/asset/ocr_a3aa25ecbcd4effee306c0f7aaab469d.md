# CNN agnostic accelerator design 173

It is often not possible to fully use the DRAM device bandwidth without wide data requests and sequential accesses for burst transfer [6]. As a result, the number of independent parallel on-chip buffer ports affects off-chip bandwidth usage. For example, IFM buffer banks have $Tn$ independent ports to supply parallel pixels every cycle. Accordingly, IFM tiles are loaded with $Tn$ elements every cycle, even though off-chip memory might be able to provide more.

Figure 8.6 shows achieved bandwidth with DDR3 DRAMs operating at 800 MHz for different on-chip buffers with small burst lengths of 128. Maximum capable performance of the memory used is 25 GB/s and the memory controller provides a 1024 bit wide interface. As we can see, to cache data in a 64 bit wide on-chip buffer, the requests have to be 64 bits per cycle which achieved only 1.32 GB/s, a fraction of the available off-chip memory performance. By increasing the on-chip bandwidth, per cycle requests can be widened correspondingly and better off-chip bandwidth usage. It is just enough to make widths equal to interface width of 1,024, as even more wider requests can also improve the burst average. Further improvement requires longer access of sequential data. For feature maps, the burst length is represented by depth of the buffer. For example, OFM buffers maximum possible burst is $Tr \times max$. The burst access effects of on-chip memory are incorporated in the runtime model presented in the next section by assuming that all accesses within maximum off-chip bandwidth do not encounter any stalls.

# 8.6.2.2 Effective bandwidth latency

We need to consider both the maximum bandwidth $off\_chip\_bw$ and the request bandwidth $on\_chip\_bw$, to study memory latency. Hence, (8.10) yields the effective bandwidth $mem\_bw$, visible to the accelerator as

```
mem_bw = min(off_chip_bw, on_chip_bw) (8.10)
on_chip_bw = vector_size × DW × freq (8.11)
```

where vector_size is the number of data elements accessed every cycle as shown in (8.6). For stall-free operation, we want the $on\_chip\_bw$ to be as close to $off\_chip\_bw$ as possible.

![](bbox=[0.118, 0.733, 0.705, 0.893])

Figure 8.6 Impact of data request width on achieved off_chip_bw. DRAM interface is 1,024 bits wide and burst accesses are 128 long