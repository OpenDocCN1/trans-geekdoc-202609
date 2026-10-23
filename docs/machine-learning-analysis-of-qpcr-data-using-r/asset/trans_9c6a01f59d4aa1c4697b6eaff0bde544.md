

```text
1st Qu.: 83.0   Class :character   Class :character
Median :115.0 Mode :character Mode :character
Mean :106.8
3rd Qu.:145.0
Max. :171.0
> length(unique(amplification$Index))
[1] 120
> unique(amplification$Target)
[1] "SIV"
> unique(amplification$Type)
[1] "Unknown"  "Control"  "NTC"      "Negative"
> range(unique(amplification$Cycle))
[1] 1 50
```

以下是 SIV 数据集的结果概览：

```text
> nrow(validation)
[1] 120
> head(validation, n=3)
```

|  | Run | Well | Fluor | Target | Content | FAM | HEX |
|---|---|---|---|---|---|---|---|
| 1 | 1 | A2 | FAM/HEX | SIV | Unkn | 23.81 | 24.56 |
| 2 | 1 | A11 | FAM/HEX | SIV | Unkn | 20.58 | 24.62 |
| 3 | 1 | B2 | FAM/HEX | SIV | Unkn | 37.79 | 24.64 |

```text
> unique(validation$Target)
[1] "SIV"
> unique(validation$Content)
[1] "Unkn"    "Pos Ctrl" "NTC"     "Neg Ctrl"
> summary(validation[c("FAM", "HEX")])
```

|  | FAM | HEX |
|---|---:|---:|
| Min. | 15.01 | 23.14 |
| 1st Qu. | 23.24 | 26.08 |
| Median | 26.71 | 26.98 |
| Mean | 29.01 | 27.01 |
| 3rd Qu. | 37.00 | 27.72 |
| Max. | 41.85 | 35.62 |
| NA's | 63 | 31 |

```text
> sd(validation$FAM, na.rm = TRUE)

[1] 8.088397

> sum(is.na(validation$FAM))

[1] 63

> sum(is.na(validation$FAM[(validation$Content == "NTC")]))

[1] 6

> sum(is.na(validation$FAM[(validation$Content == "Neg Ctrl")]))

[1] 2
```

这段快速数据探索显示，原始扩增文件包含 5304 个数据点，每个数据点都由一个索引唯一标识。单一靶标“SIV”包含 120 个反应，分为实际生物样本（“Unknown”/“Unkn”）、阳性对照（“Control”/“Pos Ctrl”）、无模板对照（“NTC”）和阴性对照（“Negative”/“Neg Ctrl”）。反应在 50 个循环内完成。FAM 的平均 Cq 为 29.01 ± 8.09 个循环，有 63 个样本的扩增循环未确定（Cq=NA）。在这 63 个无扩增反应中，6 个为 NTC，2 个为阴性对照，因此剩余 55 个实际样本为 PCR 阴性。然而，仅有 FAM 和 HEX 通道存在 264 个缺失数据。以下命令将进一步检查数据框中缺失项的存在情况：

```text
> colSums(is.na(amplification))
```

| Run | Cycle | FAM | HEX | Well | Index | Type | Target |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 264 | 264 | 0 | 0 | 0 | 0 |

```text
> colSums(is.na(validation))
```

| Run | Well | Fluor | Target | Content | FAM | HEX | Index |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 | 0 | 63 | 31 | 0 |

针对 validation 数据框发现的 63 个缺失值与上一步获取的信息一致；仅在 FAM/HEX 字段中出现的 264 个缺失值看起来可疑。以下命令将尝试定位缺失值并理解可能的原因。

```r
> missed = unique(amplification[is.na(amplification$FAM) == TRUE,]$Index)
> length(missed)
[1] 33
> head(amplification[amplification$Index == missed[1],], 5)
```

|  | Run | Cycle | FAM | HEX | Well | Index | Type | Target |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 3613 | 16 | 1 | 2799.034 | 2866.715 | A1 | 138 | NTC | SIV |
| 3614 | 16 | 2 | 2799.025 | 2870.605 | A1 | 138 | NTC | SIV |
| 3615 | 16 | 3 | 2808.016 | 2871.811 | A1 | 138 | NTC | SIV |
| 3616 | 16 | 4 | 2809.798 | 2877.324 | A1 | 138 | NTC | SIV |
| 3617 | 16 | 5 | 2813.030 | 2877.266 | A1 | 138 | NTC | SIV |

```r
> tail(amplification[amplification$Index == missed[1],], 9)
```

|  | Run | Cycle | FAM | HEX | Well | Index | Type | Target |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 3654 | 16 | 42 | 3012.705 | 4038.449 | A1 | 138 | NTC | SIV |
| 3655 | 16 | 43 | NA | NA | A1 | 138 | NTC | SIV |
| 3656 | 16 | 44 | NA | NA | A1 | 138 | NTC | SIV |
| 3657 | 16 | 45 | NA | NA | A1 | 138 | NTC | SIV |
| 3658 | 16 | 46 | NA | NA | A1 | 138 | NTC | SIV |
| 3659 | 16 | 47 | NA | NA | A1 | 138 | NTC | SIV |
| 3660 | 16 | 48 | NA | NA | A1 | 138 | NTC | SIV |
| 3661 | 16 | 49 | NA | NA | A1 | 138 | NTC | SIV |
| 3662 | 16 | 50 | NA | NA | A1 | 138 | NTC | SIV |

问题在于有 33 个反应存在空行。可以通过以下命令移除这些空行：

```r
> cleaned = amplification[is.na(amplification$FAM) == FALSE,]
> nrow(amplification)
[1] 5304
> nrow(cleaned)
[1] 5040
> colSums(is.na(cleaned))
```

