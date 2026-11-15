![](bbox=[0.21, 0.1, 0.76, 0.35])

FIG. 3.7 A graph showing nonstop flight connections between cities.

Now let’s see how well you performed. There is only one entity type: City (.Name). There is also only one fact type: City has a flight to City. For instance, the arrow from Chicago to Seattle may be verbalized as: City “Chicago” has a flight to City “Seattle”. The “to” in the predicate is important because it conveys direction and avoids the symmetry problem with the earlier marriage example.

If this was an as-is model, and we wanted also to talk about the flight connections (e.g., state their duration) or to include many airlines, we should add flight numbers to the arrows on the graph. This to-be model leads to a different verbalization, which you might like to try for yourself. A later exercise returns to this example.

In practice, it is usually possible for a city to have more than one airport, so that connections apply directly between airports rather than cities. Airports are identified by airport codes (e.g., “JFK” and “LGA”, respectively, denote John F. Kennedy and LaGuardia airports that service New York).

Airports can service a city without being located in that city. For example, Newark airport (EWR) located in New Jersey also services New York, and Sea-Tac airport (SEA) located between Seattle and Tacoma services Seattle. We need to determine which specific kinds of facts are of interest in the business domain and verbalize them precisely (e.g., Airport services City is a different fact type from Airport is located in City).

By now, you may have some sense of the power of verbalizing examples in terms of elementary facts. No matter what kind of example you start with, if you or an assistant understands the example then you should be able to express the information in simple facts. This does require practice at the technique, but this is fun anyway, isn’t it? If you can’t do step 1, there is little point in proceeding with the design—either you don’t understand the UoD or you can’t communicate it clearly.