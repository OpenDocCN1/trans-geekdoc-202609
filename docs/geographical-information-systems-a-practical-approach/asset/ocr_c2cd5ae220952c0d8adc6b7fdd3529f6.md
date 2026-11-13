scope. Therefore, this chapter examines the fundamental GIS operations as building blocks of spatial analysis, introduces network analysis and discusses spatial interpolation. Chapter 6 is devoted to spatial statistics, while Chapter 9 introduces some spatial modelling and decision analysis techniques. Surface analysis is included in Chapter 8. All discussions are focused on the basic concepts and uses of these tools, rather than the theoretical issues in spatial analysis, the algorithms behind the tools and their implementations in GIS. For such information, readers may refer to Berry (1993), Fotheringham and Rogerson (1994), Fischer and Leung (2001) and De Smith et al. (2013).

# ## 5.2 Spatial Query and Reclassification

# ### 5.2.1 Spatial Query

**Spatial query** is sometimes called spatial selection. There are basically two types of spatial query: query by attribute and query by location. As current GIS systems query vector and raster data in different ways and have no ability to query raster data by location (that is, based on spatial constraints), this section discusses spatial query on vector data only. Raster data query is mainly implemented through map algebra, to be discussed in Section 5.4.

# ### 5.2.1.1 Query by Attribute

**Query by attribute** is used to retrieve all features with particular attribute values from one data layer or feature class in a spatial database and display their locations

in a map. For example, consider the following query: ‘Retrieve all water mains installed before 2010 with a diameter less than 30 cm.’Here, water mains are features represented in a data layer, and installation year and diameter are two attributes. After the query is implemented in a GIS, all the water mains with the specified attribute values are selected and displayed in a map.

However, when making a query by attribute in GIS, the user is generally required to first build a query using a specific database query language, then submit the query expression for implementation. Different GIS systems may use different query languages. ArcGIS supports standard SQL. For the preceding query example, suppose the water main data layer is named w_mains, and installation years and diameters (in cm) are stored in two fields in its associated attribute table, named _year_ and _diameter_, respectively. Both fields are of numeric type. In SQL, the query can be expressed as

```
SELECT * FROM w_mains
WHERE "year" < 2010 AND
"diameter" < 30
```

Here, * represents all the features meeting the criteria or condition expressed in the WHERE clause. < and AND are operators. In the general form, an SQL expression for query by attribute can be written as:

```
SELECT * FROM <Layer or
dataset>
WHERE <Field name>
<Operator> <Value>
<Connector> <Field name>
<Operator> <Value> . . .
```