
It should be noted that different GIS software packages may have different sets of analytical functions and tools, may use different names and different input parameters for the same type of functions and may impose different constraints on the values of inputs and outputs. In addition, a problem can be solved by different combinations of GIS functions and tools. Therefore, a solution process designed based on a problem model with the approach discussed earlier is not unique. Different people may come up with different solution processes for the same problem by selecting different sets of methods and tools. However, the selected methods and tools should be simple, effective, valid and fit for the problem and objectives.

## 1.4.5 Implementing the Solution Process and Communicating the Results

The solution process designed in the previous stage is implemented with GIS software to produce the expected outcome. The results can be presented as maps and other forms of spatial visualisation, summarised in graphs and tables and interpreted in a report in a clear, concise, accurate and comprehensible way. They will then be used by decision-makers to develop an action plan to tackle the problem, or used by researchers for further studies.

For many problems, the final stage is not the end of the process but the start of a new round of the process, whereby the problem is revisited and the entire process or parts of it are iterated. Not only is the process iterative, but at each stage one also often looks back to the previous step and re-evaluates the validity of the decision made. Therefore, in reality, the problem-solving process is more complex and iterative than this summary of steps suggests.

## 1.5 GIS Software

### 1.5.1 Categories of GIS Software

GIS software is a vital component of a GIS project. There are many different types of GIS software, ranging from desktop GIS to server/cloud GIS, mobile GIS, spatial DBMS software and GIS software libraries.

**Desktop GIS** software runs on a personal computer and is the most widely used category of GIS software. It offers complete GIS functionality in a single-user environment, adopts standard desktop user interface styles (such as Microsoft Windows) and interoperates with other desktop applications (such as Microsoft Excel). Users can interact directly with the software via a user interface to perform ad hoc GIS tasks. With desktop GIS software, all the data and software components reside in one personal computer, and all the tasks are carried out on the same computer.

As its name suggests, **server GIS** software runs on a computer server, whose functions can be accessed and used by remote networked users. It is mainly used by software developers and web developers to create web and mobile applications with well-defined tasks, such as routing, finding addresses/places, mapping, map publishing and data editing. It has also been used to build geoportals as gateways to spatial data resources. The simplest types of server GIS applications are web or internet mapping systems, which are used to serve or publish maps and/or images over the internet that can be browsed and downloaded using standard web browsers. More advanced server GIS systems allow maps and images to be integrated or mashed up with other datasets and web services. The new generation of server GIS software can provide complete GIS functionality in a multi-user environment for distributed spatial data editing, management, analysis and visualisation. It enables sharing of GIS resources among an organisation or a group of stakeholders, which can be deployed in a client-server distributed computing or cloud computing environment. GIS running on a cloud server or cloud platform is known as cloud GIS.

**Mobile GIS** software runs on a mobile platform with an internal or external GNSS, such as a tablet or a smartphone. It is mainly designed for spatial data acquisition and updating in the field, with positioning, spatial data entry, spatial data transfer, map display, feature editing, map query and simple analytical functions. Some mobile GIS software also provides links to a GIS server or a GIS cloud server, enabling field-collected data to be uploaded directly to the server and the data stored on the server to be accessed instantly and updated via the wireless network.

Spatial DBMS software is used to develop and manage large spatial databases for enterprise applications in organisations, such as in a business or government. But they generally lack spatial data editing, analysis and mapping functions. GIS **software libraries** are collections of GIS software components which implement different GIS functions, such as reading and writing spatial datasets in different data formats, performing cartographic projections (see Section 2.2), generating buffers, overlaying map data layers and producing a contour map. They are intended to be used by software developers to design and build specific GIS applications. GIS software libraries do not allow direct use of functions; they can only be embedded in application software.

Table 1.1 lists typical tasks that can be carried out with different types of GIS software and their potential usages. Here, we classify the basic GIS tasks into data capturing, editing, storage, query, exploration (viewing and exploring spatial patterns), manipulation, analysis and mapping. Data editing, storage and query are data management functions. We also list internet mapping as a category separate from server/cloud GIS, as its functionality is limited to serving maps over the internet. In some applications, different categories of GIS software are used in combination or together with other software for database management, statistical analysis and modelling.

### 1.5.2 Proprietary GIS Software

A large number of GIS software packages are commercially or freely available. A proprietary GIS software package is a commercial product licensed under the exclusive legal right of the copyright holder. The licensee is given the right to use the software under certain conditions while restricted from other uses, such as modification and further distribution. Its source code is almost always kept secret. The price of proprietary GIS software typically ranges from $500 to $1,500 for desktop software and from $5,000 to $25,000 for server products. Although it is costly, proprietary GIS software is generally packaged, robust, comprehensive, well-documented, regularly and easily updated and has reliable professional service and support. Following is a brief introduction to some popular proprietary GIS software packages.

### 1.5.2.1 ArcGIS

ArcGIS is a comprehensive suite of GIS software products developed by ESRI (www.esri.com/). It includes ArcGIS Desktop, ArcGIS Online, ArcGIS Platform, ArcGIS Enterprise and other featured products (such as ArcGIS Indoors, ArcGIS Urban and ArcGIS Business Analyst).

ArcGIS Desktop is developed exclusively for the Microsoft Windows (or simply Windows) operating system. However, the ArcGIS Desktop software has been widely adopted by a large user base since the launch of ARC/INFO in the 1980s. It is a popular choice for spatial analysis and modelling as it includes a wide range of analytical functions and provides scripting tools and application programming interfaces (APIs) for adding user-developed functions. Many extensions and add-ons to ArcGIS Desktop have been developed to incorporate specific spatial analysis and modelling capabilities.

ArcGIS Desktop has five components, including ArcMap, ArcCatalog, ArcScene,

Table 1.1 Typical tasks that can be carried out with different types of GIS software

| | Capturing | Editing | Storage | Query | Exploration | Manipulation | Analysis | Mapping | Used by |
|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---|
| Desktop GIS | x | x | x | x | x | x | x | x | Individuals for GIS analysis and mapping |
| Internet mapping | | | | x | x | | | x | Networked users for accessing and exploring data |
| Server/Cloud GIS | x | x | x | x | x | x | x | x | Networked users for accessing and using GIS functions as remote services, or software developers and web developers to create web and mobile GIS applications |
| Mobile GIS | x | x | | x | x | | | x | Individuals for field data collection |
| Spatial DBMS | x | x | x | x | | x | | | Enterprise users for managing large spatial databases |
| GIS software libraries | | | x | | | x | x | x | Software developers to design and build specific GIS applications |
