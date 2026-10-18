
Let's take an example to understand count-sketch more clearly. Consider a table with `w = 6` and `d = 4`. The value of the hash function for each hash table is `h[1] = i mod 6`, `h2 = (2 * i) mod 6`, `h[3] = (i mod 3) mod 6` and `h[4] = (2 * i + 3) mod 6` and `g1, g2` generate either `-1` or `+1` randomly for any incoming item. The result of elements after passing through hash function `h` and `g` is represented in [Table 12.3](#15chap_12.xhtml#tab12_3). The operation `update(12,1)`, `update(5,2)`, `update(16,1)` and `update(6,1)` in series has been represented in [Figs. 12.7](#15chap_12.xhtml#fig12_7). Similarly, the operations `estimate(5)` and `estimate(12)` have been represented in [Fig. 12.8](#15chap_12.xhtml#fig12_8) and [12.9](#15chap_12.xhtml#fig12_9) respectively. It is clear from [Fig. 12.9](#15chap_12.xhtml#fig12_9) that the query for element 12 results in over-estimation. Notably, the estimation query for count-sketch may result in under-estimation as well.

![](images/tab12_3.jpg)![FIGURE 12.7. Update operation in Count-sketch.](images/fig12_7.jpg)

**FIGURE 12.7.**  

Update operation in Count-sketch.

![FIGURE 12.8. Estimate operation in count-sketch.](images/fig12_8.jpg)

**FIGURE 12.8.**  

Estimate operation in count-sketch.

![FIGURE 12.9. Estimate operation in count-sketch representing over-estimate.](images/fig12_9.jpg)

**FIGURE 12.9.**  

Estimate operation in count-sketch representing over-estimate.

## [12.4 Count-Min with Conservative Update Sketch](#contents.xhtml#rsec12_4)

The main logic behind the conservative update is “Minimal Increase” which only increment count with the minimum amount required to ensure that accuracy of the estimate remains. Counservative update (CU) can be applied to Count-Min-sketch and also to spectral BF. CM-CU sketch was introduced by authors of \[[76](#bib.xhtml#ch00-bib-76)\] with an aim to reduce the false positive error in the result. Specifically, the authors of \[[88](#bib.xhtml#ch00-bib-88)\] concluded that CMS with conservative update minimizes the over-estimation error by a factor of 1.5. Similar to CMS, CM-CU also uses a 2-D table of size `w * d` where, `w` is the width and `d` is the depth of the table. Also, `k` hash functions equal to the depth of the table are used. For any incoming item, only the count by minimal amount will be incremented. However, the CM-CU sketch does not support deletion. The operations that are supported by CM-CU sketch are discussed as follows:

*   Update (`q, c`): This operation adds an element `q` with count `c` to the sketch. To perform this operation, first, compute the approximate frequency of the element `q` from the existing state of the sketch by using the `Estimate(q)` procedure explained for CMS, (i.e., by taking a minimum of the values returned from values indexed by `d` hash functions. Let's call this value `f[q]`. Next, compare the values at `k` locations corresponding to `k` hash functions. Here, in CMS, the values at `k` locations are only incremented if the existing value in the sketch is less than `f[q] + 1`, otherwise, the value won't get changed. This type of conditional updation ensures that unnecessary updation and reduces over-estimation error. In order to update `q` with the count, `c` first compute `f[q]` using:

    $$\\begin{array}{l} {f\_{q} = min\_{k}\\, > sketch\\lbrack k,h\_{k}(q)\\rbrack\\, > \\forall\\, > 1 \\leq k \\leq d} \\\\ \\end{array}$$  

    (12.4)

    and update the count according o following equation:

    $$\\begin{array}{l} \\left. sketch\\lbrack k,h\_{k}(q)\\rbrack\\leftarrow max\\left\\{ sketch\\lbrack k,h\_{k}(q)\\rbrack,f\_{q} + c \\right\\} \\right. \\\\ \\end{array}$$  

    (12.5)

*   `Estimate(q)`: It follows the same procedure `Estimate(q)` as explained for CMS in [section 12.2](#15chap_12.xhtml#sec12_2).

The example for update operation has been represented in [Fig. 12.10](#15chap_12.xhtml#fig12_10). Here, the operations `update(12,1)`, `update(5,2)`, `update(16,1)`, `update(6,1)` in shown in series. The hash outputs for all these element has been shown in [Table 12.2](#15chap_12.xhtml#tab12_2). Similarly the operation Estimate(6) has been shown in [Fig. 12.11](#15chap_12.xhtml#fig12_11). Experiments concluded that error rate is proportional to $\\frac{1}{M}$ where `M` is the available memory.

![FIGURE 12.10. Update operation in CM-CU sketch.](images/fig12_10.jpg)

**FIGURE 12.10.**  

Update operation in CM-CU sketch.

![FIGURE 12.11. Estimate operation in CM-CU sketch.](images/fig12_11.jpg)

**FIGURE 12.11.**  

Estimate operation in CM-CU sketch.

## Activity

### Multiple Choice Questions

1.  What is the main idea behind count-min with conservative update?

    1.  Minimal increase

    2.  Minimal decrease

    3.  Maximal increase

    4.  Maximal decrease

2.  If a sketch employs a table of size `t * b` where `t` is number of rows and `b` is the number of columns, then how many hash functions are required in order to implement CMS?

    1.  `O(t+b)`

    2.  `O(b)`

    3.  `O(t)`

    4.  `O(t*b)`

3.  Which measure of central tendency is used in order to execute query by count-sketch ?

    1.  Mode

    2.  Median

    3.  Average

    4.  Range

4.  What is the impact on error rate with increase in width of 2-D array of CMS ?

    1.  Error rate will become high

    2.  Error rate will get reduced

    3.  Error could be high or low

    4.  No relation between error rate and width of table

5.  Which of the following mentioned BF does not support deletion?

    1.  Counting BF

    2.  DBF

    3.  Stable BF

    4.  Compressed BF

6.  Which among the following is the deterministic algorithm for frequency estimation?

    1.  CMS

    2.  HLL

    3.  Majority algorithm

    4.  All of the above

7.  What is the time complexity for updation operation in CMS?

    1.  `O(d)`

    2.  `O(w)`

    3.  `O(log d)`

    4.  `is_shifted`

8.  What is the space requirement for CMS?

    1.  Linear

    2.  Sub-linear

    3.  Super-linear

    4.  logarithmic

1. a  2. b  3. b  4. b  5. c  6. c  7. a  8. b

# [13](#contents.xhtml#rchapter13)

# [Approximate Similarity Search Query Probabilistic Data Structures](#contents.xhtml#rchapter13)

## [13.1 Introduction](#contents.xhtml#rsec13_1)

Large datasets generated from a system may contain duplicates or near duplicates. Applying brute force technique to probe all possible combination can give exact nearest neighbor match, but this way is no scalable. Over and above, the traditional cluster analysis techniques (e.g., k-nearest neighbor) take quadratic or cubic time which seems unpractical for large datasets. Moreover, tree structure methods, such as- kd-trees, BDD trees etc. demands enough space and time as these methods compare given query with each record while searching to identify similar records \[[83](#bib.xhtml#ch00-bib-83)\], \[[106](#bib.xhtml#ch00-bib-106)\]. Hence, there is a demand for efficient similarity search method that can solve desired queries in low cost. To address this problem, researchers proposed using approximation techniques for high dimensional similarity search.
