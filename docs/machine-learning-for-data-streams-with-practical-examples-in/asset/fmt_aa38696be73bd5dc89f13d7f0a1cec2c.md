
up to logarithmic factors, where `t` is the length of the stream and `m = |I|` is the size of the set of items. Furthermore, memory of that order is in fact *necessary* for every `p` other than 0 and 1. Later work has essentially removed the logarithmic gaps as well. In particular, for `F[∞]` or the maximum frequency, linear memory in the length of the stream is required. Observe that for the special cases `p = 0` and `p = 1` we have given algorithms using memory `O(log log t)` rather than `O(log t)` in previous sections.

# 4.7 Exponential Histograms for Sliding Windows

Often, more recent items in the stream should be considered more important for analysis. We will model this idea in several ways in chapter 5, but here we consider the simplest model, the *sliding window*: At all times, we only consider relevant the last `W` items received, where `W` is the window size; all previous items are irrelevant. Alternatively, we fix a time duration `T` (such as one week, one hour, or one minute) and consider only the items that have arrived within time `T` from now. We will consider mostly the first model, but adaptation to the second is easy.

Consider the problem of maintaining the sum of the last `W` values in a stream of real numbers. The natural solution is to use a circular buffer of size `W`; every arriving element is added to the sum; it evicts the oldest element from the buffer, which is subtracted from the sum. The scheme has constant update time, but uses memory `W`. In fact, one can show that any streaming algorithm that *exactly* solves this problem must use memory at least `W`.

We will see next a method for maintaining an *approximate* value of the sum storing only `O(log W)` values. The *Exponential Histogram* sketch by Datar et al. [83] maintains approximations of aggregate functions on sliding windows of real numbers. We describe in detail only the case in which the aggregate function is the sum and the items are bits.

The sketch partitions the length-`W` window into a sequence of subwindows, and represents each subwindow by a *bucket*. Intuitively, buckets encode the desired window of size `W` where older 1s are represented with less and less resolution. Each bucket has a *capacity*, which is a power of 2, and represents a subwindow containing as many 1s as its capacity. It contains an integer value, the *timestamp*, which is the timestamp of the most recent 1 in the subwindow it represents. For a parameter `k > 1`, there are `k` buckets of capacity 1, delimited by the most recent `k` 1s, `k` buckets of capacity 2, `k` buckets of capacity 4, and so on, up to `k` buckets of capacity `2^(m)`, where `m` is the smallest value ensuring that there are enough buckets to hold `W` items, that is,

```
m ≃ log(W/k)
```

Observe that `m ≃ log(W/k)`, and so there are `km ≃ k log(W/k)` buckets.

The pseudocode of the method is given in [figure 4.11](#chapter_4.xhtml#fig4-11) and an example of a sliding window split into buckets is given in [figure 4.10](#chapter_4.xhtml#fig4-10). The example shows the partition of the last 29 bits of a stream into 6 buckets at some time `t`, with `k = 2`. Each bucket contains as many 1s as its capacity. The most recent bit is on the right, with timestamp `t`. The least recent bit is on the left, with timestamp `t − 28`. The timestamp of each bucket is the timestamp of its most recent 1. If the desired sliding window size `W` is 25, the true count of 1s within the most recent `W` bits is 11, as there are 11 1s with timestamps between `t − 24` and `t`. The sketch will report the sum of the window to be 12: the total number of 1s in the buckets (14), minus half the capacity of the oldest bucket (2). Therefore the relative error is `(12 − 11)/11 ≃ 9%`.

![Figure 4.10 Partitioning a stream of 29 bits into buckets, with k = 2. Most recent bits are to the right.](images/Fig4-10.png)

[**Figure 4.10**](#chapter_4.xhtml#rfig4-10)

Partitioning a stream of 29 bits into buckets, with `k = 2`. Most recent bits are to the right.

![Figure 4.11 The EXPONENTIAL HISTOGRAMS sketch.](images/Fig4-11.png)

[**Figure 4.11**](#chapter_4.xhtml#rfig4-11)

The EXPONENTIAL HISTOGRAMS sketch.

The error in the approximation is introduced only by the oldest bucket. It must contain at least one 1 with timestamp greater than `t − W`, otherwise it would have been dropped, but possibly also up to `2^(m) − 1` 1s whose timestamp is at most `t − W` and that should not be counted by an exact method. The relative error is therefore at most half the capacity of the oldest bucket over the capacity of all buckets. Since, after some transient, there are either `k − 1` or `k` buckets of each size except the largest one, the relative error is at most `(2^(m)/2)/(2^(m) + (k − 1)(2^(m−1) + ⋯ + 1)) ≃ 1/2k`.

If the desired approximation rate is `𝜖`, it suffices to set `k = 1/2𝜖`. The number of buckets is then `(log W)/2𝜖`. Each bucket contains a timestamp, which is in principle an unbounded number. However, we can reduce the timestamps to the interval `0…W − 1` by counting mod `W`, so a timestamp has `log W` bits, giving a total of `O((log W)²/𝜖)` bits of memory. Update time is `O(log W)` in the worst case if the cascade of bucket updates affects all buckets, but this happens rarely; amortized time is `O(1)`. A variant of exponential histograms called *deterministic waves* achieves worst-case `O(1)` time [122].

The sketch can be adapted to work for nonnegative numbers in a range `[0, B]` multiplying memory by `log B`, and also to maintain approximations of other aggregates such as variance, maximum, minimum, number of distinct elements, and histograms [83].

# 4.8 Distributed Sketching: Mergeability

Most of the sketches discussed so far have the property called *mergeability*, which makes them appropriate for distributed computation. We say that a sketch type is *mergeable* if two sketches built from data streams `D[1]` and `D[2]` can be combined efficiently into another sketch of the same type that can correctly answer queries about interleavings of `D[1]` and `D[2]`. Note that in problems that only depend on item frequencies, the answer is the same for all interleavings of the streams. For other problems, the definition of mergeability can be more complex.

As a simple example, consider a "sketch" consisting of an integer that counts the number of items in the stream. Now we build two such sketches from two streams. If we add their values, the result is—correctly—the number of items in any stream obtained by merging the original two.

Less trivially, taking the OR is a correct merging operation for Linear Counters. For Cohen's and Flajolet-Martin counters and variants, take the minimum of their stored values, componentwise if we use several copies to reduce the variance. For the CM-sketch, add the two arrays of counters componentwise. In these cases, the two sketches to be merged must use the same hash functions. The cases of SPACESAVING and EXPONENTIAL HISTOGRAMS are left for the exercises.

Mergeability allows for distributed processing as follows: suppose we have `k` different computing nodes, each receiving a different stream—or equivalently some fraction of a large, distributed stream. A central node that wants to build a sketch for this large implicit stream can periodically request the `k` nodes to send their sketches, and merge them into its own global sketch.

For Morris's counter, Cohen (section 7 of [75]) presents a merging method; it is not as trivial as the ones above, particularly the correctness analysis.

# 4.9 Some Technical Discussions and Additional Material

## 4.9.1 Hash Functions
