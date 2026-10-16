
The polyline distance metric (PDM) is used for computing the stenosis and LD error bias. Let the LI far and LI near borders be denoted as `C[1]` and `C[2]`, respectively. Let the reference point on `C[1]` be vertex `R[1]` and the segment in `C[2]` be defined by vertices `R[2]` and `R[3]`. Let the distance between `R[1]` and `R[2]` be `d[1]` and the distance between `R[1]` and `R[3]` be denoted as `d[2]`. Let `D(R[1], L)` be the PD between vertex `R[1] : (x[1], y[1])` on `C[1]` and line segment `L` formed by two points `R[2] : (x[2], y[2])` and `R[3] : (x[3], y[3])`. Let `δ` be the distance of the reference point `R[1]` towards the line segment `L`. The perpendicular distance between the line segment `L` and the reference point, `R[1]`, is specified by `d[p]`. Then, the polyline distance `D(R[1], L)` can be defined as

```
$$D(R\_{1},L) = \\left\\{ \\begin{array}{l} \\begin{array}{lc} {\\mid d\_{p}\\mid} & {0 < \\delta < 1} \\\\ \\end{array} \\\\ \\begin{array}{lc} {\\min(d\_{1},d\_{2})} & {\\delta < 0,\\delta > 1} \\\\ \\end{array} \\\\ \\end{array} \\right.,$$
```

(8.5)

where

```
$$d\_{1} = \\sqrt{\\left( {x\_{1} - x\_{2}} \\right)^{2} + \\left( {y\_{1} - y\_{2}} \\right)^{2}}$$
```

(8.6)

```
$$d\_{2} = \\sqrt{\\left( {x\_{1} - x\_{3}} \\right)^{2} + \\left( {y\_{1} - y\_{3}} \\right)^{2}}$$
```

(8.7)

```
$$\\delta = \\frac{\\left( {y\_{3} - y\_{2}} \\right)\\left( {y\_{1} - y\_{2}} \\right) + (x\_{3} - x\_{2})(x\_{1} - x\_{2})}{\\left( {x\_{3} - x\_{2}} \\right)^{2} + \\left( {y\_{3} - y\_{2}} \\right)^{2}}$$
```

(8.8)

and

```
$$d\_{p} = \\frac{\\left( {y\_{3} - y\_{2}} \\right)\\left( {x\_{2} - x\_{1}} \\right) + (x\_{3} - x\_{2})(y\_{1} - y\_{2})}{\\sqrt{\\left( {x\_{3} - x\_{2}} \\right)^{2} + \\left( {y\_{3} - y\_{2}} \\right)^{2}}}.$$
```

(8.9)

The process to obtain `D(R[1], L)` is repeated for the remaining points of the outline `C[j]` and is specified by

```
$$D\\left( {C\_{1},C\_{2}} \\right) = \\sum\\limits\_{i = 1}^{N}{D(R\_{i},S\_{C\_{2}}),}$$
```

(8.10)

where `N` represents all points on `C[1]` and `S[C[2]]` is the section on outline of `C[2]`. This algorithm is recurring in reverse, where `C[2]` becomes the reference outline and `C[1]` becomes the segment outline. The reverse is symbolized as `D(C[2], C[1])`. Finally, by combining both `D(C[1],C[2])` and `D(C[2], C[1])`, we obtain the PDM which is specified by

```
$$\\quad D\_{PDM}\\left( {C\_{1}:C\_{2}} \\right) = \\frac{D\\left( {C\_{1},C\_{2}} \\right) + D(C\_{2},C\_{1})}{(\\#{points} \\in C\_{1} + \\#{points} \\in C\_{2})}.$$
```

(8.11)

## Results for LD

For the first DL1, the corresponding PoMs for stenosis and the LD error bias are specified in tables 8.2 and 8.3, respectively. Similarly, the stenosis and LD error bias tables for DL2 and DL3 are shown in tables 8.4 and 8.5 and tables 8.6 and 8.7, respectively. The corresponding plots for DL1, DL2, and DL3 are shown in figures 8.6, 8.7, and 8.8, respectively. Each of the DL systems was trained for 4000 iterations.

**Table 8.2.** Mean PoM stenosis (%) of DL1 w.r.t. GT1. (Reproduced with permission from [66].)

| # Images | Mean DL1 stenosis (%) | Mean GT1 stenosis (%) | Mean PoM1 (stenosis) (%) |
| --- | --- | --- | --- |
| 10 | 57.2 | 57.2 | 93.7 |
| 50 | 42.1 | 40.8 | 94.6 |
| 100 | 35.2 | 33.1 | 95.6 |
| 150 | 31.2 | 28.9 | 96.1 |
| 200 | 28.4 | 26.0 | 96.3 |
| 250 | 26.1 | 23.8 | 96.2 |
| 300 | 24.2 | 21.9 | 96.4 |
| 350 | 22.5 | 20.3 | 96.5 |
| 407 | 20.5 | 18.6 | 96.7 |

**Table 8.3.** LD 绝对平均误差偏差（毫米）和 PoM（%）计算在 DL1 与 GT1 之间（经许可复制自 [66]。）

| 范围（毫米） | 与 GT1 的图像数量 | 与 DL1 的图像数量 | 使用 GT1 计算的平均 LD（毫米） | 使用 DL1 计算的平均 LD（毫米） | LD 绝对平均误差偏差（毫米） | 与 LD 误差偏差的卡方检验 | PoM1（LD）（%） |
| --- | --- | --- | --- | --- | --- | --- | --- |
| <8.5 | 406 | 406 | 6.07 ±0.91 | 6.09 ±0.94 | 0.19 ±0.27 | `p` < 0.001 | 96.71 |
