You will now move to another headache for many ML algorithms: outliers.

# # Dealing with outliers

You are not on this studying journey just to pass the AWS Machine Learning Specialty exam but also to become a better data scientist. There are many different ways to look at the outlier problem purely from a mathematical perspective; however, the datasets used in real life are derived from the underlying business process, so you must include a business perspective during an outlier analysis.

An outlier is an atypical data point in a set of data. For example, Figure 4.8 shows some data points that have been plotted in a two-dimension plan; that is, x and y. The red point is an outlier since it is an atypical value in this series of data.

![](bbox=[0.13, 0.35, 0.875, 0.515])

Figure 4.8 – Identifying an outlier

It is important to treat outlier values because some statistical methods are impacted by them. Still, in Figure 4.8, you can see this behavior in action. On the left-hand side, there has been drawn a line that best fits those data points, ignoring the red point. On the right-hand side, the same line was drawn, but including the red point.

You can visually conclude that, by ignoring the outlier point, you will come up with a better solution on the plan of the left-hand side of the preceding chart since it was able to pass closer to most of the values. You can also prove this by computing an associated error for each line (which you will learn later in this book).

It is worth reminding that you have also seen the outlier issue in action in another situation in this book: specifically, in Table 4.10, while dealing with missing values. In that example, the median was used to work around the problem. Feel free to go back and read it again, but what should be very clear at this point is that median values are less impacted by outliers than average (mean) values.

You now know what outliers are and why you should treat them. You should always consider your business perspective while dealing with outliers, but there are mathematical methods to find them.