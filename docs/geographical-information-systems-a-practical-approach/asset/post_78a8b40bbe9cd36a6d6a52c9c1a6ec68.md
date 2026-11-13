

- (darker colours represent a higher likelihood of the farm being used in the enterprise at the end of the model runs).
- 9.10 Procedure of WofE modelling with GIS.
- 9.11 An artificial neuron.
- 9.12 An ANN with one hidden layer.
- 9.13 (a) RBFNN and (b) RBFLN.
- 9.14 Landslide susceptibility map of the Langat River Basin.
- 10.1 A GIS procedure for runoff modelling.
- 10.2 Measured and SWAT-simulated NO3-N concentration at the outlet of the Banha catchment in 2000 and 2001.
- 10.3 Measured and SWAT-simulated water-soluble P concentration at the outlet of the Banha catchment in 2000 and 2001.
- 10.4 GIS analysis in Stage 1 of wind farm site selection.
- 10.5 GIS analysis in Stages 2 and 3 of wind farm site selection.
- 10.6 The Herbert River catchment.
- 10.7 Sugarcane land allocation scenarios: (a) scenario 1, (b) scenario 2 and (c) scenario 3
- 10.8 GIS analysis in land evaluation of tea plantation in Laos.
- 10.9 A moving window approach to air pollution modelling.
- 10.10 A time sequence plot for winter rainfall and the fitted linear trend model.
- 10.11 Analysis process of measuring landscape characteristics and their relationships with bird diversity at different scales in Ohio, USA.
- 10.12 Analysis process of characterisation of population dynamics of western corn rootworm in South Dakota, USA.
- 10.13 Toothed lionema (like a dense shrub or small tree).
- 10.14 The study area of habitat potential mapping in the Strzelecki Ranges, Victoria.
- 10.15 The solution process for predicting the potential spatial distribution of toothed lionema.
- 10.16 The potential spatial distribution of toothed lionema.
- 10.17 A value transfer method for estimating economic values of ecosystem services.
- 10.18 Distribution of survey point data in the case study of the Murray River region.
- 10.19 Kernel surface for density mapping.
- 10.20 Density map of aesthetic value in the Murray River region.
- 10.21 Hotspot map of aesthetic value in the Murray River region.
- 10.22 Hotspot map of multiple landscape values in the Murray River region.

## Tables

| Table | Title | Page |
|-------|-------|------|
| 1.1 | Typical tasks that can be carried out with different types of GIS software | 40 |
| 2.1 | Major Earth spheroids | 63 |
| 2.2 | Recommended map projections for small- and medium-scale mapping | 71 |
| 2.3 | Result table for the join operation with SQL on the two relations in Figure 2.29 | 95 |
| 3.1 | Major digital spatial data formats | 124 |
| 3.2 | Examples of geodatabase topology rules for polygons, lines and points | 144 |
| 3.3 | An error matrix for a land cover layer | 150 |
| 3.4 | Kappa scale of relative strength of agreement | 151 |
| 4.1 | An attribute table of soil properties | 191 |
| 5.1 | Seven broad categories of spatial analysis and modelling tools | 222 |
| 5.2 | Major SQL operators for query | 224 |
| 5.3 | Example SQL functions for query | 225 |
| 5.4 | Spatial operators for query in ArcGIS | 226 |
| 5.5 | Mathematical operators and functions in map algebra | 249 |
| 5.6 | Forest stand characteristics | 271 |
| 7.1 | Characteristics of AVHRR | 343 |
| 7.2 | Characteristics of TM and ETM+ | 344 |
| 7.3 | Characteristics of OLI and TIRS | 345 |
| 7.4 | Covariance matrix of the 6-band ETM+ image of Woori Yallock | 371 |
| 7.5 | Eigenvectors and eigenvalues calculated from the covariance matrix in Table 7.4 | 372 |
| 9.1 | Performance matrix | 443 |
| 9.2 | The pair-wise comparison scale | 447 |
| 9.3 | Pair-wise comparison matrix | 448 |
| 9.4 | Python script for the CA forest fire model in Box 9.1 | 455 |
| 9.5 | 2 × 2 contingency table for conditional independence test | 470 |
| 10.1 | Land suitability classes | 501 |
| 10.2 | Land suitability classification criteria for tea cultivation | 502 |
| 10.3 | Annual total ecosystem service values (in US$) by land cover and ecosystem service type for Maury Island | 526 |
| 10.4 | Types of landscape values | 528 |

