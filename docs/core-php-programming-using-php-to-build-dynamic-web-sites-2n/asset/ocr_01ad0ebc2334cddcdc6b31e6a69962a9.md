# Pie Charts

Pie charts are a good way to see how a value represents a percentage of a whole. Each data point is aa slice of a pie with a unique color. A legend associates the colors with each data point's label and value.

Since the pie chart is round, it represents a much more complex problem. PHP's image functions allow you to draw an arc or a triangle, but not a pie slice. The solution is to draw the arc at the end of the slice, then two lines that connect the center of the circle to the ends of the arc. These elements are drawn in the color of the slice and the imagefilltoborder function is used to fill the shape.

The arc itself is easy to draw, since the imagearc function will draw an arc based on starting and stepping degrees. To find the coordinates of the ends of the arc requires some trigonometry. I've added a function to the script for finding the coordinates of a point on a circle of a certain degree and diameter. The return values are for a circle centered on (0,0), so an offset must be added to them to get the coordinates in the graph.

When each of the slices is drawn, a black border is added to the circle and a small box is drawn for each color used. The data point's label and value are drawn next to the colored box.

As with the bar graph above, the data used in the chart come from an array hard-coded into the script in Listing 19.4. It is possible to keep the chart up to date by editing every time the data change, but it may be better to link it with a database.

**Listing 19.4** Creating a Pie Chart