
the centre cell to the neighbouring cell j. For the four orthogonal neighbours, $d_{0j}$ is the cell size. For the four diagonal neighbours, $d_{0j}$ is the cell size × 1.414 (the square root of 2). Let $D_{max}$ be the largest distance-weighted drop in elevation for a cell. The following rules are used to determine flow direction at the cell (Jenson and Domingue 1988):

- IF $D_{max} < 0$
- The cell is a single-cell sink, which does not occur for a depressionless DEM. The cell is filled to the lowest value of its neighbours and has a flow direction to that neighbour.

- ELSE, IF $D_{max} \ge 0$ at only one neighbour,
- The cell is assigned the flow direction to that neighbour.

- ELSE, IF $D_{max} \ge 0$ at more than one neighbour (the cell has $D_{max}$ in multiple directions).

IF the cell is part of a sink (or a flat area)
The flow direction is undefined.

ELSE
The cell is assigned the most likely flow direction according to a lookup table, as in Greenlee (1987).

Figure 8.14 illustrates how flow direction is derived in ArcGIS using a simple example. The flow direction tool in ArcGIS implements the D8 algorithm to generate a flow direction raster. The tool uses the neighbour location codes shown in Figure 8.15 to encode the flow direction of a cell. For example, if a cell flows to the upper-right neighbour, its flow direction value would be 128. If a cell flows down, its flow direction value would be 4. If a cell has the largest drop in multiple directions and that cell is part of a sink, its flow direction value would be the sum of the neighbour location codes in those directions. For example, if a cell's largest weighted drop in elevation is both to the left and up, its flow direction value would be 16 + 64 = 80. If all neighbour elevations were equal to the centre cell, the centre cell would receive a flow direction value of 255.

| 1180 | 1168 | 1162 |
|---|---|---|
| 1190 | 1210 | 1170 |
| 1200 | 1225 | 1180 |

| 42 | 42 | 68 |
|---|---|---|
| 20 | | 40 |
| 14 | -15 | 30 |

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_435_0.png)

Figure 8.14 Identification of flow direction: (a) DEM, (b) weighted drops and (c) flow direction.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_436_0.png)

Figure 8.15 Neighbour location codes used by the flow direction tool in ArcGIS.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_436_1.png)

- 1
- 2
- 4
- 8
- 16
- 32
- 64
- 128

0 2.5 5 10 Kilometers

Figure 8.16 Flow direction raster.

Thus, flow direction values range from 1 to 255. Figure 8.16 shows a flow direction raster derived from the same depressionless DEM created in Practical 8.1.

accumulation provides a basis for delineating drainage networks and identifying ridgelines.

## 8.4.1.6 Flow Accumulation

**Flow accumulation** refers to how much water accumulates from upstream areas and contributes to overland flow. It is basically calculated as the number of upstream cells that flow into each cell based on their flow directions. Figure 8.17 illustrates how flow accumulation is computed based on flow direction. The value of each cell in the flow accumulation raster is the number of cells that flow into it (the cell itself is not considered), and the arrows indicate flow directions. Locations having high flow accumulation values are the areas of concentrated flow, generally corresponding to stream channels, while locations having an accumulation value of zero correspond to the pattern of ridges. Therefore, flow accumulation provides a basis for delineating drainage networks and identifying ridgelines.

Weights can also be applied to each cell when calculating flow accumulation. For example, when multiplied by the area size of a cell, the flow accumulation value is equal to the size of the drainage area or the contributing area. When multiplied by average rainfall in each cell during a given storm, the flow accumulation value represents the amount of rain that flowed through each cell or the amount of rain that fell in the upslope area of each cell, on the assumption that all rain became runoff and there was no interception, infiltration and evaporation. Figure 8.18 is the flow accumulation map derived from the depressionless DEM created in Practical 8.1.

## 8.4.1.7 Drainage Network

Flow accumulation is used to create a drainage network based on the flow direction of each cell. By selecting cells with a flow accumulation value greater than some threshold value, a network of high-flow cells can be generated. These high-flow cells should lie on stream channels and at valley bottoms. However, by applying a threshold value, drainage networks can be extracted from a DEM with arbitrary drainage density. In general, the density of the drainage network decreases as the threshold value increases. The two drainage networks in Figure 8.19 were both derived from the flow accumulation map in Figure 8.18. Figure 8.19a was produced with a threshold value of 1,000 cells, while Figure 8.19b was based on a threshold value of 7,000 cells. Different threshold values need to be tried to select the most appropriate one so that the extracted drainage network corresponds to or is close to the one obtained by more traditional methods, such as from high-resolution topographic maps or fieldwork. Several other criteria have also been proposed for extracting drainage networks from DEMs, such as a threshold on local slope, a combination of drainage area and slope, a threshold on local curvature and a threshold slope-direction-change (Heine et al. 2004; Lashmeres et al. 2007).

