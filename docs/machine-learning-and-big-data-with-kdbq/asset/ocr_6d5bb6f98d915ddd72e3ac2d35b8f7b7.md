# 220

# DATA SCIENCE

Let us run it for an example of randomly distributed arrays, one with binary outcome and the other with integer values numbers:

```
x:10072;
y:10074;
quant.stats.somersBinaryIntegerY[y;x]
```

The value is rather small, but without a statistical test, such an assertion is again descriptive.

Finally, we implement Kruskal's y. First, function kruskalGamma takes two arguments: two samples of random variables which were examined:

```
quant.stats.kruskalGamma:[x;y]
// xS, yS arrays of values to compare the rank
// aggregate concordance statistics
stats: sum raze [.quant.stats.concordanceRoutine/:;y..(1+x?y)][t]
--> each t: flip(x;yS)
// return gamma Rank coefficient
{stats[0]-stats[1]%stats[0]+stats[1]};
```

Let us test the function against a pair of random variables:

```
x:100?0;
y:100?10;
quant.stats.kruskalGamma[x;y]
```

```
-0.004848485
```

The value is small and suggests no alignment between two variables. To test such a statement, we also implement ti:

```
quant.stats.tKruskal:[x;y]
// xS, yS arrays of values to compare the rank
// calculate Kruskal's gamma
gamma: .quant.stats.kruskalGamma[x;y]
// count number of combinations
stats: sum raze [.quant.stats.concordanceRoutine/:;y..(1+x?y)][t]
--> each t: flip(x;yS)
// return t_gamma
gamma=sqrt (stats[0]+stats[1])%(count[xS]+count[xS]*1-gamma+gamma);
;
```

The transformed y then reads:

```
.quant.stats.tKruskal[x;y]
```

```
-0.00311252
```