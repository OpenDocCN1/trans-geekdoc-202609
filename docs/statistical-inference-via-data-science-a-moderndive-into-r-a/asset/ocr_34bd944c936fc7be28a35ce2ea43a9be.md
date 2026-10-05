# 38

# 2 Data Visualization

because of the high degree of overplotting in the points, it's hard to get a sense of exactly how many values are between, say, 10 mph and 15 mph.

What is commonly produced instead of Figure 2.8 is known as a histogram. A histogram is a plot that visualizes the distribution of a numerical values as:

+   We first cut the x-axis into a series of bins, where each bin represents a range of values.

+   For each bin, we count the number of observations that fall in the range corresponding to that bin.

+   For each bin, we draw a bar whose height marks the corresponding count.

Let's drill-down on an example of a histogram, shown in Figure 2.9.

![](bbox=[0.114, 0.345, 0.886, 0.498])

FIGURE 2.9: Example histogram.

Let's focus only on wind speeds between 10 mph and 25 mph for now. Observe that there are three bins of bins of equal width between 10 mph and 25 mph. Thus we have three bins of width 5 mph each: one bin for the 10-15 mph range, another bin for the 15-20 mph range, and another bin for the 20-25 mph range. Since:

+   The bin for the 10-15 mph range has a height of around 8000. In other words, around 8000 of the hourly wind speed recordings are between 10 mph and 15 mph.

+   The bin for the 15-20 mph range has a height of around 2400. In other words, around 2400 of the hourly wind speed records are between 15 mph and 20 mph.

+   The bin for the 20-25 mph range has a height of around 700. In other words, around 700 of the hourly wind speed recordings are between 20 mph and 25 mph.

All eight bins spanning 0 mph to 40 mph on the x-axis have this interpretation.