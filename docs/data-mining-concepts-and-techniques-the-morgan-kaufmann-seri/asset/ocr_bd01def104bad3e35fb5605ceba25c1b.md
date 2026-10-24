![](bbox=[0.11, 0.11, 0.88, 0.51])

attendant tables (dimension tables), one for each dimension. The schema graph resembles a starburst, with the dimension tables displayed in a radial pattern around the central fact table.

**Example 3.1. Star schema.** A star schema for sales is shown in Fig. 3.7. Sales are considered along four dimensions: time, item, branch, and location. The schema contains a central fact table for sales that contains the keys to each of the four dimensions, along with two measures: dollars_sold and units_sold. To minimize the size of the fact table, dimension identifiers (e.g., time_key and item_key) are system-generated identifiers.

Notice that in the star schema, each dimension is represented by only one table, and each table contains a set of attributes. For example, the location dimension table contains the attribute set {location_key, street, city, province_or_state, country}. This constraint may introduce some redundancy. For example, “Urbana” and “Chicago” are both cities in the state of Illinois, USA. Entries for such cities in the location dimension table create redundancy among the attributes province_or_state and country, that is, (..., Urbana, IL, USA) and (..., Chicago, IL, USA).

**Snowflake schema** is a variant of star schema, where some dimension tables are normalized, thereby further splitting the data into additional tables. The resulting schema graph forms a shape similar to a snowflake.

The major difference between the snowflake schema and star schema models is that the dimension tables of the snowflake model may be kept in normalized form to reduce redundancies. Such a table is easy to maintain and saves storage space. However, this space savings is negligible in comparison to the typical magnitude of the fact table. Furthermore, the snowflake structure may reduce the effectiveness