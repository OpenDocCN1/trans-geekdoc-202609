
# 正交部分因子设计示例

## `PROC FACTEX` 代码

``` 
/* Efficient way: code four-level vars as two binary vars */
/* All two-way interaction effects as well as quadratic effects are estimable */
proc factex;
factors apr1 apr2 limit1 limit2 color1 color2 rebate1 rebate2 brand chan;
size design=minimum;
model est=(apr1|apr2 limit1|limit2 color1|color2 rebate1|rebate2 brand chan
apr1|apr2|limit1|limit2 apr1|apr2|color1|color2 apr1|apr2|rebate1|rebate2
apr1|apr2|brand apr1|apr2|chan
limit1|limit2|color1|color2 limit1|limit2|rebate1|rebate2 limit1|limit2|brand
limit1|limit2|chan
color1|color2|rebate1|rebate2 color1|color2|brand color1|color2|chan
rebate1|rebate2|brand rebate1|rebate2|chan
brand|chan
);
examine design aliasing;
output out=twoway
      [apr1 apr2]=apr nvals=(0 1 2 3)
      [limit1 limit2]=limit nvals=(0 1 2 3)
      [color1 color2]=color nvals=(0 1 2 3)
      [rebate1 rebate2]=rebate nvals=(0 1 2 3)
      brand nvals=(0 1)
      chan nvals=(0 1);
run;

proc print data=twoway;
run;

/* Completely balanced for EACH variable */
proc freq data=twoway;
table apr limit color rebate brand chan;
run;

/* Also balanced at the multivariate level */
proc freq data=twoway;
table apr*limit*color*rebate*brand*chan/list;
run;
```

