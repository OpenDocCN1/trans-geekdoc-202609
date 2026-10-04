

# 疾病传播动力学

```r
# 根据感染状态分配颜色
V(small_world_dev)$color <- ifelse(small_world_dev)$status == "I", "black", "grey80")
```

绘制图形：

```r
par(mfrow = c(i,2))
set.seed(06082024)
plot(small_world,
vertex.size = 8,
vertex.label = NA,
edge.arrow.size = 0.5,
edge.width = 0.5)

plot(small_world_dev,
vertex.size = 8,
vertex.label = NA,
edge.arrow.size = 0.5,
edge.width = 0.5)
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_221_0.png)

**图 12.7** 小世界网络可视化：感染前后的结构。

我们使用中非共和国的点网格进行预测，并将其转换为简单的特征对象，为了简单起见，使用了协变量的平均值。

```r
ctr_africa_grid <- ctr_africa_grid_full %>%
  filter(pip == 1)

ctr_africa_grid_sf <- ctr_africa_grid %>%
  st_as_sf(coords = c("x", "y"), crs = 4326) %>%
  st_make_valid() %>%
  mutate(temperature = mean(df$temperature))

infected_sf <- df_sf %>%
  filter(presence == 1) %>%
  st_make_valid()
```

# 空间数据建模与可视化

在中非共和国地图上可视化点网格和观测到的感染。为了理解感染的空间分布和协变量，我们使用上述空间世界网络来模拟个体之间的连接。根据合成数据 (df_sf) 为空间世界网络的节点分配属性。这些属性包括个体类型（已感染或未感染）、纬度和经度坐标以及感染者人数。网络的边代表节点之间的连接。

```r
coords <- st_coordinates(df_sf)
# 为节点分配属性
V(small_world)$presence <- df_sf$presence
V(small_world)$longitude <- coords[,1]
V(small_world)$latitude <- coords[,2]
V(small_world)$cases <- df_sf$cases
```

```r
edges <- igraph::as_data_frame(small_world, what = "edges")

nodes <- coords %>%
  as_tibble() %>%
  rename(longitude = X, latitude = Y) %>%
  mutate(id = 1:nrow())
```

```r
edges <- edges %>%
  left_join(nodes, by = c("from" = "id")) %>%
  rename(lat_from = latitude, lon_from = longitude) %>%
  left_join(nodes, by = c("to" = "id")) %>%
  rename(lat_to = latitude, lon_to = longitude)
```

```r
ggplot() +
  geom_sf(data = ctr_africa_grid_sf,
  shape = 21, stroke = 0.5,
  fill = NA, size = 0.5, color = "grey") + 
  geom_sf(data = infected_sf,
  aes(size = cases),
  shape = 21, stroke = 0.2, color="black") + 
  scale_color_continuous(name = "Observed",
  low = "white", high = "red") + 
  labs(title = "Observed Infections") +
  theme(legend.position = "right")
```

```r
ggplot() +
  geom_sf(data = ctr_africa_grid_sf, fill = NA) +
  geom_sf(data = ctr_africa_grid_sf,
  shape = 21, stroke = 0.5,
  fill = NA, size = 0.5, color = "grey") + 
  geom_segment(data = edges,
  aes(x = lon_from, y = lat_from,
  xend = lon_to, yend = lat_to),
  color = "grey20", alpha = 0.2, linewidth = 0.2) + 
  geom_sf(data = df_sf,)
```

# 疾病传播动力学

```r
aes(shape = factor(presence),
color = factor(presence),
size = 0.5) +
  geom_sf(data = infected_sf,
  aes(size = cases),
  shape = 21, stroke = 0.2, color="black") + 
  guides(color = "none") +
  scale_color_manual(values = c("0" = "grey20", "1" = "red")) + 
  labs(title = "Small-World Network with Infection Status",
  y = "Longitude", shape = "Presence") + 
  theme(legend.position = "right")
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c_223_0)

(a) 观测感染规模
(b) 感染状态与小世界网络
图 12.8 中非共和国地图
个体之间的近距离接触聚集是疾病传播的重要因素，也是许多数学模型的主题。

