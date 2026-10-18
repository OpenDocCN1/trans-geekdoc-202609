

After BF, Quotient Filter (QF) \[[40](#bib.xhtml#ch00-bib-40)\] is popular among programmers for checking approximate membership queries (AMQ), i.e., it also checks whether an element belongs to a set or not. QF is a cache friendly scheme based on quotienting technique \[[120](#bib.xhtml#ch00-bib-120)\] that even provides scalability outside the main memory. Similar to BF, the membership query result answers ”probably in the set” or ”definitely not in the set” as QF also generates false positive errors. Increasing filter size can significantly reduce error probability of query whereas inserting more elements into the set can increase the false positive rates. However, no false negatives are generated for any query results. A typical use case of AMQ QF is in database tables stored on disk. Any access to the database stored on disk will first check QF for the particular key. If the filter returns positive results, the disk will be accessed otherwise not.

BF only provides beneficial when it is stored in the main memory. When BF size gets too large its performance significantly reduces. Another option is to store BF on disk but this approach requires too many random access to the disk because of the usage of multiple hash functions. Also, this approach will perform multiple input output operations. Moreover, in-memory buffering technique fails in providing scalability if BF size is much larger than in-memory buffer size. QF on the other hand, stores elements data really close to each other so as to avoid multiple random access. With this insight, QF uses a single hash function and provides ways to tackle high collision probability. However, the size consumed by QF is 20% larger than BF.

The QF is quite fascinated by the concept of hash tables where instead of storing actual elements, hashes of the element along with some meta data bits are stored. The additional meta data bits are used to handle collisions. Insertion, lookup, deletion, merging, resizing are the operations supported by QF. To perform QF operations, first pass the element `x` through a single hash function that in return generates `p` bit fingerprint. The fingerprint is further partitioned into two parts: remainder part which has `r` least significant bits and quotient part which has `q` most significant bits. The employed hash tables have a total of 2^(`q`) slots and the remainder part for any element is stored in location indexed by the quotient. Hard collision happens if different valued elements hash similar fingerprint whereas soft collision happens if two different value fingerprints have same quotient but different remainder.

Suppose a element `k` generate fingerprint `kf`, and after partition lets its remainder be `KR` and its quotient be `KQ`. If `KR` is stored exactly at slot `KQ`, the slot is termed as canonical slot. For a soft collision, `KR` is stored at next available slot to the right of location `KQ` in sorted order. Insertion algorithm makes sure that all fingerprints with same quotient bits are stored contagiously and such a set forms a run. It may also be possible that runs first fingerprint may not get stored in its canonical slot as it may get shifted with already stored remainder of some different quotient. A run having its first fingerprint stored in canonical slot refers to the start of the cluster. A cluster may comprise more than one run which ends at an empty slot or start of some other cluster. Along with elements fingerprint, three additional bits are stored in the slot as shown in [Fig. 10.23](#13chap_10.xhtml#fig10_23). These bits are explained as follows:

*   `is_occupied`: If this bit is set, it implies that this slot is the canonical slot for some inserted element in the filter. It may be possible that the key is not stored in its canonical slot but stored somewhere else in the filter.

*   `is_continuation`: If this bit is set, it implies that slot is occupied with some remainder but definitively not the first remainder of the run.

*   `is_shifted`: If this bit is set, it implies that slot is holding a remainder that is not in its canonical slot.

However, with metadata bits, QF consumes 20% more space than BF (but less than counting BF) for the same data size. Also, throughput of lookup operation slows down 3 times. The only way false positive can happen is when there is a hard collision and its probability is given as: $1 - e^{\\frac{- \\alpha}{2^{r}}}$, where `α` is load factor defined as the fraction of total elements and number of slots. When a new element is inserted, its slot is marked occupied and additional bits are updated accordingly. The significance of different combination of additional bits are specified in [Table 10.4](#13chap_10.xhtml#tab10_4). Operations of QF are discussed as follows:

![FIGURE 10.23. Structure of QF.](images/fig10_23.jpg)

**FIGURE 10.23.**  

Structure of QF.

**TABLE 10.4**  

Significance of possible combination of metadata bits.

| 1 || 2 || 3 || Interpretation |

| --- | --- | --- | --- |

| 0 || 0 || 0 || This Slot is empty |

| 0 || 0 || 1 || This is start of run and remainder has been shifted from its canonical slot. |

| 0 || 1 || 0 || This combination is not used. |

| 0 || 1 || 1 || This remainder is not first remainder in a run and also it has been shifted from its canonical slot |

| 1 || 0 || 0 || This is first remainder in run that too in canonical slot. |

| 1 || 0 || 1 || This is holding first remainder in run that has been shifted from its canonical slot. In addition, the run meant for this slot exists that has been shifted right. |

| 1 || 1 || 0 || This combination is not used |

| 1 || 1 || 1 || This remainder is not first remainder in a run that has been shifted from its canonical slot. In addition, the run meant for this slot exists that has been shifted right. |

1: `is_occupied`, 2: `is_continuation`, 3: `is_shifted`

**Lookup**: To query any element `k` follow the following steps.

*   Hash the key to generate its fingerprint `kH`.

*   Next, partition `kH` into quotient `kQ` and remainder `kR`. Clearly, canonical slot for element `k` is `kQ`. If canonical slot has all metadata bits as false, it implies slot is not occupied. Hence, the element is definitively not present in the set.

*   If `kQ` is occupied, then locate the run for `k`. As it is previously mentioned, remainder with same quotient are stored contagiously and it forms a run. The first in a run might not be present in canonical slot, if entire run has been shifted right by some another run in left. So, to locate quotient run, first locate start of the cluster and then find number of run to skip in a cluster to reach run for `kR`. For this:

    *   Scan left for locating start of the cluster. If `is_shifted` for slots to the left of `kQ` is false, it implies start of the cluster.

    *   Scan right to keep track of running count that counts number of runs to skip in order to reach quotient run. The slots to the left of `kQ` with `is_occupied` set implies another run to be skipped. For each value of `is_occupied` as 1, increment the running count and decrement one if `is_continuation` is clear (implies start of another run) until running count reaches zero. When the value of running count becomes zero it implies that quotient run has been reached.

*   Next, remainder corresponding to the run with `kR` is compared. If matches, the element `k` is probably present in the set otherwise definitely not in the filter.

**Insertion:**

*   Pass the element `k` to be inserted through the hash function to compute its fingerprint. First, ensure that the key is not already inserted in filter by using lookup procedure described above. If not inserted already, then follow the next step.

