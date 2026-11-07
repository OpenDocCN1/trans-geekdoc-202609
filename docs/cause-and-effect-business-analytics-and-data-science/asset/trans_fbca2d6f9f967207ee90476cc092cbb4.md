
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

第 180 页[表 7.15a](#chapter7.xhtml#tbl7_15a) 总结了来自 `PROC FACTEX` 输出的混杂结构的一部分，表明某些高阶交互效应与其它交互效应混杂（或混淆）。第一个方程显示了与恒等列（在 SAS 中用 0 表示而不是 I）混杂的内容，即定义关系。截断的设计在 [表 7.15b](#chapter7.xhtml#tbl7_15b) 中显示了前 50 次运行。上述程序中的 `PROC FREQ`s（频数分布）用于检查并确认属性是平衡的（即每个属性的所有水平都被同等代表），这与正交设计预期的一致。

### 表 7.15a 正交部分因子设计示例的混杂结构，截断 [⏎](#chapter7.xhtml#b7tbl7_15a)

| **混杂结构** |
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

### 表 7.15b 正交部分因子设计示例，截断 [⏎](#chapter7.xhtml#b7tbl7_15b)

| 运行 || brand || chan || apr || Limit || color || rebate |
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

根据应用部分因子设计的经验，一些公司可能觉得 256 种组合是可以接受的，而另一些公司可能觉得仍然太大。这正是当需要减少组合时，最优设计可以派上用场的情况。

最优设计旨在优化某些统计准则，使得估计参数的方差尽可能小（受约束条件限制），换句话说，估计参数尽可能“精确”。线性模型中估计参数的方差-协方差矩阵为

为了继续在 [表 7.7](#chapter7.xhtml#tbl7_7) 中信用卡设计示例，让我们以 [表 7.15b](#chapter7.xhtml#tbl7_15b) 作为 D-最优设计的候选集。

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

该最优设计在 [表 7.16a](#chapter7.xhtml#tbl7_16a) 中的输出显示了各种效率度量（越高越好）——设计编号 1 中最好的 D 效率设计（D 效率度量为 56.8%）被选为最终设计，该设计仅有 37 次运行，如 [表 7.16b](#chapter7.xhtml#tbl7_16b) 所打印。

### 表 7.16a 最优设计示例的统计输出，截断 [⏎](#chapter7.xhtml#b7tbl7_16a)

| 设计编号 || D 效率 || A 效率 || G 效率 || 平均预测标准误差 |
| --- | --- | --- | --- | --- |
| **1** || 56.7902 || 18.9995 || 45.7578 || 1.3367 |