## 12.5.1 欧式距离

为了根据空间邻近性估计个体之间的传播概率，使用了欧式距离。它被计算为两个点坐标差平方和的平方根。

欧式距离公式：

$d_{i,j} = \sqrt{(x_i - x_j)^2 + (y_i - y_j)^2}$ (12.1)

其中 $(x_i, y_i)$ 是第一个点（A，例如已感染个体）的经纬度，$(x_j, y_j)$ 是第二个点（B，例如易感个体或位置）。

它计算了二维空间内两点之间的直线距离，可以根据个体或位置的接近程度来模拟疾病的空间传播。

为了计算欧式距离，我们建立了一个考虑质心坐标之间距离的函数。

![](img/6b61f0d3dcab44c60cdfe4e888d54c9.png)

**图 12.9** 点 A 和 B 之间的欧式距离表示

```r
# 计算欧式距离指标的辅助函数
euclidean_distance <- function(longitude, latitude,
  long_com, lat_com) {
  long_distances <- (longitude - long_com)^2
  lat_distances <- (latitude - lat_com)^2
  return((long_distances + lat_distances) * 0.5)
}
```

还有其他类型的距离指标可以使用，例如**曼哈顿距离**（Manhattan distance），它计算两点坐标之间的绝对差之和；**马氏距离**（Mahalanobis distance），它考虑变量之间的相关性；以及**切比雪距离**（Chebyshev distance），它计算两点坐标之间的最大差异。

## 12.5.2 空间自相关性

空间自相关性是指这样一个原理：相邻的空间点比远离的点更有可能具有相似的值。通过分析病例的空间分布，可以发现感染扩散剧烈的区域。

使用 **Moran's I** 及其变体工具，可以通过识别病例聚集的区域来检测感染热点。为了检查空间自相关性的存在，使用了全局莫兰（Global Moran's）法则：

$I = \frac{N \sum_{i=1}^{N} \sum_{j=1}^{N} w_{ij}(x_i - \bar{x})(x_j - \bar{x})}{W \sum_{i=1}^{N} (x_i - \bar{x})^2}$ (12.2)

其中 $x_i$ 和 $x_j$ 是位置 $i$ 和 $j$ 处感兴趣变量的值$\bar{x}$ 是平均值，$N$ 表示空间单元的数量，$w_{ij}$ 是位置之间的空间权重。

$I$ 衡量感染聚集、分散或随机分布的程度，取值范围从 -1（完全分散）到 +1（完全聚集）。值为0表示没有空间自相关，表明为随机模式。

# 疾病传播动力学

我们使用 **spdep** 包，它提供了 `dnearneigh()`、`nb2listw()` 和 `moran.test()` 函数，分别用于根据距离计算邻接通性、空间权重以及最后的 Moran I。

```r
library(spdep)
library(sp)
```

```r
coordinates(df) <- longitude + latitude
# 定义邻居（例如使用距离）
# 2单位内的邻居
nb <- dnearneigh(coordinates(df), 0, 2)

# 创建空间权重
lw <- nb2listw(nb, style="W")

# 计算感染的 Moran I
moran_result <- moran.test(df$cases, lw)
moran_result
>
# 随机化下的 Moran I 
>
# 数据: df$cases
# 权重: lw
>
# Moran I 统计量偏差 = -0.18432, p值 = 0.5731
# 备择假设: 大
# 样本估计:
# Moran I 统计量          期望          方差
#               -0.01260435-0.011011001      0.000184511
```

虽然 Moran I 对理解感染整体的空间模式很有用，但它没有提供区域内病例分布的详细信息。为了估计感染的空间分布并预测爆发风险，可以使用空间插值技术，如克里金（Kiging）。⁵

该方法通过创建预测感染空间分布的栅格来估计病例的空间分布。它通过插值整个区域的人数，创建一个估计整个区域感染风险的连续表面。

> ⁵“Kriging.” 2024年7月18日， https://en.wikipedia.org/w/index.php?title=Kriging&oldid=1235203584.

