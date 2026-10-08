# Applied Intelligent Decision Making in Machine Learning

Then, the number of unique strings will be approximately $2^n$ (because $n$ bits, we can represent $2^n$ integers). A worked example of the FM algorithm is as follows.
Assume stream $M = \{..., 1, 1, 2, 3, 1, 4, 2, ...\}$ and the hash function $h(x) = (2x + 1) \pmod 5$.

Then,

```
$h(M) = \{3, 3, 0, 2, 3, 4, 0\}$
```

and

```
$ho(h(M)) = \{0, 0, 0, 1, 0, 2\}$
```

BITMAP looks like

```
BITMAP = 0|0|0|1|1|1
```

so that we see the largest index $i=2$. So $R=2$ and the unique integers $2^i/\phi = 5$ approximately (the exact answer is 5).

**Exercise:** Try finding the unique numbers in $M = \{5, 10, 15, 20, ...\}$ with any hash function. Extensions:loglog and Hyper log log algorithms are an improvement over the classic FM algorithm. The interested reader may consult Flajolet et al. (2007).

# 1.4 SAMPLING FROM DATA STREAMS

Due to the unbounded nature of data streams and low memory, we need some efficient ways to reduce the data footprint. In the literature, researchers usually use the following techniques to reduce the data load.

+   - Sampling.
- Sliding window.
- Histogram.
- Wavelets and Fourier transforms.

We have already seen some examples of sliding windows and they find application in places places such as DGIM method (Rajarajan and Ullman, 2011) for counting 1 in a bit and so on. In this section, we are going to discuss a sampling method from data streams.

There are many ways to sample from a data stream. For example we can use random uniform sampling which is the simplest. However, doing random uniform sampling in a data stream is not straightforward since all items in the stream are not available at once. Hence, there is another algorithm called reservoir sampling used to sample items from a data stream such that the probability of selecting an item is $1/n$ where $n$ is the stream size.

The intuition behind reservoir sampling is as follows. Imagine a swimming pool which can have at most $k$ people in it any time. Swimmers are coming continuously and any new swimmer only enters the pool after a previous swimmer has come out. But, how do you decide which swimmer to let in? One solution could be to toss a coin (biased) with probability $p=k/n$ where $n$ is the number of swimmers