

| Mapping unit | OM (%) | TN (g/kg soil) | TP (g/kg soil) | TK (g/kg soil) |
|---|---|---|---|---|
| 11 | 25.62 | 1.01 | 0.13 | 1.52 |
| 12 | 25.62 | 1.01 | 0.13 | 1.52 |
| 13 | 25.62 | 1.01 | 0.13 | 1.52 |
| 14 | 0.16 | 0.03 | 0.03 | 2.03 |
| 15 | 0.26 | 0.03 | 0.04 | 2.1 |
| 16 | 25.62 | 1.01 | 0.13 | 1.52 |
| 17 | 25.62 | 1.01 | 0.13 | 1.52 |
| 18 | 3.52 | 0.19 | 0.06 | 1.51 |
| 19 | 2.15 | 0.14 | 0.06 | 1.42 |
| 20 | 2.11 | 0.12 | 0.08 | 1.48 |
| 21 | 2.04 | 0.09 | 0.14 | 1.52 |
| 22 | 25.62 | 1.01 | 0.13 | 1.52 |
| 23 | 4.66 | 0.23 | 0.16 | 1.58 |

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_218_0.png)

**Figure 4.22** PCP from Table 4.1.

Guo et al. (2005) proposed an approach to integrate PCPs and SOMs in multivariate mapping. With their approach, the SOM assigns data items (features such as mapping units and statistical area units) to nodes and colours the nodes according to a systematically designed colour scheme so that nearby or similar nodes have similar colours. A node may be assigned several data items or may have no data items. The SOM itself does not show the original data values. But a node with data items contains four pieces of information: the data items assigned to the node, the number of data items in the node, the mean vector (the mean values of all the data items) and the colour of the node. These pieces of information are utilised by the PCP to draw profile lines of each data item. Every data item (not each node) is then mapped, geographically, with the colour assigned to the node that contains the data item. This map is a multivariate map linked to the non-empty nodes in the SOM's U-matrix and profiles in the PCP. From a thematic mapping perspective, the SOM serves as a multivariate classification method, providing colours for mapping, and the PCP serves as the legend, giving the meanings of those colours. This makes it easy to understand the multivariate data and discover the spatial distribution of various multivariate patterns.

For example, Figure 4.23 shows a multivariate map of four soil properties (that is, four variables) and its linked SOM and PCP created from Table 4.1 using multivariate mapping software SOMVIS (Guo et al. 2005). In the U-matrix, the scaled circle in a node hexagon depicts the number of data items in the node. Each circle is filled with a colour. The colour is used to draw the profile lines of the data items (soil mapping units) contained in the node in the PCP and to map the data items onto the soil property map. Similar colours in the PCP and map represent similarities in terms of the four soil properties (input variables). The thickness of a profile line in the PCP is also scaled to the total number of data items contained in a node. By interpreting the PCP, the distribution of the four soil properties in each mapping unit can be understood. The map is effectively a multivariate map with four variables.

With modern visualisation technology such as SOMVIS, multivariate mapping provides a visual approach to exploring and understanding spatiotemporal and multivariate patterns in spatial data facilitated by interactive visual interfaces.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_220_0.png)

Figure 4.23 Multivariate mapping with SOM and PCP.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_220_1.png)

Figure 4.24 3D perspective view of an elevation surface.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_221_0.png)

Figure 4.25 Stepped statistical surface of Australian population (by state).

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_221_1.png)

Figure 4.26 A 3D model of the Barwon Downs Graben aquifer.

Source: Created using GOCAD. Courtesy of Sultana Nasrin Nury.

can be thought of as the 3D counterparts to the pixels in 2D. A voxel is usually a cube of equal sides. A 3D model of a landscape is formed by a voxel grid, which divides the 3D space over the area into layers of rows and columns (Figure 4.29). A small 3D cube at each row, column and layer intersection in the grid is a voxel. A voxel may have values representing various properties or have no value. An object or phenomenon in 3D space can be represented using a collection of voxels with particular values,

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_222_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_222_1.png)

Figure 4.27 Vertical cross sections of the 3D model of the Barwon Downs Graben aquifer: (a) in the north-west-to-south-east direction and (b) in the south-west-to-north-east direction.

Source: Created using GOCAD. Courtesy of Sultana Nasrin Nury.

as shown in Figure 4.29. The size of a voxel determines the resolution of the 3D model. Voxels are 3D building blocks that can be used to represent complex objects. They have been used to build 3D models of urban environments (Anderson et al. 2018; Nourían et al. 2016), archaeological features (Orengo 2013), forest structures (Popescu and Zhao 2008), terrains and subsurface geological structures (Graciano et al. 2018), morphological patterns (Remmel 2022) and marine environmental characteristics (such as temperature, salinity, dissolved oxygen, nitrate, phosphate and silicate) (Wright et al. 2018). A high-resolution voxel-based 3D model can replicate real-world objects

or phenomena that would be impossible to differentiate from the real thing – in appearance and behaviour. The 3D model of dissolved oxygen in Figure 4.28 was indeed constructed using voxels. A 3D dataset structured and represented using voxels is sometimes called a voxel layer. A voxel layer may be rendered using various volume rendering techniques or by extracting isosurfaces. An isosurface is the 3D equivalent of an isoline (Copsey 2002). It is a 3D surface formed by joining points with equal values of a continuous variable (for example, air pressure, temperature and density) in a 3D space. Figure 4.30 shows two isosurfaces (in pink) draped on top of

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_223_0.png)

Figure 4.28 A 3D model of dissolved oxygen in the ocean in Monterey Bay, California.

Source: Data from the NOAA National Centers for Environmental Information's World Ocean Database.

a bathymetry map in a 3D scene. The two isosurfaces represent the dissolved oxygen level of 0.5 μmol/L in Monterey Bay. Isosurfaces provide information about the spatial distribution of a variable at a specific value in a 3D environment.

while isosurfaces are hard surfaces at user-selected values, **volume rendering** produces soft surfaces by blending the contributions from multiple surfaces, integrating the contribution from the entire volume (Levoy 1988; Slocum 2005). By carefully classifying the range of values to the various source contributions to the volume and mapping these classified values using colour and transparency, individual

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_224_0.png)

Figure 4.29 Voxel representation of a 3D tree in geographical space.

surfaces can be resolved in the rendered image. Basically, the method renders an image of a 3D dataset using the metaphor of passing light through semi-transparent objects, which allows the identification of internal structures, which are occluded by the external levels of the volume. Figure 4.31 is an example of volume rendering of the 3D model in Figure 4.28. Volume rendering is often used as a visualisation tool for datasets created by mapping 3D data to density and colour values to allow the viewer to recognise shapes and patterns within the otherwise-opaque features.

A voxel layer is a 3D raster representation of geographical space. Some GIS systems also support the vector representation of 3D phenomena. With the vector approach, true 3D geometric structures can be represented by multipatch features, which are made of planar 3D rings and triangles stitched together to model 3D objects like trees and buildings with overhanging features (Kennedy 2009). **Multipatches** represent the outer surface or isosurfaces of 3D features. They store texture, colour, transparency and geometric information representing different parts of the features. They are particularly useful for representing urban features to create 3D urban models to provide contexts

