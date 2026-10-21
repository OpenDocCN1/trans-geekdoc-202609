
### FIGURE 1.5 Data representation in hashed sharding.

The following Figure 1.6 presents the shard key value for range sharding. Figure 1.7 presents document after appending shard key. Similar process is followed in both storage and retrieval operations for finding the corresponding shard. The calculated shard value is the shard key and is appended to the document based on the latitude and longitude ranges as shown in Figure 1.8. Figure 1.9 presents the shard key value for zone sharding.

![](img/5025594f89449de2a74e5b325b1e84ef_24_0.png)

### FIGURE 1.6 Range sharding: generating shard key.

```
{
  "_id" : { "$oid" : "59e1a2120d180bec4c1ac" },
  "Place" : "KeshavSchools",
  "State" : "AndhraPradesh",
  "Country" : "India",
  "Place Type" : "School",
  "Latitude" : 17.856358,
  "Longitude" : 80.648915,
  "Tag" : "South"
}
```

### FIGURE 1.7 Range sharding: appending the shard key and storing in the database.

![](img/5025594f89449de2a74e5b325b1e84ef_24_1.png)

### FIGURE 1.8 Data representation in range sharding.

16.49590337  
80.67028580  
tfc...9kb  

### FIGURE 1.9 Zone sharding: generating shard zone based on geographic region.

Figure 1.10 presents document after appending the Shard Zone. Similar process is followed in both storage and retrieval operations for finding the corresponding shard. When this shard key range is modified, data is migrated to a new zone automatically.

The calculated geohash value is the shard key and is appended to the document based on the zone of input location along with the zone value, as shown in Figure 1.11.

LTRMP (Long Term Resource Monitoring Program Component) Spatial Data Query and Visualization Tool is developed Olsen [8]. It facilitates the display and querying of Upper Mississippi River Basin (UMRB) data sets. It requires an understanding of geographic information system (GIS) concepts and LTRMP component database structure. Data processing and visualization tools are reported in [9].

Refinement tools such as DataWrangler and Google Refine; conversion tools such as Mr. Data Convertor; statistical analysis tools such as R project for statistical computing; generic visualization applications such as Google fusion tables, Tableau, Many Eyes, CartoDB, and GeoCommons; wizards such as Google Chart Tools; JavaScript InfoVis Toolkit, D3.js, Protovis, and Recline.js; geospatial visualization tools such as OpenHeatMap, OpenLayers, and OpenStreetMap; temporal data visualization tools such as TimeFlow; tools for network analysis such as Gephi, NodeXL are discussed. In the category of web applications, Google Fusion tables, CartoDB, Google Chart Tools, Recline.js, and OpenLayers are widely used.

```
{ "_id" : { "$oid" : "5a7b2ba53767b0b96e54db709" }, "Place" : "Bobit School",
"State" : "Andhra Pradesh", "Country" : "India", "Place Type" : "School",
"Latitude" : 16.49590337 , "Longitude" : 80.67028580 , "HashKey" : "tfc...",
"Zone" : "SouthZone" }
```

### FIGURE 1.10 Zone sharding: appending the shard zone.

![](img/5025594f89449de2a74e5b325b1e84ef_25_0.png)

### FIGURE 1.11 Data representation in zone sharding and storing in the database.

Our previous work [16,18] is on geospatial querying by integrating Cassandra with Hadoop. Geospatial querying within Hadoop environment faced significant data movement because of no proper scheduling mechanism for job execution. We extended the same framework for integrating MongoDB with Spark with visualization. The main objective of this chapter is to propose “GeoMongoSpark Architecture” for efficient processing of spatial queries in a distributed environment that takes advantage of integrating MongoDB with Spark for geospatial querying by using geospatial indexing and sharding techniques and visualizing the geospatial query processing. The main objectives are listed as follows:

- 1. To understand the need for integrating MongoDB and Spark and propose a new architecture for the integration.
- 2. Collect benchmark datasets for testing the proposed architecture.
- 3. Apply various sharding techniques to partition the data.
- 4. Compare the performance evaluation of various sharding techniques.
- 5. Use Tableau for visualization.

## 1.2 LITERATURE SURVEY

