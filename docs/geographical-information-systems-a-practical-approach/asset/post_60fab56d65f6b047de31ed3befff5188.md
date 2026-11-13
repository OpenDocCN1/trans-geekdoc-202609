
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_235_0.png)

Figure 4.37 System architecture of online mapping.

as images by the server), a WFS service returns discrete geographical features. The WFS standard specifies discovery, query, locking and transaction operations as well as operations to manage stored, parameterised query expressions for creating, modifying and exchanging feature data on the internet (OGC 2010). These operations allow geographical features or their attribute values to be retrieved from the underlying database based upon the spatial constraints and query criteria defined by a client. WFS services deliver map data in the standard XML (Extensible Markup Language) format. Data from some WFS services can also be downloaded as CSV (comma-separated values), Shapefile, KML and JSON (JavaScript Object Notation) files. A WFS service is mainly a feature access service, but it can also be a feature-type service, a coordinate conversion/transformation service and geographical format conversion service. The WCS is a specification for serving raster and LiDAR datasets, referred to as coverages, over the web (OGC 2018). A coverage in WCS can be a multidimensional dataset representing spatially and temporally variable phenomena. This may include regular and irregular grids, point clouds and satellite imagery. Unlike WMS, a WCS service returns a coverage with its original properties intact, which can be interpreted, processed and extrapolated rather than just being simply viewed. It also allows the end user to directly download raster data in GeoTIFF or other image formats.

WMS, WFS and WCS services operate using different forms of HTTP requests. A map server is accessed by a client application that sends requests including specific operations supported by these protocols in the form of HTTP URL strings. The URL sets the parameters to be returned, such as what portion of the Earth is to be mapped, and the dimensions of the output GeoTIFF image. A spatial database or file server stores spatial data, which can be accessed and utilised by the map server to draw maps or dynamically generate HTML, XML or GML (Geography Markup Language) (OGC 2007) files that can be used by a client to display maps. The client can be a web browser, a mobile app or a desktop GIS.

### 4.6.2 Elements of an Online Map

Online maps are characterised by interactivity, taking advantage of the interactive, interconnected, real-time and dynamic nature of the web environment. Therefore, in addition to the cartographic elements of traditional maps described in Section 4.1.1, online maps often include navigation tools (such as zoom, pan, place finders and bookmarks) and interactive elements. Figure 4.38 shows the major elements of online maps using the online Australia’s Hydrogen Opportunities Tool as an example (https://portal.ga.gov.au/persona/hydrogen).

Generally, the map body of online maps is composed of base maps (or base layers) and thematical layers. The most common base maps for online mapping are vector road maps and remotely sensed imagery. For example, the base map shown in Figure 4.38 is the world imagery from the ArcGIS World Imagery service (https://services.arcgis.com/ArcGIS/rest/services/World_Imagery/MapServer). Although a base map may consist of many layers (such as roads, lakes, buildings and so on), these are often fused together into a rasterised set of tiled map images or map tiles and treated as a single layer in an online map. The concept of map tiles is similar to that of subsampled layers in a raster pyramid discussed in Section 2.4.3. That is, a base map is broken up at each zoom level into a set of map tiles, which are arranged in an ordered grid. When a base map scrolls to a new location, or to a new zoom level, the mapping application determines which tiles are needed and translates that into a set of tiles to retrieve and display. These map tiles may consist of thousands or millions of predrawn images that are saved on the server and transferred to browsers as users pan around the map. In recent years, some applications use the base map sent by the server as chunks of vector coordinates, sometimes known as vector tiles. Many online maps contain a base map gallery that allows users to switch between maps like imagery and topography. For example, the online maps in Figure 4.38 have a base map gallery of nine base layers for users to choose.

Thematic layers are the focus of online maps. They are constructed using data layers from the server(s) and may contain features added directly to the map from a client by local users. Many online maps organise the thematic layers into groups, which may be brought in as one or more separate web services. Users can toggle on and off these layers in a browser. When selected to display on an online map, the thematical layers are the main layers of interest. For example, Figure 4.38 shows an

### AusH2 - Australia's Hydrogen Opportunities Tool

- Interactive elements and navigation tools
- Base map gallery
- Thematic layer groups
- Layer search tool
- Hydrogen layer group
- Active thematic layer
- Legend
- Navigation tools
- Zoom level slider bar
- Return to initial zoom state
- Scale
- Base map – World Imagery
- Inset

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_237_0.png)

### Figure 4.38 Elements of online maps.

online map of hydrogen projects in Australia in which ‘Hydrogen Projects’ from the Hydrogen layer group is the thematic layer selected to display on top of the base map. This map features Australian hydrogen projects that are actively in the investigation, construction, operating or completed phase and provides a snapshot of hydrogen activity across Australia. Like base maps, thematic layers are sometimes displayed with predrawn tiles stored on servers if they do not show real-time data.

Interactive elements are an important feature of online maps. These include all interactive gadgets (which are mostly HTML and JavaScript applications that can be embedded in web pages and online maps), such as measure tools, pop-up attribute tables that appear when a user clicks a feature, slider bars that allow users to adjust the time slice of data, buttons, pull-down menus, mouseover events and hotspots that invoke action to access other tools and information, query tools to ask the server for specific data and so on. They offer the ability to link external and dynamic content with online maps or map features, incorporated with text, charts, graphs and images for a seamless user experience. For example, in the online Australia’s Hydrogen Opportunities Tool shown in Figure 4.38, when you click a point symbol representing a hydrogen project, a pop-up window appears, presenting a table of detailed information about the hydrogen activity at that location, which includes its location, operator/organisation details, current status, energy source, production method and links to external websites that provide further information about the project. On the toolbars above the map, the Layers button allows users to show and hide the layers selection window;

Data & Publications allows users to search for and download related reports and other publications; the Tools button provides access to a suite of analytic tools for hydrogen potential assessments and the Map Narrator button is used to capture and share a series of interactive scenes. There are also interactive functions for users to share a URL with current map extent and selected layers, save their map and layer state and select from multiple personas, which contain tools and data layers relevant to their interest. Effective online maps should include the interactive elements that are most useful to the targeted audience and specifically designed for their purpose.

### 4.6.3 Design of an Online Map

The basic principles for map design discussed in Section 4.2 should also be applied to the design of online maps. However, online map design needs to consider the limitations and opportunities offered by on-screen maps as well as the special characteristics of the web. An effective online map design should fulfil its intended function by conveying its particular message whilst simultaneously engaging the user. Several factors, such as consistency, usability, simplicity and functionality, contribute to good online map design. Successful online maps have to be specially designed for their purposes and intended user groups. The design of online maps covers at least four aspects: website layout, interactive elements, layers and symbology.

### 4.6.3.1 Layout Design

An online map is an interactive display of spatial data in the form of a web page. A
