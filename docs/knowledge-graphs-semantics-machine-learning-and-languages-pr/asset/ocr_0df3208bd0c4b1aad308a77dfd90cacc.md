Table 3. Runtime in milliseconds for linking NUTS to CLC using different R-tree building algorithms and capacities combined with the mixed content measure

| Algorithm | 4 | 8 | 16 | 32 | 64 | 128 | 256 |
|---|---|---|---|---|---|---|---|
| R*Tree | 55745 | 49757 | 61810 | 77957 | 137733 | 202192 | 208227 |
| HILBERT | 258193 | 245062 | 233901 | 236357 | 363893 | 270579 | 273802 |
| SMALLESTX | 204226 | 95004 | 58875 | 64362 | 65360 | 62508 | 65948 |
| OMT | 35055 | 35778 | 36415 | 44063 | 71217 | 82937 | 103397 |
| STR | 36986 | 37088 | 38366 | 44042 | 48191 | 61899 | 77262 |
| MATCHHILBERT | 398502 | 345562 | 328975 | 320710 | 327772 | 357677 | 410224 |
| MATCHSMALLESTX | 85300 | 71626 | 62810 | 59780 | 46495 | 53344 | 66957 |
| MATCHOMT | 72359 | 56792 | 55213 | 50404 | 44134 | 48084 | 54525 |
| MATCHSTR | 45716 | 42130 | 41216 | 41769 | 41859 | 42278 | 43248 |

Table 4. Runtime in milliseconds for linking CLC to NUTS using different R-tree building algorithms and capacities combined with the mixed content measure

| Algorithm | 4 | 8 | 16 | 32 | 64 | 128 | 256 |
|---|---|---|---|---|---|---|---|
| R*Tree | 135037 | 139044 | 189439 | 372823 | 1067386 | 3527572 | 1067386 |
| HILBERT | 801618 | 866145 | 621211 | 793548 | 556130 | 540250 | 556130 |
| SMALLESTX | 263744 | 245692 | 422600 | 195218 | 93560 | 134091 | 324985 |
| OMT | 77928 | 62193 | 60354 | 55639 | 48598 | 54950 | 66138 |
| STR | 51448 | 47783 | 46708 | 47289 | 47359 | 48344 | 47359 |
| MATCHHILBERT | 401815 | 357914 | 363288 | 358353 | 344742 | 370740 | 417821 |
| MATCHSMALLESTX | 138362 | 106530 | 73954 | 70796 | 57164 | 68377 | 107256 |
| MATCHOMT | 72590 | 57643 | 56258 | 51175 | 45958 | 50478 | 56514 |
| MATCHSTR | 45245 | 42892 | 42077 | 42613 | 43233 | 43218 | 43849 |

# Research question Q₂.

From Figure 4a, we can see that all the content-based measures implemented in COBALT (i.e., COBALT_area, COBALT_diagonal and COBALT_mixed) with R-tree indexing are 4 to 8 times faster than their counterparts (i.e., COBALT_area(R), COBALT_diagonal(R) and COBALT_mixed(R)) deployed based on the RADON's space tiling indexing. For instance, the total runtime of COBALT_mixed is 195 milliseconds while the total runtime in COBALT_mixed(R) is 849 milliseconds, which means that COBALT_mixed is 4.3 times faster than COBALT_mixed(R). The slowest content-based measure of COBALT (i.e., the COBALT_area) is on average 4840 times faster than RADON. COBALT_mixed is up to 1.47 × 10⁴ times faster than RADON, which is the best speedup COBALT has in comparison to all other algorithms. This shows clearly how efficient are the the content-based measures when it comes to the runtime, which clearly answers our second research question Q₂.

# Research question Q₃.

Based on the results of Table 5, we analysed the impact of using the content-based measures on the F-Measure. For discovering the equals relation based on MBBs of the original polygons, all algorithms achieved an F-Measure of 0.996. For the intersects, contains and within relations, the F-Measures were 0.852, 0.853 and 0.853, respectively. The overlaps relation was the most affected relation by using the MBBs. In the case of the NUTS×NUTS experiment for instance, using MBBs