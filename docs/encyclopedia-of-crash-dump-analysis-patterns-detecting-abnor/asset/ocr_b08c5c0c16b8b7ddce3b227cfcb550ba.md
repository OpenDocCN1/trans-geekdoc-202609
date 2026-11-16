--- Protect Summary (for commit) - RgnCount -------- Total Size --------- %ofBusy %ofTotal
| Type | RgnCount | Total Size | %ofBusy | %ofTotal |
|---|---|---|---|---|
| PAGE_READWRITE | 315 | 6c67000 ( 108.402 Mb) | 43.16% | 5.29% |
| PAGE_EXECUTE_READ | 125 | 1f2c000 ( 31.172 Mb) | 12.41% | 1.52% |
| PAGE_READONLY | 363 | 1ee5000 ( 30.895 Mb) | 12.30% | 1.51% |
| PAGE_WRITECOPY | 34 | 4d000 ( 308.000 kb) | 0.12% | 0.01% |
| PAGE_READWRITE|PAGE_GUARD | 40 | 4b000 ( 300.000 kb) | 0.12% | 0.01% |
| PAGE_EXECUTE_READWRITE | 15 | 11000 ( 68.000 kb) | 0.03% | 0.00% |
| PAGE_EXECUTE | 1 | 1000 ( 4.000 kb) | 0.00% | 0.00% |

--- Largest Region by Usage --------- Base Address -------- Region Size --------
| Region | Base Address | Region Size |
|---|---|---|
| Free | c8c4000 | 593dc000 ( 1.394 Gb) |
| <unclassified> | 6130000 | 33c4000 ( 51.766 Mb) |
| Image | 75141000 | 879000 ( 8.473 Mb) |
| Stack | 3290000 | fd000 (1012.000 kb) |
| ActivationContextData | 50000 | 4000 ( 16.000 kb) |
| NlsTables | 7efb0000 | 23000 ( 140.000 kb) |
| TEB | 7ef6f000 | 1000 ( 4.000 kb) |
| CsrSharedMemory | 7efe0000 | 5000 ( 20.000 kb) |
| PEB | 7fde0000 | 1000 ( 4.000 kb) |

0:000> !address -f:VAR

BaseAddr EndAddr+1 RgnSize Type State Protect Usage
| BaseAddr | EndAddr+1 | RgnSize | Type | State | Protect | Usage |
|---|---|---|---|---|---|---|
| 5e82000 | 5f70000 | ee000 | MEM_PRIVATE | MEM_RESERVE | | <unclassified> |
| 6130000 | 94f4000 | 33c4000 | MEM_PRIVATE | MEM_COMMIT | PAGE_READWRITE | <unclassified> |
| 9500000 | c8c4000 | 33c4000 | MEM_PRIVATE | MEM_COMMIT | PAGE_READWRITE | <unclassified> |
| 74220000 | 74221000 | 1000 | MEM_IMAGE | MEM_COMMIT | PAGE_READONLY | <unclassified> |

The name of this pattern comes from the process of discrete large memory allocations that happen after specific actions or events. Between them, there are no visible or substantial increases in memory usage.