Query processing in a centralized database system has more response time and slower data access when compared with a decentralized database. Location-based services use voluminous spatial data to answer end user queries. Hence, scalable techniques that operate on distributed computing platforms and technologies are required for efficient processing of spatial queries. Spatial data processing based on Hadoop, and Spark comparison based on query language, spatial partitioning, indexing, and data analysis operators are reported in [5]. The STARK system provides a number of spatial predicates for filters and joins. The drawback with this framework is that filters can delay the processing time, irrespective of any kind of data, and persistent indexing causes memory wastage. The processing performance can be improved with the use of hashed indexing that uses less memory. The work reported in [6] presents a distributed query scheduler for spatial query processing and optimization. It generates query execution plans using spatial indexing techniques. Experiments are performed on real datasets and are compared with other works. Although the query execution performance is improved and communication cost is reduced, this architecture is costly to implement, and the use of filters can increase the processing time of a query. Spatial-Hadoop and GeoSpark are discussed in [7], where authors proved that GeoSpark is faster than Spatial-Hadoop for geospatial big data analytics. Spatial data processing system that schedules and executes range search is described in [10]. k-NN (k nearest neighbor), spatiotemporal operation, spatial-join, and k-NN-join queries are described. Bloom filters are used to reduce network communication. Experiments are carried out using sample data. Hashed indexing can improve the query processing time by reducing the use of memory for storing global and local indexing, even though frequently accessed data is cached in Location Spark and less frequently used data is stored into disk. The usage of filters on the spatial data increases the implementation cost of this architecture. Authors in [11] described Panda architecture for spatial predictive queries, such as predictive range, k-NN, and aggregate queries. Panda System will display a system behavior statistics on the interface. Usage of grid and list data structures to store the data may cause memory wastage. Also, processing the grid data structures requires more amount of time. The identification of object movement is very important in system, and variations may lead to major differences. Distributed profitable-area query (DISPAQ) is described in [12]. It identifies profitable areas from raw taxi trip data using PQ-index. Z-skyline algorithm prunes multiple blocks during query processing. But usage of predictive function increases the computation overhead, though it reduces the processing time for executing frequent queries. Performance can be improved by dividing the places into zones. Data mining is used to increase marketing of an educational organization in [13]. Authors used k-means algorithm to cluster the locations. Student residential address is calculated using latitude and longitude and visualized minimum, maximum, and average distance. Such visualization helps to improve the admission rate. Haversine formula is used to calculate the distance between the two locations. Their application can be used for 1,000–2,000 students. Authors of [14] used open shape-based strategy (OSS) to eliminate the computation related to the world boundary. It also reduces I/O (Input-Output) and CPU (Central Processing Unit) costs when compared with range query strategies (RQS) and is scalable than RQS for large datasets. However, OSS is more expensive than the filter operations in RQS. Direction of object plays an important role in the evaluation of queries. Surrounding join query, that retrieves, for each point in Q, all its surrounding points in P, is described in [15]. Even though the surrounding join query enriches the semantics of the conventional distance-based spatial join query, creating a VD (Visitor Database) requires a lot of processing time. Also, the pruning of unnecessary nodes in hierarchical algorithm requires more time, which can be avoided by starting only with necessary nodes.

To summarize, the main drawback of the existing system is time complexity for processing large datasets. Our work mainly focuses on reducing the query response time by using hashed indexing and zones. Also, existing system has high time complexity for processing large geospatial datasets and usage of intermediate data. The usage of complex data structures to hold data leads to large processing times and requires complex infrastructures to handle. Visualization alone cannot help to perform analytics on the data that is handled by the system. Visualizing can be made fast and efficient using Tableau, as it handles different types of data and supports business analytics operations for generating automatic reports. Sharding techniques can be treated as an alternative to partitioning techniques, as such Range Sharding and Zone Sharding are used in our framework. We also made an attempt to determine which sharding performs well for geospatial query processing.

## 1.3 PROPOSED SYSTEM

This section presents a detailed architecture of GeoMongoSpark along with algorithms. Figure 1.12 presents the proposed GeoMongoSpark Architecture to perform geospatial querying, aiming at optimized query response time for spatial data analysis.

Figure 1.13 presents a detailed flow chart of the sequence of steps for the Visualization of Geospatial Data. Initially, data is stored by passing the data to Zone Sharding and Range Sharding. The output of a geospatial can be converted to JSON format and can be given as input to a Tableau for visualization.
