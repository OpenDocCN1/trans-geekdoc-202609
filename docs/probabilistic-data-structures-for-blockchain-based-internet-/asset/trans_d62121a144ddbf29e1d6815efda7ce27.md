

Oftentimes while processing streaming IoT data, searching for a particular item is required with minimum latency and space. The aim of membership query probabilistic data structures (MSQ PDS) is to check the presence of an element `x` in a large set (`S`) of elements. The membership query operation using a linked list, array or a balanced binary tree requires a memory space linear to the size of set `S`. Hash table also has a larger size so, the memory it takes will also be larger. On the other hand, MSQ PDS are getting popular for handling queries of big data and streaming applications as these data structures consume less memory. Also, MSQ PDS provides constant query time. In order to provide optimized space efficiency, as opposed to storing the entire set of data, MSQ PDS stores summarized form of data using hashing. [Table 10.1](#13chap_10.xhtml#tab10_1) represents a comparison in space and time complexity for membership query operation in different data structures. Insertion and deletion (for some specific MSQ PDS) are the operations that are supported by MSQ PDS.

**TABLE 10.1**  

Space and time complexity for searching in different data structures

|  || Linear DS || Non-linear DS || Hashing DS || Probabilistic DS |

| --- | --- | --- | --- | --- |

| Example: || Array, Linked list || Graph, BST || Hash Tables || BF, QF, Skiplist |

| Space Complexity || `O(n)` || `O(n)` || `O(n)` || `O(m)` |

| Search Time || `O(n)` || `O(log n)` || `O(1)` || `O(k)` |

`n`: data size, `m`: PDS size (`m` ¡ ¡ `n`), `k`: number of hash function, DS: Data structures, BST: Binary search trees

Nevertheless, a predictable error is expected while using MSQ PDS. However, here errors are managed under a predefined marginal threshold with a trade-off between accuracy and storage requirements. Bloom Filter, quotient filter, and skiplist are popularly used PDS under this category which will be discussed further in this chapter. Moreover, the popularity of Bloom filter resulted in its various variants with some extra capability which is not supported by standard Bloom filter. However, being a part of error prone approach, bloom filter, and quotient filter return results with false positive on membership query whereas skip list doesn't return any error.

False positive implies that even if an element is not present in the set, query result may output true whereas false negative implies that for the presence of an element query results in negative results. The difference between false positive and false negative has been represented in [Fig. 10.1](#13chap_10.xhtml#fig10_1). Additionally, the precision and recall value for the model can be computed from Eqs. 10.1 and 10.2 respectively where precision describes how accurate the calculated results are out of total positive predictions and recall depicts the proportion of correctly identified actual positive. The next topic discusses the concept of Bloom filter.

![FIGURE 10.1. False positive vs. false negative.](images/fig10_1.jpg)

**FIGURE 10.1.**  

False positive vs. false negative.

```
\begin{array}{l} {Precision = \frac{True\, positive}{True\, positive + False\, positive}} \\ \end{array}
```

(10.1)

```
\begin{array}{l} {Recall = \frac{True\, positive}{True\, positive + False\, negative}} \\ \end{array}
```

(10.2)

## [10.2 Bloom Filter and its Variants](#contents.xhtml#rsec10_2)

The concept of BF was introduced by Burton H. Bloom back in 1970 \[[46](#bib.xhtml#ch00-bib-46)\]. BF resides inside the main memory and with BF its fast to check MSQ. Insertion and lookup are the two operations supported by standard BF. However, lookup operation of standard BF occasionally results in false positive but never in false negative. Apparently, BF should be used in cases where a bit of false positive can be accepted.

### [10.2.1 Structure of Bloom filter](#contents.xhtml#rsec10_2_1)

BF is an array of `m` bits having index from 0 to m-1 as represented in [Fig. 10.2](#13chap_10.xhtml#fig10_2). A single bit is used to represent each entry in the filter, i.e., 0 or 1. Along with this, BF employs `k` different independent and uniform hash functions. Instead of storing the data itself, BF utilizes hashing to store hashes of the data in a compact form. However, employed hash functions should have fast speed. The number of hash functions can be from 1 to `m`. The bits of BF are all initialized to zero. It first performs multiple times (`k`) hashing on each data item and then stores its hash value in the array of size `m`. Clearly, with an increase in the number of hash functions, the speed of BF gets slow. Notably, searching time complexity with BF is independent of the size of array and stored number of elements. For a fixed error rate, both insertion and lookup operations serve constant time complexity that is proportional to the number of hash functions used. Hence, by encoding information in a bit vector, BF can compactly represent a data and can be transmitted with a low bandwidth requirement. Despite proving quite beneficial, there are some disadvantages of BF which are listed as follows:

*   Nevertheless, deletion is not supported by BF as resetting bits to 0 can introduce false negatives (the reseted bit might represent other element entry in the BF). However, the entire BF can be deleted once in a while with reset function. Although, there are various instances of BF which support deletion by keeping a record of variable count in memory, for example, Counting BF \[[79](#bib.xhtml#ch00-bib-79)\], Deletable BF \[[165](#bib.xhtml#ch00-bib-165)\] etc.

*   Poor scaling out of main memory as in secondary memory use of multiple hash functions requires many random access to the disk.

*   BF can not be resized dynamically.

*   Inability to compute frequency count of each element. It can only check presence of any element.

![FIGURE 10.2. Representation of Bloom filter.](images/fig10_2.jpg)

**FIGURE 10.2.**  

Representation of Bloom filter.

Insertion and membership query operations of BF are described as follows:

*   To insert an element `x`, first apply `k` hash functions to the element `x` and the position corresponding to `h_i(x)`(`i` = 1, 2, ..., `k`) is set to 1 if already not set.

*   To check membership of an element `x`, pass the element `x` through `k` hash functions to get `k` array positions. If any of the bit corresponding to these positions is zero, then the element is definitely not in the set otherwise, it might be present. Also, it is probable that even if all `k` corresponding positions are 1, element might not be present into the set (false positive). While designing BF, one of the aims of developers is to design filter with very less false positive rate. However, false negative never happens for BF.

For example, consider a case where BF is 10 bit long with three hash functions ( `h[1]`, `h[2]`, `h[3]`) where `h[1]` = `x mod 6`, `h[2]` = (`x mod 4`) `mod 6` and `h3` = (2 * `x`) `mod 6`. To insert an element 11, pass the key (`11`) through all hash functions which results in 3 indices, i.e, `h[1]` = 5, `h[2]` = 3, `h[3]` = 4 and set these three resulting positions to 1. Similarly to insert element 3, positions 0, 3 will be set to 1 as represented in [Fig. 10.3](#13chap_10.xhtml#fig10_3). However, membership query for key `5` returns definitely not in the set as positions corresponding to hash function `h[2]` is zero (See [Fig. 10.4](#13chap_10.xhtml#fig10_4)). The lookup operation for element 12 will result in false positive as 12 is not present in the set but position corresponding to all three hash functions, (i.e., 0, 0, 0) are set to 1 whereas for element 5, the scenario represents true positive. Simultaneously, [Fig. 10.5](#13chap_10.xhtml#fig10_5) represents deletion and it could be observed that deletion of element 3 from the introduces false negative for element 11.

**Union and intersection of standard BF**