**Flow direction**

| 2 | 2 | 2 | 4 | 4 |
|---|---|---|---|---|
| 2 | 2 | 1 | 1 | 8 |
| 2 | 2 | 4 | 4 | 8 |
| 2 | 2 | 2 | 4 | 16 |
| 1 | 1 | 2 | 4 | 16 |

**Flow accumulation**

| 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|---|
| 0 | 1 | 1 | 4 | 6 |
| 0 | 1 | 4 | 7 | 0 |
| 0 | 1 | 2 | 10 | 0 |
| 0 | 2 | 5 | 18 | 0 |

Figure 8.17 Flow accumulation calculated as the number of cells that flow into each cell.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_438_0.png)

Figure 8.18 Flow accumulation map.

## 8.4.1.8 Stream Order

As shown in Figure 8.20, a drainage network through which water travels to the outlet or pour point can be seen as a tree, with the root of the tree being the outlet downstream and the branches being stream channels. A point at which two upstream channels join to form one downstream channel is referred to as a node or junction. The sections of a stream channel connecting two successive junctions or a junction and the outlet are called stream links. Stream links are often ordered for the purposes of identifying and classifying types of streams based on their numbers of tributaries in order to infer their characteristics. There are two main methods for stream ordering: the Strahler method and the Shreve method.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_439_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_439_1.png)

Figure 8.19 Drainage networks based on threshold values of (a) 1,000 cells and (b) 7,000 cells.

With the Strahler method (Strahler 1952), stream links with no tributaries (that is, headwater flow paths) are assigned the number 1, referred to as first-order. Where two first-order links converge, the downslope link is assigned an order of 2. Where two second-order links meet, the downslope link is assigned an order of 3.

And so on (Figure 8.21a). Where a lower-order stream (for example, first-order) joins a higher-order stream (for example, third-order), the downslope link will retain the higher order (that is, third-order). Only where two links of the same order join will the order increase. This is the most common method of stream ordering.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_440_0.png)

Figure 8.20 Drainage network and related concepts.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_440_1.png)

Figure 8.21 Stream ordering: (a) the Strahler method and (b) the Shreve method.

The Shreve method orders streams by adding order numbers at the confluence of each stream link (Shreve 1967). It also starts at the headwaters – that is, all stream links with no tributaries are assigned an order of 1. When two links join, their order numbers are added to the downslope link (Figure 8.21b). For example, where a first-order joins a second-order stream link, the downslope link is assigned an order of 3.

Stream ordering is an effective way to classify waterways and is a crucial step in understanding and managing the many differences between streams of different sizes. It can be of assistance in studying the amount of sediment in an area, determining the number and types of organisms present in a stream of a given size, designing water quality monitoring and management plans and using waterways as natural resources in an effective and sustainable manner. For example, many more plants can live in sediment-filled slower-flowing high-order streams than in a fast-flowing low-order tributary of the same river. As another example ordered using the Strahler method, third- or higher-order streams are likely to be valuable fish habitats and hence could support viable fish populations. Therefore, fish passage barriers located in third- or higher-order streams should be considered for remediation.

## 8.4.1.9 Flow Length

**Flow length** is the distance or weighted distance along a flow path, either upstream or downstream. It can be used to calculate the length of the longest flow path. Upstream flow length is the longest distance along the flow path from each cell to the top of the drainage divide. Downstream flow length is the distance along the flow path from each cell to a sink or outlet on the edge of the mapped area. Upstream flow length is often used to calculate the time of flow concentration within a catchment, which is useful for surface runoff modelling. Figures 8.22a and 8.22b show an upstream and a downstream flow length map, respectively, derived from the depressionless DEM created in Practical 8.1.

## 8.4.1.10 Catchment Boundary

A catchment is an area that drains water and other substances to a common outlet. It is also called a drainage basin, watershed, basin or contributing area. All land is in one catchment or another. Catchment boundaries are dependent on topography but can be drawn to show smaller parts of larger catchments based on the locations of selected pour points. Traditionally, a catchment boundary is traced on a topographic map by starting at an outlet, determining flow directions, locating ridgelines and saddles, marking high points and connecting the high points with smooth lines that cross contours at right angles. In GIS, catchment boundaries are delineated from DEMs by automatically identifying ridgelines between catchments based on a specific set of pour points. Figure 8.23 shows an example of catchment boundaries delineated from the depressionless DEM created in Practical 8.1.

Delineation of catchment boundaries is important to any study of the water budget of an area, the impact of human activities on water quality or quantity or the development of water resources.