| Run | Cycle | FAM | HEX | Well | Index | Type | Target |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

还有一些用于探索数据的更高级函数，这些函数需要专门的库（*Hmisc 和 VIM*）：

```text
> library(Hmisc)
> describe(cleaned)

cleaned

8 Variables    5040 Observations

-------------------------------------------------------------------------------

        Run
n       missing     distinct    Info    Mean    Gmd
5040    0           8           0.968   11.67   5.161
lowest : 1  8  10  12  13, highest: 12 13 14 15 16
Value          1      8     10     12     13     14     15     16
Frequency    714    420    504    588    252    504    630   1428
Proportion  0.142  0.083  0.100  0.117  0.050  0.100  0.125  0.283

-------------------------------------------------------------------------------

        Cycle
n       missing     distinct    Info    Mean    Gmd    .05    .10    .25
5040    0           42          0.999   21.5    13.99  3.0    5.0    11.0
.50     .75         .90         .95
21.5    32.0        38.0        40.0
lowest : 1  2  3  4  5, highest: 38 39 40 41 42

-------------------------------------------------------------------------------

        FAM
n       missing distinct    Info    Mean    Gmd    .05    .10    .25
5040    0       4998        1       2834    382.1  2336   2467   2597
.50     .75     .90         .95
2791    2890    3099        3825
lowest : 2258.000 2260.013 2260.269 2260.344 2260.812
highest: 5766.148 5772.516 5787.097 5806.523 5806.575

-------------------------------------------------------------------------------

        HEX
n       missing distinct    Info    Mean    Gmd    .05    .10    .25
5040    0       4998        1       3127    601.1  2352   2438   2813
.50     .75     .90         .95
2977    3480    3985        4170
lowest : 2252.870 2253.220 2253.872 2254.034 2254.549
highest: 5384.987 5429.361 5487.475 5538.712 5557.927

-------------------------------------------------------------------------------

        Well
n       missing distinct
5040    0       47
lowest : A1 A10 A11 A12 A2 , highest: G2 G3 H11 H2 H3

-------------------------------------------------------------------------------

        Index
n       missing distinct    Info    Mean    Gmd    .05    .10    .25
5040    0       120         1       104.3   52.41  6.95   12.90  81.75
.50     .75     .90         .95
111.50  141.25  159.10      165.05
lowest : 1  2  3  4  5, highest: 167 168 169 170 171

-------------------------------------------------------------------------------

        Type
n       missing distinct
5040    0       4
Value      Control Negative NTC Unknown
Frequency  378     168     1680 2814
Proportion 0.075   0.033   0.333 0.558

-------------------------------------------------------------------------------

        Target
n       missing distinct value
5040    0       1       SIV
Value      SIV
Frequency  5040
Proportion 1
```

```r
library("VIM")

aggr(amplification, prop=FALSE, numbers = TRUE)

aggr(cleaned, prop=FALSE, numbers = TRUE)
```

VIM 的 aggr 函数生成的图（图 3.4）显示，清理后的数据框不再包含空值。现在数据的特征如下：

```text
> length(unique(cleaned$Index))
[1] 120

> unique(cleaned$Target)
[1] "SIV"

> unique(cleaned$Type)
[1] "Unknown" "Control" "NTC"     "Negative"

> nrow(cleaned)
[1] 5040

> range(unique(cleaned$Cycle))
[1] 1 42
```

![](img/7ea01e6937e09d043e45c73fff9eaed3_101_0.png)

**图 3.4.** 使用 VIM 进行图形化数据分析。VIM 包可以绘制数据框中存在的 NA 记录数量，从而简化分析过程。该包还会绘制不同变量之间的交集图，但本图中已省略。A. 数据清理前 SIV 数据集中 NA 项的存在情况。B. 数据清理已移除数据集中的所有 NA 项。

本质上，数据的描述保持不变，但现在有 5040 个数据点，而不是 5304 个，且扩增在 42 个循环内完成。数据探索是一个必不可少且不可忽视的准备步骤。只有数据被清理后，才能继续进行实际分析。

maxRatio 分析的第一步是为每个反应生成 MR/FCN 值，使用前面章节中定义的 mrCalc 函数。由于 SIV 数据具有高背景特征（即最低荧光值的数值已经很高），因此通过设置“background_compensation”参数引入补偿以提高 MR 值。若不进行这种校正，MR 值会非常小，并可能引入偏差。不过，该校正并非必需。数据可视化将使用 lattice 包；图形不会立即绘制，而是先保存到对象 P，再通过调用 print(P) 绘制（图 3.5）。

**代码清单 3.5**

```r
MRs = vector()
FCNs = vector()
for(i in unique(validation$Run)){
    run <- subset(validation, Run == i)
    for(j in run$Well) {
        well <- subset(amplification, Run == i & Well == j)
        x <- mrCalc(well$Cycle, well$FAM, background_compensation = 1000)
        MRs <- append(MRs, x[1])
        FCNs <- append(FCNs, x[2])
    }
}
validation$MR <- MRs
validation$FCN <- FCNs
library(lattice)
P <- xyplot(MR ~ FCN, group = Content, data = validation, cex=1.5, pch=c(0, 0, 1, 4), col = "black",
    key = list(space="top", columns=3, col = "black", points=list(pch=c(0, 1, 4), col="black"),
    text=list(c("Neg Ctrl/NTC", "Pos Ctrl", "Unkn"))))
print(P)
COLS = ifelse(is.na(validation$FAM) == TRUE, 1, 16)
plot(MR ~ FCN, validation, cex=1.5, pch=COLS, xlab="FCN", ylab="MR")
legend("topleft", legend = c("Positives", "Negatives"), pch=c(1,16))
write.table(validation, file = "validationCleaned.tsv", append = FALSE)
```

