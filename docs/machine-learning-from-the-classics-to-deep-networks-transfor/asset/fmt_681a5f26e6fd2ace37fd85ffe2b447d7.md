
# Resampling Algorithm

where `card{⋅}` denotes the cardinality of the respective set. [Fig. 17.1](#Chp017_855-884_B9780443292385000238.xhtml#f0010) illustrates the method. The resampling algorithm is summarized next.

![Figure 17.1 The sample u(1) drawn from \mathcal{U}\left( 0,\frac{1}{N} \right)Equation determines the first point that defines the set of N equidistant lines, which are drawn and cut across the cumulative distribution function (CDF). The respective intersections determine the number of times, N(i), the corresponding particle, xi, will be represented in the set. For the case of the figure, x1 will appear once, x2 is missed, and x3 appears two times.](images/B9780443292385000238/gr001.jpg)

[Figure 17.1](#Chp017_855-884_B9780443292385000238.xhtml#cf0190) The sample `u^(1)` drawn from `\mathcal{U}(0, 1/N)` determines the first point that defines the set of `N` equidistant lines, which are drawn and cut across the cumulative distribution function (CDF). The respective intersections determine the number of times, `N^(i)`, the corresponding particle, `x[i]`, will be represented in the set. For the case of the figure, `x[1]` will appear once, `x[2]` is missed, and `x[3]` appears two times.

## Algorithm 17.1: Resampling

### Initialization

1. Input the samples `x[i]` and respective weights `W^(i)`, `i = 1, 2, …, N`.
2. `c[0] = 0`, `N^(i) = 0`, `i = 1, 2, …, N`.

### Main Loop

**For** `i = 1, 2, …, N`, **Do**

1. `c[i] = c[i - 1] + W^(i)`; Construct CDF.

**End For**

### Resampling Steps

1. Draw `u^(1) ~ \mathcal{U}(0, 1/N)`.
2. `i = 1`.
3. **For** `j = 1, 2, …, N`, **Do**
   1. `u^(j) = u^(1) + (j - 1)/N`.
   2. **While** `u^(j) > c[i]`
      * `i = i + 1`
   3. **End While**
   4. `\overline{x}_j = x_i`; Assign sample.