Page 180[Table 7.15a](#chapter7.xhtml#tbl7_15a) summarizes part of the aliasing structure from the `PROC FACTEX` output, indicating that some high-order interaction effects are aliased (or confounded) with other interaction effects. The first equation shows what are aliased with the identity column (denoted as 0 as opposed to I in SAS), that is, a defining relation. The truncated design is shown in [Table 7.15b](#chapter7.xhtml#tbl7_15b) for the first 50 runs. The `PROC FREQ`s (frequency distributions) in the above program are used to check and confirm that the attributes are balanced (i.e., all levels of each attribute are equally represented), as expected from an orthogonal design.

### TABLE 7.15a Aliasing Structure of an Orthogonal Fractional Factorial Design Example, Truncated [⏎](#chapter7.xhtml#b7tbl7_15a)

| **Aliasing Structure** |
| --- |
| 0 = apr1\*limit1\*color1\*brand\*chan |
| --- |
| apr1 = limit1\*color1\*brand\*chan |
| apr2 = limit2\*color2\*rebate1\*rebate2\*chan |
| limit1 = apr1\*color1\*brand\*chan |
| limit2 = apr2\*color2\*rebate1\*rebate2\*chan |
| color1 = apr1\*limit1\*brand\*chan |
| color2 = apr2\*limit2\*rebate1\*rebate2\*chan |
| rebate1 = apr2\*limit2\*color2\*rebate2\*chan |
| rebate2 = apr2\*limit2\*color2\*rebate1\*chan |
| brand = apr1\*limit1\*color1\*chan |
| chan = apr1\*limit1\*color1\*brand = apr2\*limit2\*color2\*rebate1\*rebate2 |
| apr1\*apr2 = apr2\*limit1\*color1\*brand\*chan |
| apr1\*limit1 = color1\*brand\*chan |
| apr1\*limit2 = limit1\*limit2\*color1\*brand\*chan |
| apr1\*color1 = limit1\*brand\*chan |
| apr1\*color2 = limit1\*color1\*color2\*brand\*chan |
| apr1\*rebate1 = limit1\*color1\*rebate1\*brand\*chan |
| apr1\*rebate2 = limit1\*color1\*rebate2\*brand\*chan |
| apr1\*brand = limit1\*color1\*chan |
| apr1\*chan = limit1\*color1\*brand |

### TABLE 7.15b An Orthogonal Fractional Factorial Design Example, Truncated [⏎](#chapter7.xhtml#b7tbl7_15b)

| Run || brand || chan || apr || Limit || color || rebate |
| --- | --- | --- | --- | --- | --- | --- |
| 1 || 1 || 0 || 0 || 0 || 0 || 0 |
| --- | --- | --- | --- | --- | --- | --- |
| 2 || 0 || 1 || 0 || 0 || 0 || 2 |
| 3 || 0 || 1 || 0 || 0 || 0 || 1 |
| 4 || 1 || 0 || 0 || 0 || 0 || 3 |
| 5 || 0 || 1 || 0 || 0 || 2 || 0 |
| 6 || 1 || 0 || 0 || 0 || 2 || 2 |
| 7 || 1 || 0 || 0 || 0 || 2 || 1 |
| 8 || 0 || 1 || 0 || 0 || 2 || 3 |
| 9 || 0 || 0 || 0 || 0 || 1 || 0 |
| 10 || 1 || 1 || 0 || 0 || 1 || 2 |
| 11 || 1 || 1 || 0 || 0 || 1 || 1 |
| 12 || 0 || 0 || 0 || 0 || 1 || 3 |
| 13 || 1 || 1 || 0 || 0 || 3 || 0 |
| 14 || 0 || 0 || 0 || 0 || 3 || 2 |
| 15 || 0 || 0 || 0 || 0 || 3 || 1 |
| 16 || 1 || 1 || 0 || 0 || 3 || 3 |
| 17 || 0 || 1 || 0 || 2 || 0 || 0 |
| 18 || 1 || 0 || 0 || 2 || 0 || 2 |
| 19 || 1 || 0 || 0 || 2 || 0 || 1 |
| 20 || 0 || 1 || 0 || 2 || 0 || 3 |
| 21 || 1 || 0 || 0 || 2 || 2 || 0 |
| 22 || 0 || 1 || 0 || 2 || 2 || 2 |
| 23 || 0 || 1 || 0 || 2 || 2 || 1 |
| 24 || 1 || 0 || 0 || 2 || 2 || 3 |
| 25 || 1 || 1 || 0 || 2 || 1 || 0 |
| 26 || 0 || 0 || 0 || 2 || 1 || 2 |
| 27 || 0 || 0 || 0 || 2 || 1 || 1 |
| 28 || 1 || 1 || 0 || 2 || 1 || 3 |
| 29 || 0 || 0 || 0 || 2 || 3 || 0 |
| 30 || 1 || 1 || 0 || 2 || 3 || 2 |
| 31 || 1 || 1 || 0 || 2 || 3 || 1 |
| 32 || 0 || 0 || 0 || 2 || 3 || 3 |
| 33 || 0 || 0 || 0 || 1 || 0 || 0 |
| 34 || 1 || 1 || 0 || 1 || 0 || 2 |
| 35 || 1 || 1 || 0 || 1 || 0 || 1 |
| 36 || 0 || 0 || 0 || 1 || 0 || 3 |
| 37 || 1 || 1 || 0 || 1 || 2 || 0 |
| 38 || 0 || 0 || 0 || 1 || 2 || 2 |
| 39 || 0 || 0 || 0 || 1 || 2 || 1 |
| 40 || 1 || 1 || 0 || 1 || 2 || 3 |
| 41 || 1 || 0 || 0 || 1 || 1 || 0 |
| 42 || 0 || 1 || 0 || 1 || 1 || 2 |
| 43 || 0 || 1 || 0 || 1 || 1 || 1 |
| 44 || 1 || 0 || 0 || 1 || 1 || 3 |
| 45 || 0 || 1 || 0 || 1 || 3 || 0 |
| 46 || 1 || 0 || 0 || 1 || 3 || 2 |
| 47 || 1 || 0 || 0 || 1 || 3 || 1 |
| 48 || 0 || 1 || 0 || 1 || 3 || 3 |
| 49 || 1 || 1 || 0 || 3 || 0 || 0 |
| 50 || 0 || 0 || 0 || 3 || 0 || 2 |

Depending on the experience of applying fractional factorial design, some companies may feel fine with 256 combinations, while others may feel it is still too large. It is exactly the situation where optimal design can come to rescue if there is a need to reduce the combinations.

Optimal design aims at optimizing certain statistical criteria such that the variances of estimated parameters are as small as possible (subject to constraints) or, in other words, the estimated parameters are as “precise” as possible. Since the variance-covariance matrix of estimated parameters in a linear model is

To continue with the credit card design example in [Table 7.7](#chapter7.xhtml#tbl7_7), let's start with [Table 7.15b](#chapter7.xhtml#tbl7_15b) as the candidate set for the D-optimal design.

## `PROC OPTEX` D-optimal 设计

```
proc optex data=twoway;
class color brand chan; /* nominal variables */
model apr|limit|color|rebate|brand|chan@2 apr*apr limit*limit rebate*rebate;
generate n=saturated method=m_fedorov;
output out=optdesign;
run;

proc print data=optdesign;
run;
```

The output of this optimal design in [Table 7.16a](#chapter7.xhtml#tbl7_16a) shows various efficiency measures (the higher the better) – the best D-efficiency design (with a D-efficiency measure of 56.8%) in Design Number 1 is selected as the final design, which only has 37 runs as printed in [Table 7.16b](#chapter7.xhtml#tbl7_16b).

### TABLE 7.16a Statistical Output of an Optimal Design Example (Truncated) [⏎](#chapter7.xhtml#b7tbl7_16a)

| Design Number || D-Efficiency || A-Efficiency || G-Efficiency || Average Prediction Standard Error |
| --- | --- | --- | --- | --- |
| **1** || 56.7902 || 18.9995 || 45.7578 || 1.3367 |
