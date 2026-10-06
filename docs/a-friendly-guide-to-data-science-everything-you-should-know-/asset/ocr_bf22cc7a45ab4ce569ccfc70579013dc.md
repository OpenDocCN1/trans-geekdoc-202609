# CHAPTER 18 A NEW KIND OF STORYTELLING: DATA VISUALIZATION AND PRESENTATION

# Heatmaps

A heatmap is an enhancement on a table where the range of values are represented by different colors and gradients, usually light to dark for small to large numbers. It can be very helpful in conveying information quickly because of the visual aspect, but still with the detail of a table. See Figure 18-31 for an example of a heatmap showing average grades of middle and high school students in a range of general subjects.

| Grade | English | Science | Social Studies | Art | Music | Band | Foreign Language |
|---|---|---|---|---|---|---||}{
| 6th grade | 85 | 91 | 88 | 87 | 94 | 93 | 89 |
| 7th grade | 83 | 90 | 89 | 88 | 91 | 96 | 89 | 90 |
| 8th grade | 82 | 89 | 86 | 87 | 89 | 91 | 85 |
| 9th grade | 79 | 86 | 82 | 85 | 90 | 88 | 86 |
| 10th grade | 75 | 80 | 79 | 91 | 91 | 96 | 81 |
| 11th grade | 73 | 85 | 79 | 82 | 88 | 87 | 77 |
| 12th grade | 73 | 85 | 80 | 90 | 93 | 95 | 81 |

Figure 18-31. A heatmap of grades of students in 6th-12th grade

This heatmap makes it clear that as the grades progress, some subject average grades go down, but others don't have the same trajectory. The core subjects tend to follow this trend, whereas the electives don't. Without the grayscale coloring, we wouldn't see this so quickly.

One of the many benefits of heatmaps is that you can show a lot of data while keeping it more readable than some other visualizations. This is one reason it's common when using EDA to make correlation matrix heatmaps, especially because you can use two different colors and represent positive and negative values in different colors and different intensities.

It's all worth checking any time you are working with tabular data to see if a heatmap would be appropriate. Stakeholders tend to like them, too.