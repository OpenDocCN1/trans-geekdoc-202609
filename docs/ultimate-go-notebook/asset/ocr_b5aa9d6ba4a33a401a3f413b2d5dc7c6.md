even be there."

Performance today is about how efficiently data flows through the hardware. If every piece of data the hardware needs (at any given time) exists only in main memory, my programs will run slower as compared to the data already present in the L1 or L2 caches.

# Listing 3.1

3GHz(3 clock cycles/ns) * 4 instructions per cycle = 12 instructions per ns!
| 1 ns | | 12 instructions | (one) | |
| 1 μs | | 12,000 instructions | (thousand) | |
| 1 ms | 1,000,000 ns | 12,000,000 instructions | (million) | |
| 1 s | 1,000,000,000 ns | 12,000,000,000 instructions | (billion) |

Defined Latencies
| L1 cache reference | | 0.5 ns | | 6 |
| ins | | | |
| L2 cache reference | | 7 ns | | 84 |
| ins | | | |
| Main memory reference | | 100 ns | | 1200 |
| ins | | | |

How do I write code that guarantees the data that is needed to execute an instruction in the L1 or L2 caches? I need to write code that is mechanically sympathetic with the processor's prefetcher. The prefetcher attempts to predict what data is needed before instructions requests the data so it's already present in either the L1 or L2 cache.

There are different granularities of memory access depending on where the access is happening. My code can read/write a byte of memory as the smallest unit of memory access. However, from the caching systems point of view, the granularity is 64 bytes. This 64 byte block of memory is a cache line.

The Prefetcher works best when the instructions are executed create predictable access patterns to memory. One to create a predictable access pattern to memory is to construct a contiguous block of memory and then iterate over that memory performing a linear traversal with a predictable stride.

The array is the most important data structure to the hardware because it supports predictable access patterns. However, the slice is the most important data structure in Go. Slices in Go use an array underneath.

Once I construct an array, every element is equally distant from the next or previous element. As I iterate over an array, I begin to walk cache line by connected cache line in a predictable stride. The Prefetcher will pick up on this predictable data access pattern and begin to efficiently pull the data into the processor, thus reducing data access latency costs.