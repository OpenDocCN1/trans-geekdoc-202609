# Machine Learning: Concepts, Tools and Data Visualization

![](bbox=[0.115, 0.085, 0.845, 0.345])

| | |
| --- | --- |
| Mean | 5.8338 |
| Median | 5.8 |
| Min | 4.3 |
| Max | 7.9 |
| Standard Deviation | 0.8336 |
| Unique Values | 35 |
| Missing Values | 0 |
| Feature Type | Numeric Feature |

Figure 6-33 Statistics through data visualization

Also, you can check the statistics and histogram of the selected attribute shown in Figure 6-33.

# 6.3.3 Data Preprocessing

Once you have inserted the experimental data and confirmed through visualization, you should delete missing or unnecessary values. It is important to preprocess the data set before designing the experiment. Therefore, it is necessary to deal with missing values before applying the machine learning algorithm.

For the preprocessing practice, the row missing an attribute for “Species” was added, as shown in Figure 6-34. If the species value is missing, we should delete all the rows.

Import the “Select Columns in Dataset” block from the palette and include all the columns, as shown in Figure 6-35, using “Launch column selector”.