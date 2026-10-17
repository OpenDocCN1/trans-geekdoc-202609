
# ANGLE

["",0.11745292519433

```r
linewidth = 1,
show.legend = F) +
coord_sf()
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_209_0.png)

(a) 非洲地图 (b) 彩色的非洲地图

图 12.1 非洲地图

## 12.3 坐标参考系统 (CRS)

`坐标参考系统 (CRS)` 是是一种定义地球表面特征空间位置的标准化方法。它使用一组坐标来表示空间中点、线和多边形的位置。有不同类型的 CRS，例如`地理` CRS 和`投影` CRS，用于以不同的方式表示地球表面。地理 CRS (`LatLong`) 使用纬度和经度在曲面上表示位置以用于全球制图，而投影 CRS 或`通用横带墨卡 (UTM)` 将曲面地球投影到平面地图上，使用米进行精确制图。特别是，UTM 系统提供了从赤道到特定区域带中央经线的米制距离。

我们使用 `sf` 包来定义和转换 CRS。`st_crs()` 函数允许你检索空间对象的 CRS，而 `st_transform()` 函数允许你将空间对象的坐标转换到不同的 CRS。

```r
africa_crs <- st_crs(africa)
africa_crs
# 坐标参考系统:
# 用户输入: WGS 84
# wkt:
# GEOGCRS["WGS 84",
# DATUM["World Geodetic System 1984",
# ELLIPSID["WGS 84",6378137,298.25723563],
# LENGTHUNIT["metre",1]]
# PRIMEM["Greenwich",0,
# ANGLE["Greenwich",0,
# UNIT["degree",180/PI]],
# AXIS["longitude",0,0",0,1,
# UNIT["degree",180/PI]],
# AXIS["latitude",0,0,
ORDER[1],
# ANGLE
["",0.11745292519433
```

# 示例：中非共和国的感染模拟

`as.data.frame()` 函数将矩阵转换为数据框，而 `dplyr::select()` 函数用于选择经度和纬度列。`summary()` 提供了数据框的摘要，包括经度和纬度值的平均值、中位数和四位数。

```r
ctr_africa_coords <- ctr_africa %%
sf::st_coordinates() %%
as.data.frame() %%
dplyr::select(X, Y)
```

```r
ctr_africa_coords %%
summary()
# Min. : 14.46  Min. : 2.268
# 1st Qu.: 16.58  1st Qu. : 4.648
# Median : 20.96 Median : 5.3564
```
