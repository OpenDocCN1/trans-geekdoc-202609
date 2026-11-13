
## CHAPTER 3
## Spatial Data Input and Manipulation

This chapter introduces the major means of spatial data capture and input, outlines the principles and methods of spatial data transfer, presents the methods and techniques for spatial data editing and transformation and discusses the issues of spatial data quality and the concept of metadata.

- understand the concepts of spatial data quality and
- describe potential errors in spatial data.

## Learning Objectives

After studying this chapter, you should be able to

- understand different spatial data capture techniques;
- describe the principles and methods of spatial data transfer;
- recognise different spatial data formats, and apply appropriate mechanisms for spatial data transfer;
- grasp basic skills for spatial data editing and manipulation;

### 3.1 Spatial Data Capture

GIS projects are as varied as the places which they are designed to investigate. We may want to trace pollution in a stream, plan a wildlife reserve or identify land use conflicts, for example. Whatever the case may be, we need to study information about a geographical location to gain a better understanding of that area’s environment. The key to the success of such projects depends on having the necessary spatial data. The data needed for a project (such as vegetation, soils and species locations) often do not exist, or they are only available on paper and we need to create a digital version. We may have digital data, but they are not spatially enabled or they are not structured in the data model we need. Spatial data for use in GIS may come from different sources and can be collected through data capture or data transfer. **Spatial data capture** is the process of generating new digital spatial data. It involves direct measurement or analogue-to-digital conversion. **Spatial data transfer** is the process of converting or translating existing digital spatial data and importing them into a GIS. This section focuses on spatial data capture, and Section 3.2 will discuss spatial data transfer.

the coordinates of point features from maps or other source documents, typing the coordinates into a file in a tabular format and reading the file into the GIS. In some GIS systems, point features are also called **XY events**. This method is used where the number of point features is small.

### 3.1.1 Vector Data Capture

There are five main methods for vector data capture, depending on the source of data:

- 1. Keyboard entry
- 2. Digitising
- 3. Field surveying
- 4. Photogrammetry
- 5. LiDAR

### 3.1.1.1 Keyboard Entry

*Keyboard entry* is mainly used to input the coordinates of a number of point features into a GIS. It involves reading or obtaining

### 3.1.1.2 Digitising

**Digitising** is the process of interpreting and converting paper maps or images (aerial photos and satellite images) to digital vector data. It involves choosing geographical features from the map or image and manually tracing the features along their boundaries or shapes one by one using a digitiser while recording the coordinates of the points selected to approximate the boundary or shape of each feature. There are two digitising methods: tablet digitising and on-screen digitising.

**Tablet digitising** uses a digitising tablet to trace points, lines and polygons on a hard-copy map or image fixed on the tablet. A digitising tablet consists of an electronic tablet and a magnetic pen or puck (Figure 3.1). A *puck* is similar to a computer mouse, but it has a number of control buttons and a window with crosshairs for pinpoint placement of a point. A magnetic pen (also called a stylus) is similar to a simple ballpoint pen

### Practical 3.1 See the Support Material

In this practical, you are going to learn how a set of point features are added from a table of coordinates to create a point feature layer in ArcGIS Pro or QGIS.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_136_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_137_0.png)

Figure 3.1 Digitising tablet.
Source: Image by the author.

but uses an electronic head. The tablet has a built-in electronic mesh that can detect movement of the puck, translate its position into digital signals and send the digital signals to the attached computer. The units of measurement on the digitising tablet are in centimetres or inches. Tablet digitising results in strings of points with (x, y) values in the digitiser's unit of measurement. These (x, y) coordinates are later to be converted to real-world coordinates based on the geo-referencing system of the map or image. This method was the most popular method of vector data capture from hard-copy maps or aerial photos in the past. It has now been gradually replaced by on-screen digitising and other more advanced methods.

**On-screen digitising** uses the computer mouse and digitising software to manually trace the features on a scanned map or image displayed on the computer screen to capture vector data. It removes the need for a digitising tablet. On-screen digitising is often called heads-up digitising because the source document is viewed with the head up on the computer screen, rather than down on the digitising tablet. The source documents may be scanned images (from paper maps and aerial photographs) or digital aerial and satellite images. Most GIS software systems support on-screen digitising. It generally follows the following steps:

- 1. Scan the source document into a digital image if a paper map or aerial photo is used.
- 2. Add the image into a GIS.
- 3. Georeference the image.
- 4. Trace features on the image using the mouse.
- 5. Edit features.
- 6. Add attribute data.

Hard-copy documents are converted into digital images with a scanner. Three types of scanners can be used: flatbed scanners, rotating drum scanners and large-format feed scanners. Flat-bed scanners are generally small and less accurate, mainly used for small-format maps and aerial photos. Rotating drum and large-format feed scanners are more accurate and are used for large-format maps and aerial photos. Scanners may output digital images in different resolutions. For on-screen digitising, a resolution of 300 dpi (dots per inch) is mostly sufficient. Scanned maps do not normally contain georeference information. Therefore, after a scanned map or image is added to a GIS, it has to be georeferenced to the map projection or projected coordinate system of the source map or aerial photograph before digitising begins.

Georeferencing an image in GIS involves selecting at least three control points that can be accurately identified on the image with known real-world coordinates, using the selected control points to mathematically establish linear or nonlinear relationships between image coordinates (rows and columns) and real-world coordinates (x and y coordinates in the projected coordinate system of the source document) and transforming the image so that each location on the image can be defined in real-world coordinates. This process is completed by using the georeferencing tools available in GIS software. After the image is georeferenced, the subsequent digitising process will capture coordinate data in the projected coordinate system of the source map or aerial photograph.

On-screen digitising is performed using the digitising tools provided within GIS software. The georeferenced image is used as the backdrop map. It allows users to use drawing or sketching tools to trace (actually redraw) geographical features on the screen and digitise the features into sequences of point coordinates. There are two modes of digitising: point and stream mode. **Point mode digitising** is the most common method, using the mouse to select points as vertices of a feature on the image and clicking the mouse to record their individual locations one by one; the GIS then connects the vertices to create a digital feature. As a general rule, for a feature represented as a straight line, only two end points need to be digitised. For a feature represented as a curved line, more points need to be digitised to make sure its shape is best approximated. The number and density of points selected

### Practical 3.2 See the Support Material

In this practical, you are going to learn how to georeference an image in ArcGIS Pro or QGIS.
