involves deeper analysis of the data, typically using sophisticated statistical techniques and complex algorithms for detecting patterns. Nowadays, many tools for OLAP and data mining are in use. Either topic deserves a book in itself. The remainder of this section provides a brief overview of OLAP.

There are three main approaches to OLAP. Each uses base data as well as aggregated data (e.g., sales figures might be summed and grouped at various levels). Multidimensional OLAP (MOLAP) stores both base and aggregated data in multidimensional structures rather than tables. Relational OLAP (ROLAP) stores both base and aggregated data in relational tables. Hybrid OLAP (HOLAP) stores base data in relational tables and aggregated data in multidimensional structures. Some DBMSs, such as Microsoft SQL Server, support all three kinds of OLAP.

The multidimensional structures used for OLAP are popularly known as cubes. In geometry, a cube is a three-dimensional box structure. In OLAP theory, a cube can have as many dimensions as you like. Cubes provide an intuitive way to visualize and browse data as well as fast access to aggregate data. Let's consider a simple example.

With reference to the star schema in Fig. 18.3, suppose we wanted to list the number of units sold in the years 2020 through 2022 for each geographic region and each item category. As an exercise, you might like to formulate the SQL query for this. You need to perform the natural join of the four tables; group by saleYear, region, and category; and compute sum(qty). An extract of the possible result is shown in Table 18.1, assuming only two categories (SW = Software, HW = Hardware) and four regions (N = North, S = South, E = East, W = West). The fact type underlying this table is the quaternary Year in Region had sales of items of Category in NrUnits. The full table display of the result would include 24 rows (eight for each year); only the first nine rows are shown here.

| Year | Region | Category | NrUnits |
|---|---|---|---|
| 2020 | N | SW | 10000 |
| 2020 | N | HW | 500 |
| 2020 | S | SW | 12000 |
| 2020 | S | HW | 330 |
| 2020 | E | SW | 7500 |
| 2020 | E | HW | 440 |
| 2020 | W | SW | 12000 |
| 2020 | W | HW | ...350 |
| 2021 | N | SW | 14500 |
| ... | ... | ... | ... |

An alternative way of displaying the data using a cube is shown in Fig. 18.4. Here, the independent variables (year, region, and category) appear as the dimensions making up the edges of the cube, and the values for the dependent variable or measure (units sold) appear in the relevant cells. Only the software sales figures are shown here in the 12 cells making up the front half of the cube. You can imagine seeing the hardware sales figures by rotating the cube to see its other side.