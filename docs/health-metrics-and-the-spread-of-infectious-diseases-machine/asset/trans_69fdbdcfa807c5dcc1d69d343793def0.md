

198

空间数据建模与可视化

# 窗口网格

# 网格地图

P/G 0 - 1

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_216_0.png)

(a) 带有窗口网格的中非共和国地图
(b) 中非共和国的网格地图

图 12.4 中非共和国地图

## 12.4.7 创建温度栅格数据

为了在中非共和国的地图上视觉化温度数据，我们创建了一个栅格模板。该栅格模板的范围与模拟的感染位置相同，并将被用于对温度数据进行栅格化。这意味着温度数据将转换为栅格格式，栅格网格中的每个单元格代表一个特定的温度值。栅格化后的温度数据将以热图的形式在地图上进行可视化，颜色越暖表示温度越高。

栅格模板是使用 {terra} 包中的 `rast()` 函数创建的，并指定了行数、列数、x 和 y 坐标的最小值和最大值，以及栅格的坐标参考系统 (CRS)。如果你想了解更多关于该包的信息，输入 `terra`。

栅格模板应包含 18 行 36 列，x 和 y 坐标范围范围为 11 到 28 以及 2 到 12。

```r
library(terra)
raster_template <- terra::rast(nrows = 18, ncols = 36,
xmin = 11, xmax = 28,
ymin = 2, ymax = 12,
crs = st_crs(df_sf)$projstring
```

使用 `rasterize()` 函数对温度数据进行栅格化，将温度数据从数据框（frame）转换为栅格格式。温度数据根据经纬度坐标分配给栅格单元格。

```r
ctr_africa_raster <- rasterize(df_sf,
raster_template,
field = "temperature",
fun = max)
```

在中非共和国地图上绘制栅格化后的温度数据之前，我们需要将栅格化后的数据转换为数据框格式。这将允许我们以热图的形式在地图上视觉化温度数据。栅格化数据包含栅格网格中每个单元格的温度值，这些值根据经纬度分配。

# 示例：中非共和国的感染模拟

温度数据的坐标。
ctr_africa_raster_df <- as.data.frame(ctr_africa_raster,
y = TRUE)

```r
ctr_africa_raster_df %>% head()
#> x y max
#> 200 20.20833 8.944444 24.09246
#> 203 21.62500 8.944444 21.51325
#> 205 22.56944 8.944444 23.46981
#> 234 19.26389 8.38889 25.77824
#> 235 19.73611 8.38889 25.11388
#> 268 18.31944 7.833333 25.24466
```

## # 温度栅格

```r
ggplot() + 
geom_raster(data = aes(x = x, y = y, fill = max)) +
  viridis::scale_fill_viridis(name = "transparent") +
  labs(title = "Rasterized Temperature") + 
theme(legend.position = "right")
```

## # 中非栅格

```r
ggplot() + 
geom_point(data = ctr_africa_raster_df %>% filter(pip == 1),
  aes(x = x, y = y),
  shape = ".") + 
geom_raster(data = ctr_africa_raster_df,
geom_sf(data = df_sf %>% filter(presence == 1),
  aes(size = cases),
  shape = 21, stroke = 0.3) + 
scale_fill_gradient(low = "white", high = "grey30",
  na.value = "transparent") +
labs(title = "Max Temperature in Central African Rep.",
  subtitle = "Simulated Values",
  size = "Number of Infections",
  fill = "Max Temperature") + 
theme(legend.position = "right")
```

此图在中非共和国的地图上以热图的形式显示温度，颜色越暖表示温度越高。感染位置用圆圈表示，圈的大小表示每个位置感染的人数。

## 12.4.8 感染中心

代表该地区感染空间分布的中心是质心。它是研究疾病传播空间动力学和识别干预关键区域的重要指标。为了计算感染质心（也称为感染中心）的坐标，我们使用 `center_of_mass()` 函数。

空间数据建模与可视化

栅格化温度

中非共和国基于最大温度的尺寸模拟感染带质心的合成数据

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_218_0.png)

(a) 温度栅格
(b) 中非共和国温度等级地图

图 12.5 中非共和国栅格感染与温度等级地图

质心是根据每个位置感染人数对经纬度进行加权平均。

```r
center_of_mass <- function(df) {
  longitude <- sum(df$cases * df$longitude) / sum(df$cases)
  latitude <- sum(df$cases * df$latitude) / sum(df$cases)
  c(longitude, latitude)
}
```

```r
df_com <- tibble(longitude = center_of_mass(df) [1],
latitude = center_of_mass(df) [2])
df_com
```

```r
# A tibble: 1 x 2
  longitude latitude
  <dbl>     <dbl>
1         20.7      6.47
```

最后，在中非共和国地图上绘制感染情况，并带有小世界层。质心是根据每个位置感染人数对经纬度进行加权平均。

# 中非共和国的感染模拟
中非共和国基于最大温度的尺寸模拟感染带质心的合成数据

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_219_0.png)

(a) 模拟位置散点图
(b) 中非共和国的感染位置

图 12.6 中非共和国地图