## Preface

Geographical information systems (GIS) are effective tools for scientific investigations, environmental reporting, resource management and development planning. Like the first edition, GIS for Environmental Applications: A Practical Approach, this book provides detailed and comprehensive coverage of GIS principles and techniques and offers a practical guide to the implementation of these principles and techniques in research, management and planning through a large number of carefully chosen examples, practicals and case studies to help readers get a real grasp of knowledge and skills. In order to extend the reach of the book, the title of the second edition is changed to Geographical Information Systems: A Practical Approach because the concepts, principles, methods, techniques and practical skills introduced in the book are not limited to environmental applications. Maintaining a practical perspective, the second edition continues to bring up-to-date GIS knowledge, tools and practices into one cohesive, comprehensive, concise and self-contained book which is accessible to students, scientists and practitioners in environmental science, earth science, geography, archeology and other scientific studies that are concerned with the location, distribution and relationship of geographical phenomena.

### Changes from the First Edition

Since the first edition was published, there have been several important developments in GIS. These include:

- New sources of spatial data. New generation of Earth observation sensors, such as hyperspectral imagers and LiDAR (light detection and ranging), and new remote sensing platforms, including UAS (unmanned aircraft systems) and nano/micro-satellite constellations have been employed for spatial data collection for an ever-expanding list of environmental and socio-economic applications.
- Big data and data analytics. We are now living in the age of big data. In addition to a massive amount of remotely sensed data produced from Earth observation remote sensing systems, which come with a wide variety of spatial, temporal and spectral resolutions on a daily basis, real-time data feeds from the internet of things (IoT), such as air quality measurements, wildfire perimeters, temperature and humidity readings, result in high volumes of collected spatial information. Exploiting the potential of large collections of spatial data from various sources leads to new methods, including machine learning and artificial intelligence, incorporated into GIS for analysis and visualisation.

- 3D analysis. 3D analysis has been a growing trend in GIS because it is a better representation of the real world. It is not just for its powerful visualisations but adds a third dimension to analysis. For example, 3D analysis tools in GIS can be used to perform overlay and proximity analysis in 3D based on the geometry of the features, evaluate the amount of shadow and impact of the proposed building in an urban setting and estimate unknown values based on sample data through 3D interpolation. The third dimension may represent an area’s population density, concentrations of chemicals and minerals throughout a region, the land suitability for a particular type of land use and the depth of an aquifer. Analysing data over time adds the ability to do 4D analysis.

- Web GIS and cloud GIS. Web GIS makes spatial data and GIS services accessible through web browsers and allows users to create, share and interact with maps and other spatial data on the internet. It has evolved from simple online mapping to interactive online GIS applications serving a variety of purposes. On the other hand, cloud GIS uses cloud computing services for spatial data management, storage and analysis, offering a centralised and effective platform for GIS work. Cloud GIS can now leverage big data infrastructure through the cloud that can handle large information volumes and run faster analysis, which allows users to do far more than they ever could before.

- Open-source GIS software. Open-source GIS software systems are now comparable to proprietary GIS software systems in many regards and exceed them in several specific capabilities, such as true 3D visualisation and analysis. For many applications, open-source GIS software has become an alternative to proprietary GIS software.

As a comprehensive textbook that provides a hands-on understanding of GIS and the best practice of the use of GIS, the new edition has been expanded and updated to reflect some of these developments. A few new topics have been introduced. These include new advances in GIS (in Section 1.2), voxel models (in Section 4.4), online mapping (in Section 4.6), space-time analysis (in Section 6.7), object-based image classification (in Section 7.5) and neural network image classification (in Section 7.5). The chapters are organised as in the first edition, except that the chapter on spatial visualisation has been brought forward, which is now Chapter 4. Learning how to visualise spatial data on a map earlier enables learners to present spatial data in a form that can be easily understood and interpreted, and to visually convey the results of GIS analyses with competence when they study spatial analysis and more advanced concepts in later chapters. Indeed, understanding and making maps are most fundamental, as the inputs and outputs of GIS analyses are largely represented in maps. In each chapter, the content has been revised, additional content has been added,

