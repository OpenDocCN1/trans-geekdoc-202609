Graphical Excellence

2. The mean is not a robust measure of central tendency. For datasets containing large outliers, the mean will be highly influenced by these values and will fail to represent the center of the data. As an alternative, the median should be used in place of the mean when the data is at risk of containing outliers. Examples include financial transactions in real estate, where the sale of an outlier home can distort the overall pricing of a neighborhood.

# 11.4 Graphical Excellence

In the earlier sections, we used Python modules to produce graphs that seemed helpful in exploring variables. Let's spend some time on what makes for good graphs, and what should be avoided. Many of the points in this section can be found in the excellent book [35]. Graphics introduce overhead, as they may include elements such as curves, a coordinate system, and labels which must be understood by the viewer. For small datasets, a graph may not even be necessary; it be preferable to show the values in a table.

When we decide to produce a graph, it is essential to tell the truth about the data. It may sound obvious, but there are many ways to lie about data, both wittingly and unwittingly. In the first category, visual effects might be intentionally used to mislead a viewer. In the second category, we might use technology that confuses the viewer. In either case, the graphics creator is responsible for accurate, clear, reporting of the data. This means applying the appropriate ethics and skill. If a certain package cannot produce the correct graph, then another or method should be used.

Next, we will look at several examples of plotting data to understand what can go wrong, and how to improve the depiction of data. Pie charts are very popular for displaying data, particularly in the financial community where they display the wealth invested in different assets like stocks and bonds (the breakdown is called an asset allocation). Figure 11.1 shows an example of an asset allocation. If you can guess the data.

You might reason that the larger wedge is greater than 50% and less than 75%, and you would be right. It might be hard, however, to arrive at the correct answer: the larger wedge is 65%, while the smaller wedge is 35%. Why make the viewer work so hard and risk arriving at the incorrect answer? The chart could be labeled for greater clarity, but with this little data, it would be better to make a table:

| 65% |
| Bonds | 35% |