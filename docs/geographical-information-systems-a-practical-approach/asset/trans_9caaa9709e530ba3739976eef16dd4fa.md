

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_442_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_442_1.png)

图 8.22 流长图：(a) 上游和 (b) 下游。

## 8.4.2 次要地形属性

次要属性用于描述景观中特定环境过程的空间变异性（Wilson and Gallant 2000）。它们可用于量化地形对水、土壤、动植物的空间分布和丰富度的影响。次要属性的示例包括地形湿度指数（TWI）、流力指数（SPI）、输沙指数（STI）和辐射指数。辐射指数在第 8.6 节中讨论。

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_443_0.png)

图 8.23 从 DEM 划定的五个单独集水区。

## 实践 8.4 参见支持材料

在本实践中，您将学习如何在 ArcGIS Pro 或 QGIS 中从 DEM 划定集水区并提取其他水文相关地形属性。

### 8.4.2.1 地形湿度指数

TWI 量化了地形对土壤中水分积聚区域位置和大小的影响（Beven and Kirkby 1979）。它定义为：

```
$TWI = \ln\left(\frac{A_s}{\tan \theta}\right)$ (8.17)
```

其中 $A_s$ 是单位等高线长度的上游集水区面积，$\theta$ 是局部坡度角。$A_s$ 被称为特定集水区。当使用 DEM 时，$A_s$ 可以估计为上游集水区面积与 DEM 像元大小（$d$）的比值，除非 DEM 分辨率非常高（Chirico et al. 2005）。通常采用以下程序从无洼 DEM 中估计 TWI：

- 1 从 DEM 中推导流向。
- 2 从流向中推导流累积 \(f_{acc}\)。
- 3 计算上游集水区面积 \(A\) 为：\(A = (f_{acc} + 1) \times d^2\) (8.18)
- 4 计算特定集水区为：\(A_s = \frac{A}{d} = (f_{acc} + 1) \times d\) (8.19)
- 5 从 DEM 中计算坡度 \((\theta)\)。
- 6 使用公式 8.17 计算 TWI。

因为山脊的流累积值为 0，所以在公式 8.18 和 8.19 中必须对所有流累积值加 1；否则，集水区面积将比一个网格单元大小小。图 8.24 是由实践 8.1 中创建的无洼 DEM 推导出的 TWI 图。TWI 可以提供关于相对湿润区域和相对干燥区域的空间分布及比例的洞察。它作为一种基于物理的指数，用于量化地形对径流产生的影响并估计地表饱和区域的位置（Beven and Kirkby 1979）。可以使用阈值 TWI 值来识别产生饱和地表径流的区域。在一个集水区中，当其他环境条件（如土地覆盖和土壤）相同时，具有相似 TWI 值的区域被认为对降雨具有相似的水文响应（Qin et al. 2011）。还发现它与地下水深度和土壤 pH 值相关良好（Sørensen et al. 2005）。TWI 已被用作潜在土壤湿度模式的指标，一

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_444_0.png)

图 8.24 地形湿度指数。

input for digital soil mapping, a parameter in modelling the spatial variability of crop yields and a criterion for delineating nitrogen management zones (Qin et al. 2011). In addition, it has been used to predict the spatial distribution of vascular plant species richness in the Swedish boreal forest (Zinko 2004). However, TWI assumes that the soil hydraulic conductivity decreases exponentially with depth so that subsurface flow is confined to a shallow layer. If this is not the case, it may not be a good predictor of the spatial distribution of soil water (Wilson and Gallant 2000).

provide good predictors of the location of ephemeral gullies (Moore et al. 1988). For example, ephemeral gullies formed where TWI > 6.8 and SPI > 18 for a small semi-arid catchment in Australia (Moore et al. 1988), and they formed where TWI > 8.3 and SPI > 18 on a small catchment in Antigua in the Caribbean (Srivastava and Moore 1989). The threshold values of these indices vary from place to place due to differences in soil properties (Moore et al. 1988). Moore and Nieber (1989) also used SPI to identify areas where soil conservation measures should be taken to reduce the erosive effects of concentrated flow. Figure 8.25 shows an SPI map derived from the depressionless DEM created in Practical 8.1.

### 8.4.2.2 流力指数

SPI 是地面流侵蚀能力的度量，定义如下（Moore et al. 1991）：

SPI = $A_s \times \tan \theta$ (8.20)

随着特定集水区和坡度梯度的增加，坡上区域贡献的水量和水流速度增加；因此，流力指数和侵蚀风险增加。

SPI 可用于描述地形表面给定点的潜在流蚀及相关景观过程。联合使用时，TWI 和 SPI

### 8.4.2.3 输沙指数

STI 考虑了地形对土壤侵蚀的影响。它源自单位流力理论（Moore and Wilson 1992）。该指数的计算如下：

$STI = \left( \frac{A_s}{22.13} \right)^m \left( \frac{\sin \theta}{0.0896} \right)^n$ (8.21)

where m and n are constants depending on slope length. Usually, m is set to 0.4 and n

## 实践 8.5 参见支持材料

In this practical, you are going to learn how to calculate TWI in ArcGIS Pro or QGIS.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_446_0.png)

图 8.25 流力指数。

to 1.3 (Moore et al. 1991). The value of STI may vary along the length of a stream. STI can be used to characterise the processes of erosion and deposition, and to present the effect of topography on soil loss. For example, Pallaris (2000) applied this index to model erosion risk in the Cabuyal River catchment in Colombia, a typical hillside agro-ecosystem environment under the threat of soil degradation. The results were validated using local farmers’ knowledge and proved that STI is useful for initial erosion assessment at the regional level. This index is sometimes also used in place of the length-slope factor in the revised universal soil loss equation for slope lengths < 100 m and slope < 14° (Moore and Wilson 1992). Figure 8.26 is an STI map derived from the depressionless DEM created in Practical 8.1.

## 8.5 可见性分析

可见性分析涉及确定从某个位置或一组位置沿给定视线或整个区域可以看到什么。它是景观规划中用于评估景观质量和新开发对景观影响的有用工具。例如，它可以用来回答诸如“从一座高 20 米的森林火灾观测站可以看到哪些区域？”、“从规划中的景观道路可以看到哪些陆地区域，以及从道路上可以多频繁地看到这些区域？”和“从一个村庄可以看到多少台风力涡轮机？”等问题。

位置到位置的可见性主要受地形表面形状的影响。在远距离上，可能需要考虑地球曲率。GIS 中通常支持两种可见性分析：视线分析和视域分析。它们基于数字地形模型。

### 8.5.1 视线分析

视线是连接两点的一条线，显示线沿线地形表面不同部分的可见性。**视线分析**确定给定目标是否可从特定观测点看到。如图 8.27 所示，它涉及定义观察点或观测点（有时还有其高度）、目标（及其高度）以及观察点和目标之间的直接视线。如果视线被地形阻挡，则目标被认为不可见；否则，它是可见的。

在 GIS 中，用户可以决定观察点和目标的位置，设置观察点和目标在地形表面以上的偏移（高度），并在 DEM 或 TIN 上交互式地创建两个位置之间的视线。视线将显示线沿线从观察点可见或不可见的地形表面部分。如果目标被地形阻挡，视线还将显示阻挡点的位置。图 8.28 是 DEM 上视线分析的典型输出。

### 8.5.2 视域分析

**视域分析**将视线分析扩展到将研究区域中的每一个可能点作为目标。它用于

