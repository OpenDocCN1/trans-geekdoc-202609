important industries include forestry, beef and the small-scale cultivation of crops such as pineapples, melons and pumpkins. Land not used for arable agriculture is mainly under native vegetation or improved pasture for beef production. Small areas are utilised for mining and industrial activities. The study area is located in the south-east of the catchment (known as the ‘Lower Herbert’), where sugarcane is the dominant land use.

This study aimed to assist industry and government users to explore and evaluate different land allocation scenarios for sugarcane production in the catchment. It used SMARTER (see Section 9.1) to help users identify those criteria that were important for sugarcane land allocation, make subjective assessments of relative importance of those criteria and convert the assessments into a set of weights. GIS was used to develop map data layers to represent the identified allocation criteria and potential constraints for sugarcane land use, combine these map layers through spatial modelling, identify the suitable land for sugarcane production by applying the SMARTER weights and generate map presentations of land allocation scenarios.

A detailed GIS database was collated, containing map data layers for land use/ cover, slope, elevation, land suitability for sugarcane, roads, rivers, mill locations and flood-prone areas. All map data layers were in the ARC/INFO GRID format, with a cell resolution of 100 m × 100 m. ArcView (the early version of ArcMap) was used for the analysis.

The following procedure was used:

+   1 Define land use constraints and allocation criteria.

Land use constraints represent restrictions imposed on areas for sugarcane production. They define regions of certain biophysical and environmental conditions which are unsuitable for sugarcane. These include areas where state forests, national parks, wetlands or flood-prone areas are located. The criteria for sugarcane land allocation include land suitability, slope, proximity to existing mills, proximity to roads, shape compactness of sugarcane land blocks and fragmentation of landscape.

The shape compactness of a sugarcane land block Cs is measured as:

$C_s = 4 \times \frac{\sqrt{A}}{P}$ (10.10)

where A is the area (km²) and P is the perimeter (km) of a sugarcane land block (Bogaert et al. 2000). When Cs equals 1, the sugarcane land block is a square. A more compact sugarcane land block has a higher Cs and is easier to manage and maintain. The fragmentation of landscape Fg is calculated as:

$F_g = 2 \times \frac{\log A_s}{\log P_s}$ (10.11)

where As is the total area of sugarcane land and Ps is the total perimeter of sugarcane land in the study area (Milne 1988). The higher the Fg, the less fragmented the landscape. Both Cs and Fg can be calculated in GIS.

+   2 Prepare constraint data layers.

Each land use constraint is represented as a map data layer in the GIS. The constraint maps are created by eliminating regions