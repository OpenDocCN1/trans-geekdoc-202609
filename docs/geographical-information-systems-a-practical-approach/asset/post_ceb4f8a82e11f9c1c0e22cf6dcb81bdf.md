
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_164_0.png)

First trend line   Second trend line   Third trend line   Fourth trend line   Simplified line

Simplification tolerance

Figure 3.12 Line simplification with the Douglas–Peucker algorithm.

The bend-based approach involves identifying and eliminating insignificant bends along a line or polygon boundary. For example, Wang (1996) proposed an algorithm which applies shape recognition techniques to identify bends along a line or polygon, analyse their geometric properties and remove extraneous ones. A line feature can be viewed as a series of bends. Each bend is defined as a fraction of a line composed of a number of subsequent vertices, with the inflection angles on all vertices included in the bend being either positive or negative and the inflection of the bend's two end vertices being in opposite signs (Wang 1996; Wang and Müller 1998). The algorithm detects bends according to the inflection angles at vertices, then measures several geometrical properties of each bend, such as size, shape and the relationship with its neighbouring bends. These properties determine whether a bend is kept or removed. Bend elimination is carried out by replacing the bend curve with its baseline, the line connecting the end points of the bend. The iteration for generalisation is carried out until the baseline length of every bend on the line is larger than the length of the reference bend baseline, which is a simplification tolerance specified by a user. The bend-based approach generally eliminates fewer points but preserves a geometry that is closer to the original (the main shape and topology of the original line) than the point-based approach does, as shown in Figure 3.13.

While the point-based and bend-based approaches use a threshold distance or length as the simplification tolerance, the area-based approach employs a threshold area as the simplification tolerance. For instance, Visvalingam and Whyatt (1992) proposed an algorithm for line simplification by repeatedly eliminating the smallest triangle formed by three adjacent vertices that is smaller than the pre-set threshold area. In the first step, the algorithm generates triangles between points, as illustrated in Figure 3.14. Then, it identifies the smallest of these triangles and checks whether its area is smaller or bigger than the threshold area. If it is smaller, the point associated with the triangle is removed, and the process starts again – generating new triangles, identifying the smallest one, checking whether the smallest triangle is smaller than the threshold area and repeating. The algorithm stops when all generated triangles are bigger than the threshold area.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_165_0.png)

> **Practical 3.7 See the Support Material**
> 
> In this practical, you are going to learn how to simplify line features in ArcGIS Pro or QGIS.

## 3.4 Spatial Data Editing

**Spatial data editing** aims to remove the errors that arise during the encoding of spatial data, including location, topological and attribute data errors. **Location errors** are positional inaccuracies of digitised features, including locational displacement of features, doubling digitising, omission errors (missing features) and commission errors (features erroneously included in the data when they should have been excluded, possibly because the original sources are outdated). Topological errors are those that violate the topology rules defined by either a GIS system or a user – for example, only one point may exist at a given location, lines must intersect at nodes, polygons are bounded by lines, overlapping polygons do not exist and so on. Undershoot, overshoot, dangling arc and unsnapped node, depicted in Figure 3.3, are all topological errors. Attribute data errors may include incorrect assignment of feature unique identifiers during manual key-in or digitising, missing data records or too many data records. Different from spatial data transformation (discussed in Section 3.3), which corrects systematic errors with regular patterns, spatial data editing is an interactive process involving identification of random spatial and non-spatial errors and graphic editing of these errors.

for comparison. Missing features can be added through digitising, and errors can be corrected using the editing operations described next.

Before using the editing tools in GIS to edit features, the editing environment needs to be set up, which involves defining the tolerances used to snap points and lines. The snap tolerance is a specified distance within which points or features are moved to match or coincide exactly with each other. It can be measured using either map units (for example, metres) or pixels. When the snap distance is defined, in an editing session, the pointer or a feature will snap to another location (vertex, edge, end point, segment, intersection and so on) within that distance. Practicals 3.4 and 3.5 show how to set up the snap environment in ArcGIS Pro and QGIS.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_166_0.png)

Figure 3.14 Line simplification with the Visvalingam–Whyatt algorithm.

### 3.4.1 Editing Individual Features

The easiest way to identify location and topological errors is to plot the digital map at the same scale as its source map and then overlay it with the source map

Individual features can be modified using graphic editing tools. Basic editing operations available in GIS include extend (lines), trim (lines), delete or erase (vertices or features), add (vertices), copy (features), create (features), rotate (features), move (vertices or features), reshape (features) and split and merge (features). Figure 3.15 provides some examples of the basic editing operations.

coincident should be updated simultaneously so that they continue to share geometry.

The operations for editing individual features discussed earlier do not change the shapes and positions of other features with shared geometry. For example, each polygon is treated as separate from other polygons in the data layer. When a polygon is moved, its adjacent, connected polygons remain unchanged. Therefore, the relocated polygon will overlap with some other polygons and leave its original location an empty or void place, which leads to a change in topological relationships among features. In order to maintain the topology (such as coincident borders and nodes), topological associations among the features need to be built, with which boundaries and nodes/vertices shared by multiple features can be edited, moved or reshaped simultaneously. In other words, when a node is moved, all the edges (which are line segments that define lines or polygons) that connect to it are stretched to remain connected to the node. For example, as shown in Figure 3.16, by moving a corner vertex shared by three land lots, the boundaries of the three lots are all updated at the same time. Similarly, when an edge is moved, all the adjacent edges are stretched to stay connected.

### 3.4.2 Editing Features with Shared Geometry

Many vector data layers contain features that share geometry – that is, they have common boundaries or vertices. For instance, a river may be a border between two states, and soil polygons may share borders with land use polygons and shorelines of water bodies. When editing these layers, features that are

| Type of Errors | Before Correction | Edit Function | After Correction |
|---|---|---|---|
| Unclosed Polygon | | Move a vertex | |
| Missing Arc | | Split a feature | |
| Overshoot | | Delete a feature | |
| Undershoot | | Extend a feature | |

Figure 3.15 Examples of basic editing operations.

## Practical 3.8 See the Support Material

In this practical, you are going to learn the basic operations for editing individual features in ArcGIS Pro or QGIS.

In GIS, editing features with shared geometry require first building a map topology, then defining a cluster tolerance. A map topology is a set of topological relationships between coincident parts of features in a data layer or several data layers. For example, a map topology can be constructed between a stream (line) layer and a forest (polygon) layer to ensure that forest boundaries are coincident with streams. With the map topology, coincidental features in all participating data layers can be identified according to a specified cluster tolerance (defined later). When edited with the map topology, features that are coincident are updated simultaneously so that they continue to share geometry. Coincident edges are called topology edges. The points where edges are connected are referred to as topology nodes. In topological editing, they are collectively called topology elements. A cluster tolerance is the distance within which lines (edges) and vertices are close enough to be considered coincident. Lines or vertices that fall within the specified cluster tolerance will be snapped together. Increasing the cluster tolerance may cause more features to be snapped together unintentionally, leading to poor data accuracy and feature distortion. A typical cluster tolerance is at least an order of magnitude smaller than the accuracy of the data. For example, if the features are accurate to 1 m, the cluster tolerance should be no more than 0.1 m. If the data accuracy is unknown, a good strategy is to use the default cluster tolerance and increase it only to handle more severe but localised errors (Chang 2014).

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_168_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_168_1.png)

Figure 3.16 Editing features with shared geometry.
