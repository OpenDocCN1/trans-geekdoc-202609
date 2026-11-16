# ## 5 PERFORMANCE ANALYSIS AND VISUALISATION

Model performance is evaluated by comparing predicted values with test data. Comparison is made in terms of Mean Squared Error (MSE), Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE). The average of these metrics is taken and named 'average_score' to get a sense of the overall fit of the prediction with test data. Figure 2 shows monthly interpolated data. The monthly analysis of the data shows that due to higher cloud cover and rain, less data is available for July, Figure 3. Also, September is the crop's flowering time, and yellow flowers can decrease the NDVI values. June is the hottest month in the region and has the worst NDVI, implying that the region is unsuitable for summer crops. All the winter months, starting from October to January, had the highest NDVI index, which means the region is suitable for the winter crops. The plants start to form grains during the month of October. Therefore, a significant peak in the NDVI index is seen. It is the period when farmers need to ensure that fields are kept flooded and that there is enough sunlight for the grains to mature. The NDVI index increased in the post-COVID year, which depicted better crop growth after COVID-19, and there could be multiple reasons for this change in the index.

![](bbox=[0.225, 0.34, 0.8, 0.505])

Figure 2. Average NDVI vs Monthly interpolated data over the years.

The lowest NDVI index was in the year 2015, which has the most outliers in the data Figure 3. According to the Indian Meteorological Department (IMD), Bihar witnessed rainfall deficiency till the middle of 2015, declaring a drought as the rainfall touched 28% lower than the average. The horizontal line in the box represents the median NDVI, the lower and upper box edges represent the first and third quartiles, respectively, and the whiskers represent the data minimum and maximum. The whiskers show a few outliers in the data, with some NDVI values falling below 0.2 or above 0.7. However, these outliers are relatively rare.

![](bbox=[0.225, 0.67, 0.735, 0.84])

Figure 3. Yearly NDVI index along with data outliers.

The health of the crops is visualized in Figure 4. It can be concluded that in all these years, most of the crops lay in the unhealthy region, and only a few crops lie in the moderately