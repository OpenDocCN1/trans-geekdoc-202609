

# Python 绘制莫比乌斯带

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Define the parameters of the Möbius strip
R = 2

# Define the Möbius strip surface
u = np.linspace(0, 2 * np.pi, 100)
v = np.linspace(-1, 1, 100)
u, v = np.meshgrid(u, v)
x = (R + v * np.cos(u / 2)) * np.cos(u)
y = (R + v * np.cos(u / 2)) * np.sin(u)
z = v * np.sin(u / 2)

# Create the plot
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

# Plot the Möbius strip surface
ax.plot_surface(x, y, z, alpha=0.5)

# Set plot properties
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.set_title('Möbius Strip')

# Set the limits of the plot
ax.set_xlim([-3, 3])
ax.set_ylim([-3, 3])
ax.set_zlim([-3, 3])

# Show the plot
plt.show()
```

**输出：**

![](image_rsrc9WF.jpg)

图 5.11 莫比乌斯带绘图

# 5.12 为什么地理空间数据可视化如此重要？

地理数据科学是数据科学的一个子集，专门处理基于位置的数据，即空间中物体的描述及其关系。在当今世界，地理数据至关重要，大多数业务/应用/服务都围绕位置要素展开。因此，为了从基于位置的数据集中更快地获取洞察，可视化显得尤为重要。

沟通技巧对所有工作都至关重要，而地理空间数据可视化是呈现地理信息以得出结论的有效模式。此外，人类大脑捕捉和保留图形/图像比包含信息的数百行电子表格容易得多。因此，信息的可视化摘要使识别模式和趋势以获取洞察变得更加容易。总之，地理空间数据可视化提供：

*   轻松可视化位置相关信息的能力，并改善洞察以促进决策
*   向受众传达他们能理解的信息的改进能力
*   无需口头解释即可获得更易访问和理解的信息
*   基于观察采取行动的能力增强，从而以更大的敏捷性取得成功

# 如何使用开源库创建地理空间数据可视化？

存在各种支持创建地理空间可视化的库，下面列出了其中几个（列表不详尽）：

*   **folium**：它构建在 Python 生态系统的数据处理优势和 `leaflet.js` 库的映射优势之上
*   **d3-geo** —— 用于以地图形式渲染地理信息的 JavaScript 库
*   **mplleaflet** —— 一个将 `matplotlib` 图表转换为包含可平移、可缩放的 Leaflet 地图网页的 Python 库。它还可以在 IPython 笔记本中嵌入 Leaflet 地图
*   **geoplot**：一个高级 Python 地理空间绘图库。它是 `cartopy` 和 `matplotlib` 的扩展，使制图变得简单：就像地理空间领域的 `seaborn`
*   **geoJs**：旨在弥合 GIS、地理空间可视化、科学可视化和信息可视化之间的差距。`geoJs` 不仅仅是一个 GIS 库，因为用户可以创建矢量图和等高线图等科学图表，并使用 `D3.js` 嵌入信息可视化图表

# Folium 库

`Folium` 构建在 Python 生态系统的数据处理优势和 `Leaflet.js` 库的映射优势之上，帮助可视化地理空间数据。数据在 Python 中处理，然后通过 `folium` 在 Leaflet 地图中可视化。这些地图具有交互性，可以基于纬度和经度值构建，并可直接在笔记本环境中可视化，这是大多数人所偏好的。

## 安装

`Folium` 可以通过以下两种方法中的任意一种安装在系统上：

```bash
$ pip install folium
```

或

```bash
$ conda install -c conda-forge folium
```

## 探索性数据分析

```python
# Import necessary libraries
import pandas as pd  # data processing, CSV file I/O (e.g. pd.read_csv)

# !pip install folium — install folium library for mapping
import folium
from folium.plugins import MarkerCluster

# Import property attributes dataset
df = pd.read_csv("innercity.csv")

# Check a few rows of the loaded dataset to ensure if data is loaded is correctly
df.head()

# Check the shape of dataframe
df.shape
# (21613, 23)

# Property data contains 21,613 observations with 23 fields/attributes.

# Check the name of fields in data
df.columns
# Index(['cid', 'dayhours', 'price', 'room_bed', 'room_bath', 'living_measure',
#        'lot_measure', 'ceil', 'coast', 'sight', 'condition', 'quality',
#        'ceil_measure', 'basement', 'yr_built', 'yr_renovated', 'zipcode',
#        'lat', 'long', 'living_measure15', 'lot_measure15', 'furnished',
#        'total_area'],
#       dtype='object')

# Folium need latitude/longitude attributes in the data to be able to run its functionalities and this dataset has these two fields.

# Check the data type and null values present in fields.
df.info()

# Count of unique values in each field
df.nunique()

# Check for missing values
df.isnull().sum()

# Check rows with missing values
df[df.isnull().any(axis=1)]

# Viewing the data statistics
df.describe()
```

`describe()` 函数说明数据中各字段/属性存在 0 值。这些零值是否有意义或需要清洗，需要进一步的数据探索。数据中也存在一些异常值（例如 `room_bed` 字段 75% 的数据在 3 卧室的范围内，但最大值出现了 33 这样的值），需要用正确的策略进行填补。数据中也存在偏度。

上述分析与可视化无关，但深入审视你计划处理的数据非常重要，这是优秀数据科学家的标志 :)

## 使用 Folium 库进行地理空间数据可视化

`Folium` 是一个强大的 Python 库，有助于创建多种地图可视化，如地图、聚类地图、地形图、热力图等。`Folium` 地图具有交互性且易于使用，这使得该库在 Jupyter 笔记本或仪表板构建中非常强大。为了演示其部分功能，下面通过代码片段展示了一些示例。

### 带简单标记的地图

```python
# Plotting the map of property data location with OpenStreet as basemap
# Create Map: Basemap — OpenStreet Map
property_map = folium.Map(
    location=[df['lat'].mean(), df['long'].mean()],
    zoom_start=11,
    control_scale=True,
)

for i in range(len(df)):
    folium.CircleMarker(
        location=[df.lat.iloc[i], df.long.iloc[i]],
        radius=3,
        popup=df.cid.iloc[i],
        color='blue',
        opacity=0.2
    ).add_to(property_map)

property_map
```

`folium.Map` 类函数中有几个参数，详细讨论如下：

*   **`folium.Map()`**：`property_map` 对象是通过 `folium.Map()` 对象创建的，它保存与地图中心、缩放、比例、瓦片等相关的信息
*   **`location`**：`folium.Map()` 对象中的 `location` 参数有助于定义**纬度（Y 值）**和**经度（X 值）**字段以定义地图中心。有多种方法可以定位地图中心：要么指定中心坐标（如果你知道在哪里定位地图），通过提供纬度和经度值（`location=[47.6062, -122.3321]`）；要么从数据中获取纬度和经度的平均值（`location=[df['lat'].mean(), df['lon'].mean()]`）
*   **`zoom`**：`zoom` 参数设置地图首次渲染时的放大级别
*   **`tiles`**：此处未添加 `tiles` 参数选项，因为默认瓦片 `OpenStreetMap` 被用作背景地图。可以在 `folium` 中指定各种瓦片服务器作为背景地图

在 `folium` 类方法中也可以设置各种参数，你可以从 [folium github](https://python-visualization.github.io/folium/modules.html) 阅读相关内容。

