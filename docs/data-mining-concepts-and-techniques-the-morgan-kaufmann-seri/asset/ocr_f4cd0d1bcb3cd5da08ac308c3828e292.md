of s. <<(abc)(ac)d(cf)) is the suffix of s with respect to the prefix <a>; (<bc>(ac)d(cf)) is its suffix with respect to the prefix <aa>; and (<c)(ac)d(cf)) is its suffix with respect to the prefix <a(ab)>.

Based on the concepts of prefix and suffix, the problem of mining sequential patterns can be decomposed into a set of subproblems as shown below.

+   1. Let {(x1), (x2), ..., (xn)} be the complete set of length-1 sequential patterns in a sequence database, S. The complete set of sequential patterns in S can be partitioned into n disjoint subsets. The ith subset (1 <= i <= n) is the set of sequential patterns with prefix <xi>.

+   2. Let alpha be a length-l sequential pattern and {beta1, beta2, ..., beta_m} be the set of all length-(l + 1) sequential patterns with prefix alpha. The complete set of sequential patterns with prefix alpha, except for alpha itself, can be partitioned into m disjoint subsets. The jth subset (1 <= j <= m) is the set of sequential patterns prefixed with beta_j.

Based on this observation, the problem can be partitioned recursively. That is, each subset of sequential patterns can be further partitioned when necessary. This forms a divide-and-conquer framework. To mine the subsets of sequential patterns, we construct corresponding projected databases and mine each one recursively.

Let's use our running example to examine how to use the prefix-based projection approach for mining sequential patterns.

# **Example 5.16. PrefixSpan: a pattern-growth approach.** Using the same sequence database, S, of Table 5.4 with min_sup = 2, sequential patterns in S can be mined by a prefix-projection method in the following steps.

+   **1. Find length-1 sequential patterns.** Scan S once to find all of the frequent items in sequences. Each of these frequent items is a length-1 sequential pattern. They are <a> : 4, <b> : 4, <c> : 4, <d> : 3, <e> : 3, and <f> : 3, where the notation "<pattern> : count" represents the pattern and its associated support count.

+   **2. Partition the search space.** The complete set of sequential patterns can be partitioned into the following six subsets according to the six prefixes: (1) the ones with prefix <a>, (2) the ones with prefix <b>, ..., and (6) the ones with prefix <f>.

+   **3. Find subsets of sequential patterns.** The subsets of sequential patterns mentioned in step 2 can be mined by constructing corresponding projected databases and mining each recursively. The projected databases, as well as the sequential patterns found in them, are listed in Table 5.5, while the mining process is explained as follows.

+   **a. Find sequential patterns with prefix <a>.** Only the sequences containing <a> should be collected. Moreover, in a sequence containing <a>, only the subsequence prefixed with the first occurrence of <a> should be considered. For example, in sequence <(ef)(ab)(df)cb>, only the subsequence <(_b)(df)cb> should be considered for mining sequential patterns prefixed with <a>. Notice that (_b) means that the last event in the prefix, which is a, together with b, form one event. The sequences in S containing <a> are projected with respect to <a> to form the <a>-projected database, which consists of four suffix sequences: <(abc)(ac)d(cf)>, <(_d)c(bc)(ae)>, <(_b)(df)cb> and <(_f)cbc>. By scanning the <a>-projected database once, its locally frequent items are a : 2, b : 4, _b : 2, c : 4, d : 2, and f : 2. Thus all the length-2 sequential patterns prefixed with <a> are found, and they are <aa> : 2, <ab> : 4, <(ab)> : 2, <ac> : 4, <ad> : 2, and <af> : 2.