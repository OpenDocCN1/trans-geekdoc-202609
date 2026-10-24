+   c. If each dimension has five levels (including all), such as “student < major < status < university < all,” how many cuboids will this cube contain (including the base and apex cuboids)?

3.6. Suppose that a data warehouse consists of the four dimensions date, spectator, location, and game, and the two measures count and charge, where charge is the fare that a spectator pays when watching a game on a given date. Spectators may be students, adults, or seniors, with each category having its own charge rate.

+   a. Draw a star schema diagram for the data warehouse.

+   b. Starting with the base cuboid [date, spectator, location, game], what specific OLAP operations should you perform in order to list the total charge paid by student spectators at GM_Place in 2010?

+   c. Bitmap indexing is useful in data warehousing. Taking this cube as an example, briefly discuss advantages and problems of using a bitmap index structure.

3.7. A data warehouse can be modeled by either a star schema or a snowflake schema. Briefly describe the similarities and the differences of the two models, and then analyze their advantages and disadvantages with regard to one another. Give your opinion of which might be more empirically useful and state the reasons behind your answer.

3.8. Design a data warehouse for a regional weather bureau. The weather bureau has about 1000 probes, which are scattered throughout various land and ocean locations in the region to collect basic weather data, including air pressure, temperature, and precipitation at each hour. All data are sent to the central station, which has collected such data for more than 10 years. Your design should facilitate efficient querying and online analytical processing and derive general weather patterns in multidimensional space.

3.9. A popular data warehouse implementation is to construct a multidimensional database, known as a data cube. Unfortunately, this may often generate a huge, yet very sparse, multidimensional matrix.

+   a. Present an example illustrating such a huge and sparse data cube.

+   b. Design an implementation method that can elegantly overcome this sparse matrix problem. Note that you need to explain your data structures in detail and discuss the space needed, as well as how to retrieve data from your structures.

+   c. Modify your design in (b) to handle incremental data updates. Give the reasoning behind your new design.

3.10. Regarding the computation of measures in a data cube:

+   a. Enumerate three categories of measures, based on the kind of aggregate functions used in computing a data cube.

+   b. For a data cube with the three dimensions time, location, and item, which category does the function variance belong to? Describe how to compute it if the cube is partitioned into many chunks. Hint: The formula for computing variance is 1/N sum_{i=1}^{N} (x_i - x_i_bar)^2, where x_i_bar is the average of x_i s.

+   c. Suppose the function is “top 10 sales.” Discuss how to efficiently compute this measure in a data cube.

3.11. Suppose a company wants to design a data warehouse to facilitate the analysis of moving vehicles in an online analytical processing manner. The company registers huge amounts of auto